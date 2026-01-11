---
layout: chapter
title: "Reading Code"
chapter: 12
part: 4
part_title: "Code Literacy"
part_url: "/part-4-literacy/"
prev: "/part-3-pitfalls/11-unstuck"
prev_title: "Getting Unstuck"
next: "/part-4-literacy/13-concepts"
next_title: "Core Concepts"
---

Here's a secret: You don't need to write code to understand it.

Reading code is like reading a recipe. You can follow along without being a chef. You can understand what's happening without knowing how to create it from scratch. This skill—reading and understanding code—will serve you even if you never write a single line yourself.

![Learning to Read Code](/code-with-ai/assets/images/diagrams/12-1-learning-to-read.png)
{: .chapter-diagram}
*Figure 12.1: Learning to Read Code — What to look for*
{: .diagram-caption}

When you look at code, focus on these patterns. **Names** tell you what things represent—`bolt_diameter`, `max_stress`, `is_valid` describe what data they hold. **Structure** shows grouping through indentation; things indented under an `if` statement only happen when that condition is true. **Keywords** like `if`, `for`, `while`, and `return` control the flow and work the same way in almost every language. **Comments** starting with `#` are human explanations written for you. And **flow** runs top to bottom unless something branches it.

When you encounter code you don't understand, AI is your interpreter. Ask "What does this code do?" or "Explain line by line" or "What is [variable] for?" or "Why is this needed?" or "What would break this?" AI excels at explaining code because it's seen millions of examples.

Don't worry about memorizing syntax, understanding every detail, advanced patterns, or optimization tricks. Focus on the big picture first. Your goal is to understand what code does, not to memorize how to write it.

<div class="key-insight">
<strong>Goal:</strong> Understand what code does, not memorize how to write it.
</div>

---

## Code Anatomy

Every program is made of the same universal parts. Once you recognize these building blocks, you can read any code.

![Code Anatomy](/code-with-ai/assets/images/diagrams/12-2-code-anatomy.png)
{: .chapter-diagram}
*Figure 12.2: Code Anatomy — The universal parts*
{: .diagram-caption}

A **COMMENT** like `# Calculate bolt stress` is a note for humans. The computer ignores it completely. Think of comments as sticky notes attached to the code.

A **FUNCTION** like `def calculate_stress(force, area):` is a reusable block of code that takes inputs and gives outputs. It's named for what it does. Think of functions like machines in a factory.

A **VARIABLE** like `stress = force / area` is a named container for data. The name `stress` holds the result of the calculation so you can use it later.

A **CONDITION** like `if stress > 250:` makes a decision based on whether something is true or false. It branches the flow like a fork in the road.

**OUTPUT** like `print("Warning: High stress!")` shows results to the user, making the invisible visible.

A **FUNCTION CALL** like `calculate_stress(1000, 4)` uses a function you defined. You put in values and get back a result.

<div class="key-insight">
<strong>Key Insight:</strong> Every program you'll ever see is made of these same building blocks, just arranged differently. Learn the parts = Read any program.
</div>

---

## Try It Yourself

This example demonstrates reading and understanding code. Run it and follow along with the annotations.

Create a file called `reading_code.py`:

```python
# reading_code.py
# Learning to read code by examining an annotated example

# ============================================================
# ANNOTATED CODE EXAMPLE
# Each line is explained so you understand what it does
# ============================================================

# ------- COMMENT -------
# This is a comment - it explains what comes next
# Comments start with # and are for humans, not the computer

# ------- VARIABLE -------
# Variables store data with descriptive names
bolt_diameter = 12.0    # millimeters - the name tells you the unit
applied_force = 5000    # Newtons
yield_strength = 250    # MPa - maximum allowable stress

# ------- CALCULATION -------
# Calculate bolt cross-sectional area (circle: pi * r^2)
import math
radius = bolt_diameter / 2
area = math.pi * radius ** 2    # ** means "to the power of"

# ------- FUNCTION DEFINITION -------
# Functions are reusable blocks of code
# 'def' means "define a function"
# Parameters (stress, limit) are inputs the function receives

def check_stress(stress, limit):
    """
    This text in triple quotes is called a docstring.
    It explains what the function does.
    Returns 'PASS' if stress is below limit, 'FAIL' otherwise.
    """
    # ------- CONDITION -------
    # 'if' checks whether something is true
    if stress > limit:
        return "FAIL"    # 'return' sends a value back
    else:
        return "PASS"    # 'else' handles the opposite case


# ------- FUNCTION CALL -------
# Using the function we defined above
# Put values in, get a result back

# First, calculate the stress
stress = applied_force / area    # Force / Area = Stress

# Then check if it passes
result = check_stress(stress, yield_strength)

# ------- OUTPUT -------
# print() displays information to the screen
print("=" * 50)
print("BOLT STRESS ANALYSIS")
print("=" * 50)
print(f"Bolt diameter: {bolt_diameter} mm")
print(f"Applied force: {applied_force} N")
print(f"Cross-sectional area: {area:.2f} mm²")
print(f"Calculated stress: {stress:.2f} MPa")
print(f"Yield strength: {yield_strength} MPa")
print(f"Result: {result}")
print("=" * 50)


# ============================================================
# READING EXERCISE
# Now let's practice reading unfamiliar code
# ============================================================

print("\n" + "=" * 50)
print("READING EXERCISE")
print("=" * 50)

# Can you understand what this code does?
# Don't worry about syntax - focus on the LOGIC

def analyze_bolts(bolt_list, stress_limit):
    """Analyze a list of bolts and count how many pass/fail"""
    passed = 0
    failed = 0

    for bolt in bolt_list:
        bolt_stress = bolt["force"] / bolt["area"]
        if bolt_stress <= stress_limit:
            passed = passed + 1
        else:
            failed = failed + 1

    return {"passed": passed, "failed": failed}

# Test data
test_bolts = [
    {"name": "Bolt A", "force": 1000, "area": 50},   # 20 MPa
    {"name": "Bolt B", "force": 5000, "area": 50},   # 100 MPa
    {"name": "Bolt C", "force": 15000, "area": 50},  # 300 MPa - will fail!
    {"name": "Bolt D", "force": 8000, "area": 50},   # 160 MPa
]

results = analyze_bolts(test_bolts, stress_limit=250)

print(f"\nAnalyzed {len(test_bolts)} bolts with 250 MPa limit:")
print(f"  Passed: {results['passed']}")
print(f"  Failed: {results['failed']}")

# ============================================================
# WHAT DID YOU LEARN?
# ============================================================

print("\n" + "=" * 50)
print("CODE READING CHECKLIST")
print("=" * 50)
print("""
When reading code, look for:

1. NAMES - Variables and functions have descriptive names
   bolt_diameter, calculate_stress, is_valid

2. STRUCTURE - Indentation shows what belongs together
   Code under 'if' only runs when condition is true

3. FLOW - Code runs top to bottom
   Unless if/else branches it or loops repeat it

4. COMMENTS - # explains the intent
   Read them for context

5. PATTERNS - You'll see the same patterns everywhere
   if/else for decisions, for loops for repetition

You don't need to memorize syntax!
Ask AI: "Explain this code" whenever you're unsure.
""")
```

Run it:

```bash
python reading_code.py
```

**Expected Output:**

```
==================================================
BOLT STRESS ANALYSIS
==================================================
Bolt diameter: 12.0 mm
Applied force: 5000 N
Cross-sectional area: 113.10 mm²
Calculated stress: 44.21 MPa
Yield strength: 250 MPa
Result: PASS
==================================================

==================================================
READING EXERCISE
==================================================

Analyzed 4 bolts with 250 MPa limit:
  Passed: 3
  Failed: 1

==================================================
CODE READING CHECKLIST
==================================================

When reading code, look for:

1. NAMES - Variables and functions have descriptive names
   bolt_diameter, calculate_stress, is_valid

2. STRUCTURE - Indentation shows what belongs together
   Code under 'if' only runs when condition is true
...
```

The annotated example shows every building block in action. The reading exercise gives you practice understanding code you didn't write—which is exactly the skill you need when working with AI-generated code.

---

## Key Takeaway

Reading code is a learnable skill separate from writing it. Focus on names (what data represents), structure (what belongs together), flow (top to bottom with branches), and patterns (the same building blocks everywhere). When you're unsure, ask AI to explain. You don't need to memorize syntax—you need to understand intent.

In the next chapter, we'll dive deeper into the core concepts that appear in every program.

