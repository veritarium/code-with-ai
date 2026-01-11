---
layout: chapter
title: "The Loop"
chapter: 2
part: 1
part_title: "Foundations"
part_url: "/part-1-foundations/"
prev: "/part-1-foundations/01-core"
prev_title: "The Core Partnership"
next: "/part-1-foundations/03-operations"
next_title: "Six Operations"
---

This is how every coding session with AI actually works. Memorize this loop.

![The Loop](/code-with-ai/assets/images/diagrams/02-1-the-loop.png)
{: .chapter-diagram}
*Figure 2.1: The Loop — Describe, Get, Run, Evaluate, Repeat*
{: .diagram-caption}

The loop has five steps, and you'll repeat them constantly. First, you **DESCRIBE** what you want to AI. Something like "Create a function that calculates bolt stress from force and area." Then AI gives you code—the **GET** step. The code might be perfect. It probably won't be.

Next comes the critical step most beginners skip: **RUN**. You actually execute the code. Not just look at it. Not just assume it works. Run it with real inputs and see what happens.

Then you **EVALUATE**. Does it work? Does it do what you wanted? This is where your engineering judgment matters most. AI doesn't know if the output makes sense for your application—you do. A stress calculation that returns negative megapascals might be syntactically correct but physically meaningless.

Finally, you make a decision: **Done or Refine?** If it works, you're done. Move on. If it doesn't, you go back to DESCRIBE with more information. "The function works but returns negative values when force is negative. Add validation to reject negative inputs." This loop might run once. It might run ten times. That's normal. Every professional developer works this way—the only difference is they've done more loops.

<div class="key-insight">
<strong>Key Insight:</strong> Every problem is solvable through iteration. You don't need to get it right the first time. You need to keep going until it's right.
</div>

---

## The Draft Mindset

Here's what most beginners get wrong: they expect perfection on the first try.

![The Draft](/code-with-ai/assets/images/diagrams/02-2-the-draft.png)
{: .chapter-diagram}
*Figure 2.2: The Draft — Progress through iteration*
{: .diagram-caption}

Look at this progression. Version 1 is maybe 10% of what you want. It's rough. It might not even run. That's fine. That's the *draft*. Version 2 gets you to 40%—now the basic structure works, but maybe the output format is wrong. Version 3 reaches 75%—it's doing the right calculation but doesn't handle edge cases. Version 4 hits 100%. It works. Ship it.

When you write an engineering report, do you expect the first draft to be perfect? Of course not. You write, review, revise, repeat. Code works the same way. The first output from AI is a starting point, not a final answer. Your job is to test it, identify what's wrong, and guide the refinement.

This mindset shift is crucial. Stop asking "why didn't AI give me perfect code?" and start asking "what do I need to tell AI to make this better?"

<div class="key-insight">
<strong>Key Insight:</strong> Treat AI output like a first draft, not a final answer.
</div>

---

## Try It Yourself

Let's experience the loop in action. This example shows iterative refinement—a common pattern where you start simple and improve through multiple passes.

Create a file called `iterative_refinement.py`:

```python
# iterative_refinement.py
# Demonstrating the describe-get-run-evaluate loop

def calculate_stress_v1(force, area):
    """Version 1: Basic calculation"""
    return force / area

def calculate_stress_v2(force, area):
    """Version 2: Added units"""
    stress = force / area
    return f"{stress} Pa"

def calculate_stress_v3(force, area):
    """Version 3: Handle edge cases"""
    if area <= 0:
        return "Error: Area must be positive"
    if force < 0:
        return "Error: Force cannot be negative"
    stress = force / area
    return f"{stress:.2f} Pa"

def calculate_stress_v4(force, area, yield_strength=250e6):
    """Version 4: Complete with safety check"""
    if area <= 0:
        return "Error: Area must be positive"
    if force < 0:
        return "Error: Force cannot be negative"

    stress = force / area
    safety_factor = yield_strength / stress

    result = f"Stress: {stress/1e6:.2f} MPa\n"
    result += f"Safety Factor: {safety_factor:.2f}\n"
    if safety_factor < 2:
        result += "WARNING: Safety factor below 2!"
    else:
        result += "OK: Design is safe"
    return result

# Test each version to see the progression
print("=== Version 1: Basic ===")
print(calculate_stress_v1(1000, 0.001))
print()

print("=== Version 2: With units ===")
print(calculate_stress_v2(1000, 0.001))
print()

print("=== Version 3: With validation ===")
print(calculate_stress_v3(1000, 0.001))
print(calculate_stress_v3(-1000, 0.001))  # Test negative force
print(calculate_stress_v3(1000, 0))        # Test zero area
print()

print("=== Version 4: Complete ===")
print(calculate_stress_v4(1000, 0.001))
print()
print(calculate_stress_v4(50000, 0.001))  # Higher stress
```

Run it:

```bash
python iterative_refinement.py
```

**Expected Output:**

```
=== Version 1: Basic ===
1000000.0

=== Version 2: With units ===
1000000.0 Pa

=== Version 3: With validation ===
1000000.00 Pa
Error: Force cannot be negative
Error: Area must be positive

=== Version 4: Complete ===
Stress: 1.00 MPa
Safety Factor: 250.00
OK: Design is safe

Stress: 50.00 MPa
Safety Factor: 5.00
OK: Design is safe
```

Notice how each version improves on the last. Version 1 just does math. Version 2 adds units. Version 3 catches bad inputs. Version 4 adds engineering context with safety factors. This is exactly how you'll work with AI—start simple, test, identify gaps, refine.

---

## Key Takeaway

The loop is your fundamental workflow. Every time you work with AI, you'll describe what you want, get code, run it, evaluate whether it works, and either finish or refine. Expect multiple iterations. Plan for them. The goal isn't perfect code on the first try—it's working code after enough loops.

In the next chapter, we'll categorize all the different types of operations you can perform in this loop.

