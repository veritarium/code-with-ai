---
layout: chapter
title: "Core Concepts"
chapter: 13
part: 4
part_title: "Code Literacy"
part_url: "/part-4-literacy/"
prev: "/part-4-literacy/12-reading"
prev_title: "Reading Code"
next: "/part-4-literacy/14-functions"
next_title: "Functions and Libraries"
---

Every program you'll ever encounter is built from the same fundamental concepts: variables to hold data and control flow to make decisions and repeat actions. Master these two ideas and you can understand any code.

## Variables

Variables are named containers for data. That's the entire concept. Think of them as labeled boxes—the name tells you what's inside.

![Variables](/code-with-ai/assets/images/diagrams/13-1-variables.png)
{: .chapter-diagram}
*Figure 13.1: Variables — Named containers for data*
{: .diagram-caption}

When you write `bolt_diameter = 12.5`, you're creating a box labeled `bolt_diameter` and putting the value `12.5` inside it. Later, when you use `bolt_diameter` in a calculation, the computer retrieves that value from the box.

Variables can hold different types of data. **Numbers** store quantities like `count = 42` or `price = 19.99` or `stress = 250.5`. **Text** (called "strings") stores characters like `name = "M12"` or `grade = "8.8"` or `status = "OK"`. **True/False values** (called "booleans") store binary states like `is_valid = True` or `has_error = False`. **Lists** store multiple items like `sizes = [8, 10, 12]`.

Naming matters enormously. Use descriptive names with no spaces (use underscores instead): `bolt_count` not `bolt count`. Always start with a letter. Good names like `bolt_count`, `max_stress`, and `is_valid` make code self-documenting. Bad names like `x`, `bc`, and `thing1` force you to guess what data they hold.

<div class="key-insight">
<strong>Key Insight:</strong> Good variable names make code self-documenting. When you read <code>if stress > max_allowable_stress</code>, you know exactly what's being checked.
</div>

---

## Control Flow

Control flow determines how programs make decisions and repeat actions. Three patterns handle virtually all programming logic.

![Control Flow](/code-with-ai/assets/images/diagrams/13-2-control-flow.png)
{: .chapter-diagram}
*Figure 13.2: Control Flow — Decisions and repetition*
{: .diagram-caption}

The if/else pattern handles decisions. The code checks a condition: if true, it does one thing; if false, it does another. Think of it as a fork in the road. When you see `if stress > 250: print("Fail") else: print("Pass")`, the program chooses one path based on whether stress exceeds 250.

For loops repeat actions a known number of times, once for each item in a collection. When you write `for size in [8, 10, 12]: print(size)`, the code does something for each item in the list—process one item, move to the next, until all items are handled.

While loops repeat actions until a condition changes. When you write `while error > 0.01: refine()`, the code keeps going until the error is small enough. You don't know in advance how many iterations it will take; the code runs until the condition is satisfied.

These three patterns—if/else for choosing, for for repeating through items, while for repeating until done—combine to create every program ever written.

<div class="key-insight">
<strong>Key Insight:</strong> Programs = Data + Decisions + Repetition. Variables hold the data. If/else makes decisions. Loops handle repetition. That's everything.
</div>

---

## Try It Yourself

This example demonstrates variables and control flow in action with real engineering calculations.

Create a file called `core_concepts.py`:

```python
# core_concepts.py
# Demonstrating variables and control flow

# ============================================================
# VARIABLES: Named containers for data
# ============================================================

print("=" * 60)
print("VARIABLES")
print("=" * 60)

# Numbers - storing quantities
bolt_diameter = 12.0     # millimeters
applied_force = 10000    # Newtons
safety_factor = 2.5      # dimensionless

# Text (strings) - storing characters
bolt_name = "M12x1.75"
material = "Grade 8.8 Steel"
status = "Under Review"

# True/False (booleans) - storing yes/no states
is_metric = True
has_passed = False
needs_review = True

# Lists - storing multiple items
available_sizes = [6, 8, 10, 12, 16, 20]
stress_readings = [150.2, 175.8, 162.3, 158.9]

# Demonstrate using variables
print(f"\nBolt: {bolt_name}")
print(f"Material: {material}")
print(f"Diameter: {bolt_diameter} mm")
print(f"Applied Force: {applied_force} N")
print(f"Is Metric: {is_metric}")
print(f"Available sizes: {available_sizes}")

# ============================================================
# IF/ELSE: Making decisions
# ============================================================

print("\n" + "=" * 60)
print("IF/ELSE: Making Decisions")
print("=" * 60)

# Calculate stress
import math
area = math.pi * (bolt_diameter / 2) ** 2
stress = applied_force / area

print(f"\nCalculated stress: {stress:.2f} MPa")

# Simple if/else
yield_strength = 640  # MPa for Grade 8.8

if stress > yield_strength:
    result = "FAIL - Exceeds yield strength"
else:
    result = "PASS - Within limits"

print(f"Yield strength: {yield_strength} MPa")
print(f"Result: {result}")

# Multiple conditions with elif
print("\nSafety factor classification:")
actual_sf = yield_strength / stress

if actual_sf >= 3:
    classification = "EXCELLENT - Very conservative design"
elif actual_sf >= 2:
    classification = "GOOD - Standard safety margin"
elif actual_sf >= 1.5:
    classification = "MARGINAL - Minimum acceptable"
else:
    classification = "INADEQUATE - Needs redesign"

print(f"Safety factor: {actual_sf:.2f}")
print(f"Classification: {classification}")

# ============================================================
# FOR LOOPS: Repeating through items
# ============================================================

print("\n" + "=" * 60)
print("FOR LOOPS: Repeating Through Items")
print("=" * 60)

# Process each available size
print("\nAnalyzing all available bolt sizes:")
print("-" * 40)

for size in available_sizes:
    # Calculate area for each size
    area = math.pi * (size / 2) ** 2
    stress = applied_force / area
    sf = yield_strength / stress

    # Determine if it works
    if sf >= 2:
        verdict = "OK"
    else:
        verdict = "Too small"

    print(f"M{size}: Area={area:.1f}mm², Stress={stress:.1f}MPa, SF={sf:.2f} [{verdict}]")

# Calculate statistics from readings
print("\nProcessing stress readings:")
print(f"Readings: {stress_readings}")

total = 0
for reading in stress_readings:
    total = total + reading

average = total / len(stress_readings)
print(f"Average stress: {average:.2f} MPa")

# ============================================================
# WHILE LOOPS: Repeating until condition met
# ============================================================

print("\n" + "=" * 60)
print("WHILE LOOPS: Repeating Until Done")
print("=" * 60)

# Find the minimum bolt size that works
print("\nFinding minimum acceptable bolt size:")

test_diameter = 4  # Start with smallest possible
step = 0.5

while True:
    area = math.pi * (test_diameter / 2) ** 2
    stress = applied_force / area
    sf = yield_strength / stress

    if sf >= 2:
        print(f"Found: {test_diameter}mm diameter gives SF={sf:.2f}")
        break  # Exit the loop when we find a solution

    test_diameter = test_diameter + step

    if test_diameter > 50:  # Safety limit
        print("No suitable size found up to 50mm")
        break

print(f"Minimum diameter for SF >= 2: {test_diameter} mm")

# Iterative refinement example
print("\nIterative refinement:")

estimate = 10.0  # Initial guess for required diameter
target_sf = 2.5
tolerance = 0.01
iterations = 0

while True:
    area = math.pi * (estimate / 2) ** 2
    stress = applied_force / area
    current_sf = yield_strength / stress

    error = abs(current_sf - target_sf) / target_sf
    iterations += 1

    if error < tolerance:
        print(f"Converged in {iterations} iterations")
        print(f"Diameter: {estimate:.3f} mm, SF: {current_sf:.4f}")
        break

    # Adjust estimate
    if current_sf < target_sf:
        estimate = estimate * 1.1  # Increase
    else:
        estimate = estimate * 0.95  # Decrease

    if iterations > 100:
        print("Did not converge")
        break

# ============================================================
# SUMMARY
# ============================================================

print("\n" + "=" * 60)
print("SUMMARY: Core Concepts")
print("=" * 60)
print("""
VARIABLES store data:
  - Numbers: bolt_diameter = 12.0
  - Text: material = "Steel"
  - Boolean: is_valid = True
  - Lists: sizes = [8, 10, 12]

CONTROL FLOW directs execution:
  - IF/ELSE: Choose between paths
  - FOR: Repeat for each item
  - WHILE: Repeat until condition met

These concepts appear in EVERY program.
Understand them = Understand any code.
""")
```

Run it:

```bash
python core_concepts.py
```

**Expected Output:**

```
============================================================
VARIABLES
============================================================

Bolt: M12x1.75
Material: Grade 8.8 Steel
Diameter: 12.0 mm
Applied Force: 10000 N
Is Metric: True
Available sizes: [6, 8, 10, 12, 16, 20]

============================================================
IF/ELSE: Making Decisions
============================================================

Calculated stress: 88.42 MPa
Yield strength: 640 MPa
Result: PASS - Within limits

Safety factor classification:
Safety factor: 7.24
Classification: EXCELLENT - Very conservative design

============================================================
FOR LOOPS: Repeating Through Items
============================================================

Analyzing all available bolt sizes:
----------------------------------------
M6: Area=28.3mm², Stress=353.7MPa, SF=1.81 [Too small]
M8: Area=50.3mm², Stress=198.9MPa, SF=3.22 [OK]
M10: Area=78.5mm², Stress=127.3MPa, SF=5.03 [OK]
...
```

The example shows how variables hold your engineering data, how if/else makes decisions about pass/fail criteria, how for loops process multiple items, and how while loops iterate until finding a solution.

---

## Key Takeaway

Variables and control flow are the foundation of all programming. Variables are just named containers—think labeled boxes. Control flow uses if/else for decisions, for loops to process collections, and while loops to repeat until done. Every complex program is built from these simple pieces combined in different ways.

In the next chapter, we'll explore functions—how to package code into reusable building blocks.

