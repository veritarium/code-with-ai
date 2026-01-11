---
layout: chapter
title: "Functions and Libraries"
chapter: 14
part: 4
part_title: "Code Literacy"
part_url: "/part-4-literacy/"
prev: "/part-4-literacy/13-concepts"
prev_title: "Core Concepts"
next: "/part-4-literacy/15-data"
next_title: "Data and Files"
---

## Functions

A function is like a machine: put something in, get something out.

![Functions](/code-with-ai/assets/images/diagrams/14-1-functions.png)
{: .chapter-diagram}
*Figure 14.1: Functions — Reusable building blocks*
{: .diagram-caption}

```python
def calculate_stress(force, area):
    return force / area

result = calculate_stress(1000, 4)
# result is now 250
```

### Parts of a Function

- **Name** — what it does (`calculate_stress`)
- **Parameters** — inputs (`force`, `area`)
- **Body** — the work (`return force / area`)
- **Return** — output (the calculated stress)

### Why Use Functions?

- Reuse code (write once, use many times)
- Organize logic (clear names for clear operations)
- Test easily (isolated units you can verify)
- Fix in one place (change the function, all uses updated)

### Ask AI To

- "Create a function that..."
- "Explain this function"
- "What does it return?"
- "Add error handling to this function"

<div class="key-insight">
<strong>Key Insight:</strong> Functions = Reusable building blocks of code.
</div>

---

## Libraries

Libraries are pre-built code you can use. Don't reinvent the wheel.

![Libraries](/code-with-ai/assets/images/diagrams/14-2-libraries.png)
{: .chapter-diagram}
*Figure 14.2: Libraries — Stand on shoulders of giants*
{: .diagram-caption}

**Without libraries:**
```python
# Calculate average manually
total = 0
for num in numbers:
    total = total + num
average = total / len(numbers)
```
5 lines, reinventing the wheel.

**With libraries:**
```python
import statistics
average = statistics.mean(numbers)
```
1 line, tested, reliable.

### Libraries for Engineers

**Math/Science**
- `numpy` — Arrays, matrices
- `scipy` — Engineering calculations
- `pandas` — Data tables
- `math` — Basic math operations

**Visualization**
- `matplotlib` — Charts, plots
- `plotly` — Interactive plots
- `seaborn` — Statistical visualization

**Files/Automation**
- `os` — File operations
- `json` — Read/write JSON
- `csv` — Spreadsheets
- `datetime` — Dates and times

**Ask AI:** "What library should I use to [task]?" or "Show me how to use [library] for [goal]"

<div class="key-insight">
<strong>Key Insight:</strong> Stand on shoulders of giants — use libraries!
</div>
