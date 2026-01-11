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

## Variables

Variables are named containers for data. That's it.

Think of them like labeled boxes. The name tells you what's inside.

![Variables](/code-with-ai/assets/images/diagrams/13-1-variables.png)
{: .chapter-diagram}
*Figure 13.1: Variables — Named containers for data*
{: .diagram-caption}

```python
bolt_diameter = 12.5
```

This creates a box labeled `bolt_diameter` and puts the value `12.5` inside it.

### Types of Data You Can Store

**NUMBERS**
```python
count = 42
price = 19.99
stress = 250.5
```

**TEXT** (called "strings")
```python
name = "M12"
grade = "8.8"
status = "OK"
```

**TRUE/FALSE** (called "booleans")
```python
is_valid = True
has_error = False
passed = True
```

**LISTS** (multiple items)
```python
sizes = [8, 10, 12]
```

### Naming Rules

- No spaces (use underscores: `bolt_count`, not `bolt count`)
- Start with a letter
- Be descriptive

Good names: `bolt_count`, `max_stress`, `is_valid`
Bad names: `x`, `bc`, `thing1`

<div class="key-insight">
<strong>Key Insight:</strong> Good variable names make code self-documenting. When you read <code>if stress > max_allowable_stress</code>, you know exactly what's being checked.
</div>

---

## Control Flow

How programs make decisions and repeat actions. Three patterns handle most logic.

![Control Flow](/code-with-ai/assets/images/diagrams/13-2-control-flow.png)
{: .chapter-diagram}
*Figure 13.2: Control Flow — Decisions and repetition*
{: .diagram-caption}

**IF/ELSE — Decisions**

```python
if stress > 250:
    print("Fail")
else:
    print("Pass")
```

Check a condition. If true, do one thing. If false, do another. Like a fork in the road.

**FOR LOOP — Repeat N times**

```python
for size in [8, 10, 12]:
    print(size)
```

Do something for each item in a list. Process each one, then move to the next.

**WHILE LOOP — Repeat until**

```python
while error > 0.01:
    refine()
```

Keep going until a condition is met. Don't know how many times in advance.

### Summary

| Pattern | Purpose |
|---------|---------|
| `if/else` | Choose between options |
| `for` | Do something N times |
| `while` | Keep going until done |

That's it. These three patterns handle most logic you'll ever need.

<div class="key-insight">
<strong>Key Insight:</strong> Programs = Data + Decisions + Repetition
</div>
