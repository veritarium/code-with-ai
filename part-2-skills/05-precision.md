---
layout: chapter
title: "Precision"
chapter: 5
part: 2
part_title: "Skills"
part_url: "/part-2-skills/"
prev: "/part-2-skills/04-decomposition"
prev_title: "Decomposition"
next: "/part-2-skills/06-feedback"
next_title: "Feedback"
---

Not all prompts are equal. There's a spectrum from vague to precise, and where you land on that spectrum determines your success rate.

![The Spectrum](/code-with-ai/assets/images/diagrams/05-1-the-spectrum.png)
{: .chapter-diagram}
*Figure 5.1: The Spectrum — From vague to precise*
{: .diagram-caption}

Look at this gradient bar. On the left, in red: VAGUE. On the right, in blue: PRECISE. Your goal is to move as far right as possible before hitting send.

A vague prompt like "Help me with calculations" has maybe a 20% success rate. AI has no idea what calculations you mean. What inputs? What outputs? What domain? It will guess, and it will probably guess wrong. You'll spend the next hour trying to get what you actually wanted.

A medium prompt like "Write a stress calculation function" improves to around 50%. Better—AI knows the domain now. But what kind of stress? What inputs does the function take? What should it return? Still too much guessing required.

A precise prompt transforms everything. "Write a Python function called calculate_tensile_stress that takes force in Newtons and area in square millimeters, returns stress in MPa, and raises an error if either input is negative." This hits 90%+ success rate. AI knows exactly what to build: the function name, the inputs, the output, the units, the error handling—it's all specified.

Yes, writing precise prompts takes more time upfront. But it saves enormous time in the loop. Would you rather spend 2 minutes writing a good prompt and get working code, or spend 30 seconds on a vague prompt and then 20 minutes trying to fix what AI gives you?

<div class="key-insight">
<strong>Key Insight:</strong> More specific prompts = Fewer iterations = Better results.
</div>

---

## Five Components of a Good Prompt

Here's a framework for building precise prompts. Five components, each adding clarity.

![Five Components](/code-with-ai/assets/images/diagrams/05-2-five-components.png)
{: .chapter-diagram}
*Figure 5.2: Five Components — The framework for precise prompts*
{: .diagram-caption}

**WHAT** is the action you want. "Create a function" or "Fix this error" or "Explain this code." This is the verb of your prompt.

**WHERE** is the location or context. "In the utils.py file" or "In the calculate function" or "For this data structure." This tells AI where to focus.

**HOW** specifies the method or approach. "Using a for loop" or "With error handling" or "Using the pandas library." This constrains how AI solves the problem.

**WHY** explains the purpose. "To improve performance" or "For user validation" or "To match the existing code style." This gives AI intent to align with.

**EXAMPLE** shows what you expect. "Input: [1,2,3], Output: 6" or "Like this existing function but for temperature." This removes ambiguity about the desired result.

You don't always need all five. But the more you include, the better your results. When a prompt isn't working, run through this checklist and add the components you're missing.

<div class="key-insight">
<strong>Key Insight:</strong> The five components give you a systematic way to make any prompt more precise.
</div>

---

## Try It Yourself

This example demonstrates the dramatic difference between vague and precise prompts. We'll implement the exact same calculation three ways, showing what you might get from each approach.

Create a file called `prompt_comparison.py`:

```python
# prompt_comparison.py
# Demonstrating the difference between vague and precise prompts

# === What you might get from: "Help me with calculations" ===
def vague_calculation(x, y):
    """Vague prompt result: AI guesses what you want"""
    return x + y  # Addition? Multiplication? Who knows!

# === What you might get from: "Write a stress calculation" ===
def medium_calculation(force, area):
    """Medium prompt result: Right domain, wrong details"""
    # Missing units, no validation, unclear return type
    return force / area

# === What you get from a precise prompt ===
# "Write a Python function called calculate_tensile_stress that takes
# force_newtons (float) and area_mm2 (float), returns stress in MPa
# as a float, and raises ValueError if either input is negative or
# if area is zero"

def calculate_tensile_stress(force_newtons: float, area_mm2: float) -> float:
    """
    Calculate tensile stress from force and cross-sectional area.

    Args:
        force_newtons: Applied force in Newtons (must be non-negative)
        area_mm2: Cross-sectional area in square millimeters (must be positive)

    Returns:
        Tensile stress in MegaPascals (MPa)

    Raises:
        ValueError: If force is negative, area is zero, or area is negative
    """
    if force_newtons < 0:
        raise ValueError(f"Force cannot be negative: {force_newtons}")
    if area_mm2 <= 0:
        raise ValueError(f"Area must be positive: {area_mm2}")

    # Convert mm² to m² for calculation
    area_m2 = area_mm2 * 1e-6

    # Calculate stress in Pa, then convert to MPa
    stress_pa = force_newtons / area_m2
    stress_mpa = stress_pa / 1e6

    return stress_mpa


# === Demonstrate the difference ===
if __name__ == "__main__":
    # Test values
    force = 10000  # Newtons
    area = 50      # mm²

    print("PROMPT PRECISION COMPARISON")
    print("=" * 50)
    print(f"Input: Force = {force} N, Area = {area} mm²")
    print("=" * 50)

    # Vague result
    print("\n1. VAGUE PROMPT: 'Help me with calculations'")
    result1 = vague_calculation(force, area)
    print(f"   Result: {result1}")
    print("   Problem: Just added the numbers! Wrong operation entirely.")

    # Medium result
    print("\n2. MEDIUM PROMPT: 'Write a stress calculation'")
    result2 = medium_calculation(force, area)
    print(f"   Result: {result2}")
    print("   Problem: No units! Is this Pa? MPa? psi? Unusable.")

    # Precise result
    print("\n3. PRECISE PROMPT: Full specification with units and validation")
    result3 = calculate_tensile_stress(force, area)
    print(f"   Result: {result3:.2f} MPa")
    print("   Correct! Clear units, proper conversion, ready to use.")

    # Show validation works
    print("\n" + "=" * 50)
    print("BONUS: The precise version also handles errors:")
    print("=" * 50)

    try:
        calculate_tensile_stress(-100, 50)
    except ValueError as e:
        print(f"\n   Negative force test: {e}")

    try:
        calculate_tensile_stress(100, 0)
    except ValueError as e:
        print(f"   Zero area test: {e}")

    try:
        calculate_tensile_stress(100, -50)
    except ValueError as e:
        print(f"   Negative area test: {e}")

    print("\n" + "=" * 50)
    print("LESSON: Precision in your prompt = precision in your code")
    print("=" * 50)
```

Run it:

```bash
python prompt_comparison.py
```

**Expected Output:**

```
PROMPT PRECISION COMPARISON
==================================================
Input: Force = 10000 N, Area = 50 mm²
==================================================

1. VAGUE PROMPT: 'Help me with calculations'
   Result: 10050
   Problem: Just added the numbers! Wrong operation entirely.

2. MEDIUM PROMPT: 'Write a stress calculation'
   Result: 200.0
   Problem: No units! Is this Pa? MPa? psi? Unusable.

3. PRECISE PROMPT: Full specification with units and validation
   Result: 200.00 MPa
   Correct! Clear units, proper conversion, ready to use.

==================================================
BONUS: The precise version also handles errors:
==================================================

   Negative force test: Force cannot be negative: -100
   Zero area test: Area must be positive: 0
   Negative area test: Area must be positive: -50

==================================================
LESSON: Precision in your prompt = precision in your code
==================================================
```

The vague prompt produces code that doesn't even perform the right operation. The medium prompt gets the operation right but produces unusable output without units or validation. The precise prompt produces production-ready code with proper unit handling, type hints, documentation, and error checking. That's the power of precision.

---

## Key Takeaway

Every minute you spend making your prompt more precise saves five minutes of iteration later. Use the five components—What, Where, How, Why, and Example—as a checklist. When AI gives you something wrong, ask yourself: "What was I not specific enough about?" The answer is almost always in the prompt.

In the next chapter, we'll learn how to give effective feedback when AI's first attempt isn't quite right.

