---
layout: chapter
title: "Feedback"
chapter: 6
part: 2
part_title: "Skills"
part_url: "/part-2-skills/"
prev: "/part-2-skills/05-precision"
prev_title: "Precision"
next: "/part-2-skills/07-context"
next_title: "Context"
---

AI gave you something. It's not quite right. What do you say next?

This is where most beginners fail. They give bad feedback, and then wonder why AI keeps giving them wrong answers.

![Good vs Bad Feedback](/code-with-ai/assets/images/diagrams/06-1-good-vs-bad.png)
{: .chapter-diagram}
*Figure 6.1: Good vs Bad Feedback — What works and what doesn't*
{: .diagram-caption}

Bad feedback leaves AI guessing. "It doesn't work" tells AI nothing about what's wrong—doesn't work how? What happened? What did you expect? Saying "This is wrong" raises the question: wrong how? What's the correct behavior? "Fix it" provides no direction—fix what? AI will guess, and it will guess wrong. "That's not what I wanted" begs the question: then what DID you want? AI can't read your mind.

Good feedback is specific and actionable. "Getting error: TypeError on line 15" tells AI exactly where to look. "Output is 5, but should be 10" defines the gap AI needs to close. "Change the loop to start at 1, not 0" gives AI the exact modification needed. "Add validation: reject negative numbers" specifies the new requirement clearly.

See the pattern? Good feedback tells AI exactly what's wrong and often suggests what needs to change. The more information you provide, the faster you get to working code.

<div class="key-insight">
<strong>Key Insight:</strong> Specific feedback → Specific fixes → Done faster.
</div>

---

## The Feedback Formula

Here's a formula you can use every time AI gives you something that's not quite right.

![The Formula](/code-with-ai/assets/images/diagrams/06-2-the-formula.png)
{: .chapter-diagram}
*Figure 6.2: The Feedback Formula — Got X, Expected Y, Change Z*
{: .diagram-caption}

The formula is simple: **"Got [X]. Expected [Y]. Change [Z]."** Three parts. Complete information. Immediate fix.

**GOT [X]** describes what actually happened—the current output, the error message, the current behavior. Be specific. Copy-paste exact values and messages.

**EXPECTED [Y]** describes what should happen—the correct output, the desired behavior, the expected result. This gives AI a clear target.

**CHANGE [Z]** suggests what to modify—the specific fix, which part to change. This part is optional but helpful when you know what's wrong.

Here's an example in action. You ask AI for a function to calculate the product of a list, and it gives you something that returns 15 for input [1, 2, 3, 4, 5]. You know the product should be 120. Using the formula: "The function returns 15 for input [1,2,3,4,5] but should return 120—it's calculating the sum instead of the product. Change the addition to multiplication in the loop."

AI now has everything it needs. One response, done.

<div class="key-insight">
<strong>Key Insight:</strong> Complete information = One-shot fix.
</div>

---

## Try It Yourself

This example demonstrates the feedback process. We start with buggy code, apply the feedback formula, and produce corrected versions.

Create a file called `feedback_correction.py`:

```python
# feedback_correction.py
# Demonstrating how to fix code using the feedback formula

# === ORIGINAL CODE (has bugs) ===
def calculate_average_v1(numbers):
    """First version: Has a bug"""
    total = 0
    for n in numbers:
        total = total + n
    return total  # BUG: Returns sum, not average!

# === FEEDBACK: "Got 15 for [1,2,3,4,5]. Expected 3. Divide by length." ===
def calculate_average_v2(numbers):
    """Second version: Fixed the average calculation"""
    total = 0
    for n in numbers:
        total = total + n
    return total / len(numbers)  # FIXED: Now divides by count

# === FEEDBACK: "Got ZeroDivisionError for empty list. Expected 0 or error message." ===
def calculate_average_v3(numbers):
    """Third version: Handles empty list"""
    if len(numbers) == 0:
        return 0  # FIXED: Handle empty list
    total = 0
    for n in numbers:
        total = total + n
    return total / len(numbers)

# === FEEDBACK: "Got TypeError for [1,'two',3]. Expected to skip non-numbers." ===
def calculate_average_v4(numbers):
    """Fourth version: Handles mixed types"""
    valid_numbers = []
    for n in numbers:
        if isinstance(n, (int, float)):
            valid_numbers.append(n)  # FIXED: Filter non-numbers

    if len(valid_numbers) == 0:
        return 0

    total = sum(valid_numbers)
    return total / len(valid_numbers)


# === Demonstrate the feedback loop ===
if __name__ == "__main__":
    test_cases = [
        ([1, 2, 3, 4, 5], "Normal list"),
        ([], "Empty list"),
        ([1, 'two', 3, None, 5], "Mixed types"),
    ]

    print("FEEDBACK LOOP DEMONSTRATION")
    print("=" * 60)

    # Version 1: Original buggy code
    print("\nVERSION 1: Original code")
    print("-" * 60)
    numbers = [1, 2, 3, 4, 5]
    result = calculate_average_v1(numbers)
    print(f"Input: {numbers}")
    print(f"Got: {result}")
    print(f"Expected: 3.0")
    print("FEEDBACK: 'Got 15, expected 3. Divide total by length.'")

    # Version 2: Fixed average
    print("\nVERSION 2: After first feedback")
    print("-" * 60)
    result = calculate_average_v2(numbers)
    print(f"Input: {numbers}")
    print(f"Got: {result}")
    print("SUCCESS! But let's test edge cases...")

    print("\nTesting empty list with V2...")
    try:
        result = calculate_average_v2([])
        print(f"Got: {result}")
    except ZeroDivisionError as e:
        print(f"Got: ZeroDivisionError!")
        print("FEEDBACK: 'Got ZeroDivisionError for []. Expected 0 or error message.'")

    # Version 3: Handles empty list
    print("\nVERSION 3: After second feedback")
    print("-" * 60)
    result = calculate_average_v3([])
    print(f"Input: []")
    print(f"Got: {result}")
    print("SUCCESS! Empty list handled. Testing mixed types...")

    print("\nTesting mixed types with V3...")
    try:
        result = calculate_average_v3([1, 'two', 3, None, 5])
        print(f"Got: {result}")
    except TypeError as e:
        print(f"Got: TypeError!")
        print("FEEDBACK: 'Got TypeError for mixed list. Expected to skip non-numbers.'")

    # Version 4: Final working version
    print("\nVERSION 4: After third feedback (FINAL)")
    print("-" * 60)
    for test_input, description in test_cases:
        result = calculate_average_v4(test_input)
        print(f"Input: {test_input} ({description})")
        print(f"Result: {result}")
        print()

    print("=" * 60)
    print("SUMMARY: Three rounds of specific feedback produced robust code.")
    print("Each 'Got X, Expected Y, Change Z' led to a targeted fix.")
    print("=" * 60)
```

Run it:

```bash
python feedback_correction.py
```

**Expected Output:**

```
FEEDBACK LOOP DEMONSTRATION
============================================================

VERSION 1: Original code
------------------------------------------------------------
Input: [1, 2, 3, 4, 5]
Got: 15
Expected: 3.0
FEEDBACK: 'Got 15, expected 3. Divide total by length.'

VERSION 2: After first feedback
------------------------------------------------------------
Input: [1, 2, 3, 4, 5]
Got: 3.0
SUCCESS! But let's test edge cases...

Testing empty list with V2...
Got: ZeroDivisionError!
FEEDBACK: 'Got ZeroDivisionError for []. Expected 0 or error message.'

VERSION 3: After second feedback
------------------------------------------------------------
Input: []
Got: 0
SUCCESS! Empty list handled. Testing mixed types...

Testing mixed types with V3...
Got: TypeError!
FEEDBACK: 'Got TypeError for mixed list. Expected to skip non-numbers.'

VERSION 4: After third feedback (FINAL)
------------------------------------------------------------
Input: [1, 2, 3, 4, 5] (Normal list)
Result: 3.0

Input: [] (Empty list)
Result: 0

Input: [1, 'two', 3, None, 5] (Mixed types)
Result: 3.0

============================================================
SUMMARY: Three rounds of specific feedback produced robust code.
Each 'Got X, Expected Y, Change Z' led to a targeted fix.
============================================================
```

Three rounds of specific feedback transformed buggy code into a robust function. Each iteration addressed one specific problem identified by the feedback formula. This is faster and more reliable than vague complaints like "it doesn't work."

---

## Key Takeaway

When AI gives you something wrong, resist the urge to say "fix it" and instead use the formula: Got [X], Expected [Y], Change [Z]. The more specific your feedback, the faster AI can correct the issue. Every piece of information you provide eliminates guesswork and gets you closer to done.

In the next chapter, we'll explore how to give AI the context it needs to understand your problem fully.

