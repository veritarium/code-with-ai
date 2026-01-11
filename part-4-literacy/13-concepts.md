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

Practice understanding core concepts:

- "Create a variable to store a bolt diameter of 12.5mm"
- "Write an if statement that prints 'Fail' if stress is over 250"
- "Create a for loop that prints each item in a list of bolt sizes"
- "What's the difference between a for loop and a while loop?"
- "Show me an example of a boolean variable and how to use it in an if statement"
- "Create a list of numbers and write a loop that calculates their sum"

---

## Key Takeaway

Variables and control flow are the foundation of all programming. Variables are just named containers—think labeled boxes. Control flow uses if/else for decisions, for loops to process collections, and while loops to repeat until done. Every complex program is built from these simple pieces combined in different ways.

In the next chapter, we'll explore functions—how to package code into reusable building blocks.

