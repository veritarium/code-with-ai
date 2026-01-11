---
layout: chapter
title: "Debugging"
chapter: 10
part: 3
part_title: "Problems"
part_url: "/part-3-pitfalls/"
prev: "/part-3-pitfalls/09-traps"
prev_title: "Common Pitfalls"
next: "/part-3-pitfalls/11-unstuck"
next_title: "Getting Unstuck"
---

Your code doesn't work. Here's the systematic approach to fixing it.

![The Debugging Flow](/code-with-ai/assets/images/diagrams/10-1-the-debugging.png)
{: .chapter-diagram}
*Figure 10.1: The Debugging Flow — A systematic approach*
{: .diagram-caption}

Debugging follows a six-step process. First, **CAPTURE** the exact error message—all of it, not a summary, the actual text. Second, **LOCATE** the problem line; error messages usually tell you where to look. Third, gather **CONTEXT** by including the surrounding code; AI needs to see what's happening around the error. Fourth, **ASK** AI with all this context assembled. Fifth, **APPLY** the fix AI provides. Sixth, **TEST** by running the code again to verify it's actually fixed.

The difference between bad and good debug requests is stark. A bad request says "My code doesn't work, fix it"—missing the error message, the failing line, the relevant code, and what the code should do. AI will guess wrong. A good request says "Error: TypeError on line 15. Here's lines 10-20: [code]. Input was: [1, 2, None]. Expected: sum of numbers. Should skip None values." This has the exact error, location, code context, input data, and expected behavior. AI can provide a precise fix.

<div class="key-insight">
<strong>Key Insight:</strong> Better information in = Better fix out. Every detail you provide eliminates guesswork.
</div>

---

## Error Types

Understanding error types helps you describe them better to AI.

![Error Types](/code-with-ai/assets/images/diagrams/10-2-error-types.png)
{: .chapter-diagram}
*Figure 10.2: Error Types — Know your errors*
{: .diagram-caption}

**SYNTAX ERRORS** mean the code can't even run. These include missing brackets, typos, and wrong indentation. Tell AI "Syntax error on line X: [error message]." These are the easiest to fix—usually one character or line needs correction.

**RUNTIME ERRORS** mean the code runs but crashes midway. Examples include division by zero, accessing null values, and file not found. Tell AI "Crashes at line X with [error]. Input was [data]." These are medium difficulty because you need to understand what triggered the crash.

**LOGIC ERRORS** are the trickiest—the code runs without crashing but gives wrong results. Examples include wrong calculations, off-by-one errors, and incorrect conditions. Tell AI "Got [X], expected [Y]. Here's the code." These are hardest because there's no error message to guide you.

<div class="key-insight">
<strong>Key Insight:</strong> Name the error type = Faster fix. Knowing what you're dealing with shapes how you describe the problem.
</div>

---

## Try It Yourself

This example demonstrates debugging all three error types with a systematic approach.

Create a file called `debugging_practice.py`:

```python
# debugging_practice.py
# Practicing the debugging flow with all three error types

# ============================================================
# ERROR TYPE 1: SYNTAX ERROR
# The code won't even run
# ============================================================

def syntax_error_example():
    """Demonstrate finding and fixing a syntax error"""
    print("\n" + "=" * 60)
    print("SYNTAX ERROR EXAMPLE")
    print("=" * 60)

    # This is the BROKEN code (commented out so file runs):
    broken_code = '''
def calculate_area(length, width)   # Missing colon!
    return length * width
'''
    print("BROKEN CODE:")
    print(broken_code)
    print("ERROR: SyntaxError: expected ':'")
    print("LINE: 1")

    print("\nDEBUGGING STEPS:")
    print("1. CAPTURE: SyntaxError: expected ':'")
    print("2. LOCATE: Line 1, after 'width)'")
    print("3. CONTEXT: Function definition line")
    print("4. ASK: 'SyntaxError expected colon on line 1: def calculate_area(length, width)'")
    print("5. APPLY: Add the missing colon")
    print("6. TEST: Run again")

    # FIXED version:
    def calculate_area(length, width):  # Colon added!
        return length * width

    result = calculate_area(5, 3)
    print(f"\nFIXED! calculate_area(5, 3) = {result}")


# ============================================================
# ERROR TYPE 2: RUNTIME ERROR
# The code runs but crashes on certain inputs
# ============================================================

def runtime_error_example():
    """Demonstrate finding and fixing a runtime error"""
    print("\n" + "=" * 60)
    print("RUNTIME ERROR EXAMPLE")
    print("=" * 60)

    # BROKEN version that crashes:
    def calculate_average_broken(numbers):
        total = sum(numbers)
        return total / len(numbers)  # Crashes on empty list!

    print("BROKEN CODE:")
    print("def calculate_average(numbers):")
    print("    total = sum(numbers)")
    print("    return total / len(numbers)")

    print("\nTEST CASE: calculate_average([])")
    try:
        calculate_average_broken([])
    except ZeroDivisionError as e:
        print(f"ERROR: {type(e).__name__}: {e}")

    print("\nDEBUGGING STEPS:")
    print("1. CAPTURE: ZeroDivisionError: division by zero")
    print("2. LOCATE: Line 3 (the division)")
    print("3. CONTEXT: Empty list input causes len() to be 0")
    print("4. ASK: 'ZeroDivisionError when input is empty list. Code: [paste]. Expected: return 0 or error message'")
    print("5. APPLY: Add check for empty list")
    print("6. TEST: Try with empty list again")

    # FIXED version:
    def calculate_average_fixed(numbers):
        if len(numbers) == 0:
            return 0  # Handle empty list
        total = sum(numbers)
        return total / len(numbers)

    result = calculate_average_fixed([])
    print(f"\nFIXED! calculate_average([]) = {result}")
    print(f"calculate_average([1,2,3,4,5]) = {calculate_average_fixed([1,2,3,4,5])}")


# ============================================================
# ERROR TYPE 3: LOGIC ERROR
# The code runs without error but gives wrong results
# ============================================================

def logic_error_example():
    """Demonstrate finding and fixing a logic error"""
    print("\n" + "=" * 60)
    print("LOGIC ERROR EXAMPLE")
    print("=" * 60)

    # BROKEN version with wrong logic:
    def find_max_broken(numbers):
        max_val = 0  # Bug: assumes max is at least 0!
        for n in numbers:
            if n > max_val:
                max_val = n
        return max_val

    print("BROKEN CODE:")
    print("def find_max(numbers):")
    print("    max_val = 0  # <-- The bug is here")
    print("    for n in numbers:")
    print("        if n > max_val:")
    print("            max_val = n")
    print("    return max_val")

    test_input = [-5, -2, -8, -1]
    result = find_max_broken(test_input)
    print(f"\nTEST: find_max({test_input})")
    print(f"GOT: {result}")
    print(f"EXPECTED: -1 (the largest negative number)")

    print("\nDEBUGGING STEPS:")
    print("1. CAPTURE: Got 0, expected -1 (no crash, wrong answer)")
    print("2. LOCATE: Logic error - no line number, must trace")
    print("3. CONTEXT: Input was all negative numbers")
    print("4. ASK: 'find_max([-5,-2,-8,-1]) returns 0, should return -1. Starting max_val at 0 seems wrong.'")
    print("5. APPLY: Initialize max_val to first element or negative infinity")
    print("6. TEST: Try with all-negative list again")

    # FIXED version:
    def find_max_fixed(numbers):
        if not numbers:
            return None
        max_val = numbers[0]  # Start with first element!
        for n in numbers[1:]:
            if n > max_val:
                max_val = n
        return max_val

    result = find_max_fixed(test_input)
    print(f"\nFIXED! find_max({test_input}) = {result}")


# ============================================================
# COMPLETE DEBUGGING WORKFLOW
# ============================================================

def complete_workflow():
    """Show a complete debugging workflow"""
    print("\n" + "=" * 60)
    print("COMPLETE DEBUGGING WORKFLOW")
    print("=" * 60)

    # Real scenario: Processing sensor data
    def process_readings_broken(readings):
        """Original buggy function"""
        results = []
        for r in readings:
            celsius = (r - 32) * 5/9  # Assumes Fahrenheit, but some are strings!
            results.append(round(celsius, 1))
        return results

    sensor_data = [98.6, "error", 72.0, None, 68.0]

    print("\nSCENARIO: Process temperature sensor readings")
    print(f"Input: {sensor_data}")

    try:
        result = process_readings_broken(sensor_data)
    except TypeError as e:
        print(f"\nERROR: {type(e).__name__}: {e}")

    print("\n--- Applying the 6-step debugging flow ---")
    print("\n1. CAPTURE the error:")
    print("   TypeError: unsupported operand type(s) for -: 'str' and 'int'")

    print("\n2. LOCATE the problem:")
    print("   Line with: celsius = (r - 32) * 5/9")
    print("   When r = 'error' (a string)")

    print("\n3. CONTEXT:")
    print("   - Some sensor readings are error strings")
    print("   - Some might be None")
    print("   - Need to handle non-numeric values")

    print("\n4. ASK AI:")
    print("   'TypeError when processing sensor data. Code: [function]")
    print("    Input includes strings like \"error\" and None values.")
    print("    Expected: Skip invalid readings, return list of valid conversions.'")

    print("\n5. APPLY the fix:")

    def process_readings_fixed(readings):
        """Fixed function with error handling"""
        results = []
        skipped = []
        for i, r in enumerate(readings):
            # Skip None and non-numeric values
            if r is None:
                skipped.append((i, "None value"))
                continue
            if isinstance(r, str):
                skipped.append((i, f"String: {r}"))
                continue
            try:
                celsius = (r - 32) * 5 / 9
                results.append(round(celsius, 1))
            except (TypeError, ValueError) as e:
                skipped.append((i, str(e)))
        return {"converted": results, "skipped": skipped}

    result = process_readings_fixed(sensor_data)

    print("\n6. TEST the fix:")
    print(f"   Input: {sensor_data}")
    print(f"   Converted: {result['converted']}")
    print(f"   Skipped: {result['skipped']}")
    print("\n   SUCCESS! Handles all edge cases.")


# ============================================================
# RUN ALL EXAMPLES
# ============================================================

if __name__ == "__main__":
    syntax_error_example()
    runtime_error_example()
    logic_error_example()
    complete_workflow()

    print("\n" + "=" * 60)
    print("SUMMARY: For each error type:")
    print("  Syntax  -> Look at exact line, usually simple fix")
    print("  Runtime -> Check what input caused the crash")
    print("  Logic   -> Compare expected vs actual output")
    print("Always: Capture, Locate, Context, Ask, Apply, Test")
    print("=" * 60)
```

Run it:

```bash
python debugging_practice.py
```

**Expected Output:**

```
============================================================
SYNTAX ERROR EXAMPLE
============================================================
BROKEN CODE:

def calculate_area(length, width)   # Missing colon!
    return length * width

ERROR: SyntaxError: expected ':'
LINE: 1

DEBUGGING STEPS:
1. CAPTURE: SyntaxError: expected ':'
2. LOCATE: Line 1, after 'width)'
3. CONTEXT: Function definition line
4. ASK: 'SyntaxError expected colon on line 1: def calculate_area(length, width)'
5. APPLY: Add the missing colon
6. TEST: Run again

FIXED! calculate_area(5, 3) = 15

...

============================================================
SUMMARY: For each error type:
  Syntax  -> Look at exact line, usually simple fix
  Runtime -> Check what input caused the crash
  Logic   -> Compare expected vs actual output
Always: Capture, Locate, Context, Ask, Apply, Test
============================================================
```

The complete workflow example shows how to handle real-world debugging with messy data. The six-step process works for any error type.

---

## Key Takeaway

Debugging is a systematic process, not random guessing. Capture the error exactly. Locate where it happens. Gather context around the problem. Ask AI with all this information. Apply the fix. Test to confirm. The more information you provide at step 4, the faster you get to working code.

In the next chapter, we'll tackle what to do when you're completely stuck and nothing seems to work.

