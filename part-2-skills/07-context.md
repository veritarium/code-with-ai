---
layout: chapter
title: "Context"
chapter: 7
part: 2
part_title: "Skills"
part_url: "/part-2-skills/"
prev: "/part-2-skills/06-feedback"
prev_title: "Feedback"
next: "/part-2-skills/08-restart"
next_title: "When to Restart"
---

This concept will change how you work with AI.

![The Window](/code-with-ai/assets/images/diagrams/07-1-the-window.png)
{: .chapter-diagram}
*Figure 7.1: The Window — AI only sees what's in the prompt*
{: .diagram-caption}

Look at this diagram. The large box represents YOUR WORLD—everything you know about your project, your history, your requirements, your preferences. The small box inside represents AI'S WINDOW—what AI can actually see.

AI cannot see your screen. It cannot access your files. It doesn't remember your past conversations. It doesn't know your project. It cannot read your mind. Unless you tell it, AI has no access to any of the context you take for granted.

All that information floating outside the window—your project history, other files, business requirements, team coding standards, past conversations, your preferences, why you're doing this—none of it exists for AI until you share it.

This is why vague prompts fail. When you say "fix the function," you're assuming AI knows which function, what's wrong with it, and how you want it fixed. AI doesn't know any of that. You must explicitly share relevant code, error messages, constraints, and requirements. Make the window bigger. The more context you share, the better AI understands.

<div class="key-insight">
<strong>Key Insight:</strong> AI only sees what's in the prompt. Everything else is invisible.
</div>

---

## What to Share

There are five types of context that dramatically improve AI results.

![What to Share](/code-with-ai/assets/images/diagrams/07-2-what-to-share.png)
{: .chapter-diagram}
*Figure 7.2: What to Share — Five types of context*
{: .diagram-caption}

Constraints are the limitations and requirements that bound your solution. Saying "must work in Python 3.8" eliminates solutions using newer features. Specifying "no external libraries" focuses AI on standard library solutions. Setting "max 100 lines of code" gives a size target. Without knowing your constraints, AI might give you something technically correct but unusable in your actual situation.

Preferences are your style and approach choices. Asking for "descriptive variable names" shapes how AI writes code. Requesting "comments for complex logic" determines documentation level. Saying "prefer simple over clever" guides AI toward maintainable solutions. When you share preferences, you get code that fits your standards rather than AI's defaults.

History is what led to this point in your project. Mentioning "we tried X but it failed because Y" prevents AI from suggesting the same failed approach. Noting "this is part of a larger system" helps AI understand scope. Sharing "previous version had this bug" gives AI context about what to avoid. History prevents you from going in circles.

Errors are the exact messages and symptoms you're seeing. Pasting "TypeError: 'NoneType' has no len()" gives AI the specific error to diagnose. Describing "happens when input is empty list" identifies the trigger. Saying "line 42 in process_data function" pinpoints the location. The more precise your error description, the faster AI can fix it.

Files are the relevant code and data for your task. Including "here's the current function: [code]" shows AI what you're working with. Providing "sample input data: [data]" helps AI understand the format. Attaching "related config file: [config]" gives system context. AI can't help with code it can't see.

<div class="key-insight">
<strong>Key Insight:</strong> More context = Fewer iterations = Better results.
</div>

---

## Try It Yourself

This example demonstrates the dramatic difference context makes. We'll show the same request with and without context.

Create a file called `context_comparison.py`:

```python
# context_comparison.py
# Demonstrating how context improves AI results

# === SCENARIO: You need to convert temperature values ===

# WITHOUT CONTEXT: "Write a temperature converter"
# AI might give you something generic and incomplete:

def convert_temperature_no_context(value):
    """What AI might produce without context"""
    # Celsius to Fahrenheit? Fahrenheit to Celsius? Kelvin?
    # What precision? What error handling?
    return value * 9/5 + 32  # Guessing C to F


# WITH FULL CONTEXT:
# "Write a temperature converter for our process monitoring system.
#  CONSTRAINTS: Python 3.8, no external libraries
#  PREFERENCES: Use type hints, include docstrings
#  HISTORY: Previous version crashed on None values
#  ERRORS: Need to handle sensor reading 'ERR' string
#  FILES: Must match existing function signature: convert(value, from_unit, to_unit)"

def convert_temperature(
    value: float,
    from_unit: str,
    to_unit: str
) -> float:
    """
    Convert temperature between Celsius, Fahrenheit, and Kelvin.

    Used in process monitoring system for multi-unit sensor data.

    Args:
        value: Temperature value to convert
        from_unit: Source unit ('C', 'F', or 'K')
        to_unit: Target unit ('C', 'F', or 'K')

    Returns:
        Converted temperature value

    Raises:
        ValueError: If units are invalid or value is None
        TypeError: If value cannot be converted to float
    """
    # Handle None values (from previous crash)
    if value is None:
        raise ValueError("Temperature value cannot be None")

    # Handle sensor error strings
    if isinstance(value, str):
        if value.upper() == 'ERR':
            raise ValueError("Sensor returned error reading")
        try:
            value = float(value)
        except ValueError:
            raise TypeError(f"Cannot convert '{value}' to temperature")

    # Normalize units to uppercase
    from_unit = from_unit.upper()
    to_unit = to_unit.upper()

    valid_units = {'C', 'F', 'K'}
    if from_unit not in valid_units or to_unit not in valid_units:
        raise ValueError(f"Units must be C, F, or K. Got: {from_unit}, {to_unit}")

    # Convert to Celsius first (common base)
    if from_unit == 'C':
        celsius = value
    elif from_unit == 'F':
        celsius = (value - 32) * 5/9
    elif from_unit == 'K':
        celsius = value - 273.15

    # Convert from Celsius to target
    if to_unit == 'C':
        result = celsius
    elif to_unit == 'F':
        result = celsius * 9/5 + 32
    elif to_unit == 'K':
        result = celsius + 273.15

    return round(result, 2)


# === Demonstrate the difference ===
if __name__ == "__main__":
    print("CONTEXT COMPARISON: Temperature Converter")
    print("=" * 60)

    # Test cases that reveal the difference
    test_cases = [
        (100, 'C', 'F', "Normal conversion"),
        (212, 'F', 'C', "Reverse conversion"),
        (0, 'K', 'C', "Kelvin conversion"),
        (None, 'C', 'F', "None value (crashed previous version)"),
        ('ERR', 'C', 'F', "Sensor error string"),
        ('98.6', 'F', 'C', "String number from sensor"),
    ]

    print("\nWITHOUT CONTEXT (basic converter):")
    print("-" * 60)
    print("Only handles C to F. No validation. Will crash on edge cases.")
    print(f"convert_temperature_no_context(100) = {convert_temperature_no_context(100)}")

    print("\nWITH FULL CONTEXT (production-ready converter):")
    print("-" * 60)

    for value, from_u, to_u, description in test_cases:
        print(f"\nTest: {description}")
        print(f"Input: {value} {from_u} -> {to_u}")
        try:
            result = convert_temperature(value, from_u, to_u)
            print(f"Result: {result} {to_u}")
        except (ValueError, TypeError) as e:
            print(f"Handled error: {e}")

    print("\n" + "=" * 60)
    print("LESSON: Context transforms generic code into production code.")
    print("Share constraints, preferences, history, errors, and files.")
    print("=" * 60)
```

Run it:

```bash
python context_comparison.py
```

**Expected Output:**

```
CONTEXT COMPARISON: Temperature Converter
============================================================

WITHOUT CONTEXT (basic converter):
------------------------------------------------------------
Only handles C to F. No validation. Will crash on edge cases.
convert_temperature_no_context(100) = 212.0

WITH FULL CONTEXT (production-ready converter):
------------------------------------------------------------

Test: Normal conversion
Input: 100 C -> F
Result: 212.0 F

Test: Reverse conversion
Input: 212 F -> C
Result: 100.0 C

Test: Kelvin conversion
Input: 0 K -> C
Result: -273.15 C

Test: None value (crashed previous version)
Input: None C -> F
Handled error: Temperature value cannot be None

Test: Sensor error string
Input: ERR C -> F
Handled error: Sensor returned error reading

Test: String number from sensor
Input: 98.6 F -> C
Result: 37.0 C

============================================================
LESSON: Context transforms generic code into production code.
Share constraints, preferences, history, errors, and files.
============================================================
```

Without context, AI produced a bare-bones function that only converts Celsius to Fahrenheit. With context—constraints, preferences, history, error cases, and file requirements—AI produced a robust function that handles multiple units, validates input, catches the edge cases that crashed the previous version, and matches the required signature.

---

## Key Takeaway

Every time you prompt AI, remember the window. AI only sees what you put in front of it. Before you hit send, ask yourself: Did I share the constraints? The preferences? The history? The errors? The relevant code? The more context you provide, the closer AI gets to exactly what you need on the first try.

In the next chapter, we'll learn when to stop iterating and start fresh instead.

