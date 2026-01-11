---
layout: chapter
title: "Common Pitfalls"
chapter: 9
part: 3
part_title: "Problems"
part_url: "/part-3-pitfalls/"
prev: "/part-2-skills/08-restart"
prev_title: "When to Restart"
next: "/part-3-pitfalls/10-debugging"
next_title: "Debugging"
---

Let's talk about mistakes. Every beginner makes these. Now you won't.

![Common Traps](/code-with-ai/assets/images/diagrams/09-1-common-traps.png)
{: .chapter-diagram}
*Figure 9.1: Common Traps — Mistakes everyone makes*
{: .diagram-caption}

There are six traps that catch nearly every beginner. The first is **BLIND TRUST**—running code without reading it. AI-generated code can have bugs, security issues, or simply not do what you think. Always review before running, and ask AI to explain what the code does if you're unsure.

The second trap is **VAGUE PROMPTS**. Requests like "Make it better" or "Fix this" force AI to guess what you mean, and it will usually guess wrong. Be specific about what's wrong. State the expected behavior versus the actual behavior.

**TOO BIG TASKS** is the third trap. Asking AI to "Build me a whole app" gives it too much to handle at once. AI loses focus, you lose control, and the result satisfies no one. Break the work into small tasks and tackle one feature at a time.

The fourth trap is **NO CONTEXT**. Not sharing error messages or relevant code leaves AI working blind. It can't fix what it can't see. Paste the errors, include the code, share the full context.

**GIVING UP TOO FAST** catches many beginners who quit after the first attempt fails. But you might have been one iteration away from success. Give it 3-5 attempts before considering a different approach.

Finally, **NOT LEARNING** happens when you copy-paste solutions without understanding them. You never build skills this way, and you'll face the same problems again. Ask AI to explain. Learn from each solution.

<div class="key-insight">
<strong>Key Insight:</strong> Most traps come from treating AI like magic instead of a tool. Stay engaged, stay specific, stay curious.
</div>

---

## Trust Levels

How much should you trust AI's output? It depends on the consequences of failure.

![Trust Levels](/code-with-ai/assets/images/diagrams/09-2-trust-levels.png)
{: .chapter-diagram}
*Figure 9.2: Trust Levels — How much verification is needed*
{: .diagram-caption}

**LOW TRUST** requires verifying everything. Use this level for security-related code, financial calculations, safety-critical systems, and data deletion operations. Read every line. Test thoroughly. Get a second opinion if needed. Understand fully before deploying.

**MEDIUM TRUST** means reviewing and testing. Use this for standard features, business logic, API integrations, and database operations. Skim the code to understand its structure. Run basic tests. Check edge cases. Verify the behavior matches expectations.

**HIGH TRUST** allows a quick check. Use this for simple utilities, formatting code, text manipulation, and documentation. Glance at the output, run it once, check that it works, and move on.

The key insight is that trust level depends on consequences of failure, not on how confident AI seems. AI might be very confident about code that deletes your database. That doesn't mean you should trust it blindly. For a bolt stress calculator in a real engineering application? Low trust—verify everything. For a script that renames files in a folder? Higher trust—a quick check suffices.

<div class="key-insight">
<strong>Key Insight:</strong> Higher stakes = More verification needed. Trust level depends on consequences, not AI confidence.
</div>

---

## Try It Yourself

This example demonstrates all six traps and their fixes, showing you what bad patterns look like and how to avoid them.

Create a file called `common_traps.py`:

```python
# common_traps.py
# Demonstrating the six common traps and how to avoid them

# === TRAP 1: BLIND TRUST ===
# Never run code without understanding it first

def trap1_blind_trust():
    """Example of blind trust trap"""
    print("\nTRAP 1: BLIND TRUST")
    print("-" * 50)

    # BAD: AI gave you this code and you ran it without reading
    dangerous_code = """
    import os
    os.system('rm -rf /important_data')  # This deletes your data!
    """
    print("BAD: Running AI code without reviewing it")
    print(f"Dangerous code that could have been run:\n{dangerous_code}")

    # GOOD: Always review and understand
    print("\nGOOD: Review code before running")
    print("- Read each line and understand what it does")
    print("- Ask AI: 'Explain what this code does line by line'")
    print("- Look for file operations, network calls, system commands")


# === TRAP 2: VAGUE PROMPTS ===
# Being specific gets better results

def trap2_vague_prompts():
    """Example of vague prompts trap"""
    print("\nTRAP 2: VAGUE PROMPTS")
    print("-" * 50)

    # BAD: Vague request
    print("BAD Prompt: 'Make this better'")
    print("Result: AI guesses what 'better' means to you")

    # GOOD: Specific request
    print("\nGOOD Prompt: 'Add input validation to reject negative")
    print("numbers and return an error message explaining why'")
    print("Result: AI knows exactly what to implement")


# === TRAP 3: TOO BIG TASKS ===
# Break large tasks into small pieces

def trap3_too_big():
    """Example of too-big-tasks trap"""
    print("\nTRAP 3: TOO BIG TASKS")
    print("-" * 50)

    # BAD: One massive request
    print("BAD: 'Build me a complete inventory system with")
    print("database, web interface, reports, and user auth'")

    # GOOD: Break it down
    print("\nGOOD: Break into steps:")
    tasks = [
        "1. Create a function to add an item to inventory",
        "2. Create a function to remove an item",
        "3. Create a function to list all items",
        "4. Add a simple text file storage",
        "5. Add a command-line interface",
        "6. (Later) Add database, web UI, etc."
    ]
    for task in tasks:
        print(f"   {task}")


# === TRAP 4: NO CONTEXT ===
# AI can only see what you show it

def trap4_no_context():
    """Example of no context trap"""
    print("\nTRAP 4: NO CONTEXT")
    print("-" * 50)

    # BAD: No context provided
    print("BAD: 'Why doesn't my code work?'")
    print("AI response: 'I don't know, I can't see your code!'")

    # GOOD: Full context
    print("\nGOOD: 'My function crashes with TypeError:")
    print("  TypeError: unsupported operand type(s) for +: int and str")
    print("  Here is the code:")
    print("    def add_values(a, b):")
    print("        return a + b")
    print("  Called with: add_values(5, \"10\")")
    print("  Expected: 15'")


# === TRAP 5: GIVING UP TOO FAST ===
# Persistence pays off

def trap5_giving_up():
    """Example of giving up too fast trap"""
    print("\nTRAP 5: GIVING UP TOO FAST")
    print("-" * 50)

    # BAD: Quit after first failure
    print("BAD: First attempt failed -> 'AI doesn't work' -> Give up")

    # GOOD: Iterate and refine
    print("\nGOOD: Apply the 5-attempt rule:")
    attempts = [
        ("Attempt 1", "Try", "Didn't work"),
        ("Attempt 2", "Add more details", "Closer"),
        ("Attempt 3", "Include error message", "Almost there"),
        ("Attempt 4", "Provide example input", "Works!"),
    ]
    for attempt, action, result in attempts:
        print(f"   {attempt}: {action} -> {result}")


# === TRAP 6: NOT LEARNING ===
# Understand, don't just copy

def trap6_not_learning():
    """Example of not learning trap"""
    print("\nTRAP 6: NOT LEARNING")
    print("-" * 50)

    # BAD: Copy-paste without understanding
    print("BAD: Copy code, paste code, move on")
    print("Result: Same problems keep happening")

    # GOOD: Learn from each solution
    print("\nGOOD: Ask AI to explain:")
    print("   'Why did you use a list comprehension here?'")
    print("   'What does the enumerate() function do?'")
    print("   'Why is try/except better than checking type?'")
    print("Result: Build skills that compound over time")


# === DEMONSTRATION: The cost of each trap ===

def demonstrate_trap_cost():
    """Show the real cost of falling into traps"""
    print("\n" + "=" * 60)
    print("THE COST OF TRAPS")
    print("=" * 60)

    traps_costs = [
        ("Blind Trust", "Security breach, data loss, system damage"),
        ("Vague Prompts", "10+ iterations instead of 2-3"),
        ("Too Big Tasks", "Unusable code that needs complete rewrite"),
        ("No Context", "Wrong fixes that create new bugs"),
        ("Giving Up Fast", "Abandoned projects, wasted time"),
        ("Not Learning", "Repeating same mistakes forever"),
    ]

    for trap, cost in traps_costs:
        print(f"\n{trap}:")
        print(f"   Cost: {cost}")


# === RUN ALL DEMONSTRATIONS ===

if __name__ == "__main__":
    print("=" * 60)
    print("COMMON TRAPS IN AI-ASSISTED CODING")
    print("=" * 60)

    trap1_blind_trust()
    trap2_vague_prompts()
    trap3_too_big()
    trap4_no_context()
    trap5_giving_up()
    trap6_not_learning()

    demonstrate_trap_cost()

    print("\n" + "=" * 60)
    print("SUMMARY: Avoid these six traps and you'll succeed faster")
    print("than 90% of people starting with AI-assisted coding.")
    print("=" * 60)
```

Run it:

```bash
python common_traps.py
```

**Expected Output:**

```
============================================================
COMMON TRAPS IN AI-ASSISTED CODING
============================================================

TRAP 1: BLIND TRUST
--------------------------------------------------
BAD: Running AI code without reviewing it
Dangerous code that could have been run:

    import os
    os.system('rm -rf /important_data')  # This deletes your data!


GOOD: Review code before running
- Read each line and understand what it does
- Ask AI: 'Explain what this code does line by line'
- Look for file operations, network calls, system commands

TRAP 2: VAGUE PROMPTS
--------------------------------------------------
BAD Prompt: 'Make this better'
Result: AI guesses what 'better' means to you

GOOD Prompt: 'Add input validation to reject negative
numbers and return an error message explaining why'
Result: AI knows exactly what to implement

TRAP 3: TOO BIG TASKS
--------------------------------------------------
BAD: 'Build me a complete inventory system with
database, web interface, reports, and user auth'

GOOD: Break into steps:
   1. Create a function to add an item to inventory
   2. Create a function to remove an item
   3. Create a function to list all items
   4. Add a simple text file storage
   5. Add a command-line interface
   6. (Later) Add database, web UI, etc.

...

============================================================
SUMMARY: Avoid these six traps and you'll succeed faster
than 90% of people starting with AI-assisted coding.
============================================================
```

Each trap is demonstrated with its bad pattern and the corresponding fix. Understanding these patterns now will save you hours of frustration later.

---

## Key Takeaway

The six traps—blind trust, vague prompts, tasks too big, no context, giving up fast, and not learning—catch most beginners. Now that you know them, you can avoid them. Stay engaged with the code, be specific in your requests, break work into small pieces, share full context, persist through difficulties, and always aim to understand what AI gives you.

In the next chapter, we'll tackle debugging—what to do when things go wrong.

