---
layout: chapter
title: "Decomposition"
chapter: 4
part: 2
part_title: "Skills"
part_url: "/part-2-skills/"
prev: "/part-1-foundations/03-operations"
prev_title: "Six Operations"
next: "/part-2-skills/05-precision"
next_title: "Precision"
---

This is the single most important skill for coding with AI: breaking big things into small things.

![Decomposition](/code-with-ai/assets/images/diagrams/04-1-decomposition.png)
{: .chapter-diagram}
*Figure 4.1: Decomposition — Breaking big tasks into AI-sized pieces*
{: .diagram-caption}

Look at this tree. At the top, you have a big task: "Build a bolt calculator app." If you give that to AI as-is, you'll get something. But it probably won't be what you want. The task is too big, too vague, too open to interpretation.

Now look what happens when we decompose it. That big task breaks into medium tasks: input section, calculation engine, results display, and file handling. Each of those breaks into small tasks. The input section becomes "get force value," "get area value," and "validate inputs." The calculation engine becomes "calculate stress," "check against limits," and "determine pass/fail."

These small tasks are perfect for AI. They're specific. They're contained. They have clear inputs and outputs. Each one can be described in a single sentence, and AI can execute each one with near-perfect accuracy.

Think of it like engineering drawings. You don't hand someone a napkin sketch and say "build this building." You provide detailed drawings of each component. AI needs the same level of specificity. The more you break down a problem before asking AI to solve it, the better your results will be.

<div class="key-insight">
<strong>Key Insight:</strong> Big tasks confuse AI. Small tasks get perfect results.
</div>

---

## The One-Sentence Rule

Here's a simple test to know if your task is the right size.

![The Rule](/code-with-ai/assets/images/diagrams/04-2-the-rule.png)
{: .chapter-diagram}
*Figure 4.2: The One-Sentence Rule — The test for right-sized tasks*
{: .diagram-caption}

Ask yourself: "Can I explain this task in ONE sentence?" If you can't, the task is too big—break it down further. If you can, the task is just right—give it to AI.

Consider these two approaches to the same goal. The first says "Build me an app that handles all our bolt calculations with a UI and database and reports." That's not one sentence describing one task—that's a paragraph describing a project. AI will either refuse or produce something unusable.

The second approach says "Create a function that calculates tensile stress from force and area." One sentence. One task. One clear outcome. This is the kind of prompt that gets results.

<div class="key-insight">
<strong>Key Insight:</strong> When you find yourself writing a paragraph to describe what you want, stop. That's a sign you need to decompose first.
</div>

---

## Try It Yourself

This example demonstrates decomposition in action. We'll build a complete bolt stress calculator by creating several small, focused functions instead of one monolithic program.

Create a file called `bolt_calculator.py`:

```python
# bolt_calculator.py
# Demonstrating decomposition: breaking a calculator into small functions

# === SMALL TASK 1: Get numeric input from user ===
def get_number(prompt, unit=""):
    """Get a positive number from user with validation"""
    while True:
        try:
            value = float(input(f"{prompt} ({unit}): " if unit else f"{prompt}: "))
            if value <= 0:
                print("Error: Value must be positive. Try again.")
                continue
            return value
        except ValueError:
            print("Error: Please enter a valid number.")

# === SMALL TASK 2: Calculate stress ===
def calculate_stress(force_n, area_mm2):
    """Calculate tensile stress in MPa"""
    area_m2 = area_mm2 * 1e-6  # Convert mm² to m²
    stress_pa = force_n / area_m2
    stress_mpa = stress_pa / 1e6
    return stress_mpa

# === SMALL TASK 3: Determine safety status ===
def check_safety(stress_mpa, yield_strength_mpa=250):
    """Check if stress is within safe limits"""
    safety_factor = yield_strength_mpa / stress_mpa
    if safety_factor >= 3:
        status = "SAFE"
        message = "Design has excellent safety margin"
    elif safety_factor >= 2:
        status = "ACCEPTABLE"
        message = "Design meets minimum safety requirements"
    elif safety_factor >= 1:
        status = "WARNING"
        message = "Safety factor below recommended minimum"
    else:
        status = "FAILURE"
        message = "Stress exceeds yield strength!"
    return status, safety_factor, message

# === SMALL TASK 4: Format the results ===
def format_results(force, area, stress, status, sf, message):
    """Create formatted output string"""
    output = "\n" + "=" * 40 + "\n"
    output += "BOLT STRESS ANALYSIS RESULTS\n"
    output += "=" * 40 + "\n"
    output += f"Applied Force:    {force:,.1f} N\n"
    output += f"Bolt Area:        {area:,.2f} mm²\n"
    output += f"Tensile Stress:   {stress:,.2f} MPa\n"
    output += f"Safety Factor:    {sf:.2f}\n"
    output += f"Status:           {status}\n"
    output += "-" * 40 + "\n"
    output += f"{message}\n"
    output += "=" * 40
    return output

# === MAIN: Combine small tasks into complete program ===
def main():
    print("BOLT STRESS CALCULATOR")
    print("-" * 30)

    # Task 1: Get inputs
    force = get_number("Enter applied force", "N")
    diameter = get_number("Enter bolt diameter", "mm")

    # Calculate area from diameter (Task 2a)
    import math
    area = math.pi * (diameter / 2) ** 2

    # Task 2: Calculate stress
    stress = calculate_stress(force, area)

    # Task 3: Check safety
    status, sf, message = check_safety(stress)

    # Task 4: Display results
    results = format_results(force, area, stress, status, sf, message)
    print(results)

if __name__ == "__main__":
    main()
```

Run it:

```bash
python bolt_calculator.py
```

**Expected Output:**

```
BOLT STRESS CALCULATOR
------------------------------
Enter applied force (N): 50000
Enter bolt diameter (mm): 10

========================================
BOLT STRESS ANALYSIS RESULTS
========================================
Applied Force:    50,000.0 N
Bolt Area:        78.54 mm²
Tensile Stress:   636.62 MPa
Safety Factor:    0.39
Status:           FAILURE
-----------------------------------------
Stress exceeds yield strength!
========================================
```

Notice how the program is built from four small functions, each doing exactly one thing. If any part doesn't work correctly, you know exactly which function to fix. If you want to add features—like saving to a file or adding different materials—you just add another small function. This is the power of decomposition.

---

## Key Takeaway

Decomposition is the master skill for AI coding. Before you write any prompt, ask yourself: "Is this task small enough?" If you can't describe it in one sentence, break it down. Build your programs from small, single-purpose pieces, and AI will help you assemble them into something powerful.

In the next chapter, we'll focus on making each of those small prompts as precise as possible.

