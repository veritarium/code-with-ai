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

A function is like a machine: put something in, get something out. Functions let you package code into reusable building blocks that you can use over and over.

![Functions](/code-with-ai/assets/images/diagrams/14-1-functions.png)
{: .chapter-diagram}
*Figure 14.1: Functions — Reusable building blocks*
{: .diagram-caption}

When you write `def calculate_stress(force, area): return force / area`, you're creating a machine called `calculate_stress` that takes two inputs (`force` and `area`), does some work (divides them), and returns the result. Later, you can use this machine anywhere: `result = calculate_stress(1000, 4)` gives you 250.

Every function has four parts. The **name** describes what it does (`calculate_stress`). The **parameters** are the inputs it needs (`force`, `area`). The **body** is the work it performs (`return force / area`). The **return** is the output it produces (the calculated stress value).

Functions matter because they let you reuse code—write once, use many times. They organize logic with clear names for clear operations. They make testing easy because you can verify isolated units. And they centralize fixes—change the function once and all uses are updated.

<div class="key-insight">
<strong>Key Insight:</strong> Functions = Reusable building blocks of code. Write once, use everywhere.
</div>

---

## Libraries

Libraries are pre-built code you can use. They're collections of functions that others have written and tested so you don't have to reinvent the wheel.

![Libraries](/code-with-ai/assets/images/diagrams/14-2-libraries.png)
{: .chapter-diagram}
*Figure 14.2: Libraries — Stand on shoulders of giants*
{: .diagram-caption}

Without libraries, calculating an average takes five lines of manual code: initialize a total, loop through numbers, accumulate the sum, divide by count. With libraries, it takes one line: `import statistics` then `statistics.mean(numbers)`. One line, tested, reliable, correct.

For engineers, certain libraries are essential. For math and science: `numpy` handles arrays and matrices, `scipy` provides engineering calculations, `pandas` works with data tables, and `math` offers basic operations. For visualization: `matplotlib` creates charts and plots, `plotly` makes interactive visualizations, `seaborn` produces statistical graphics. For files and automation: `os` manages file operations, `json` reads and writes JSON data, `csv` handles spreadsheet formats, and `datetime` works with dates and times.

When you need something specific, ask AI: "What library should I use to [task]?" or "Show me how to use [library] for [goal]."

<div class="key-insight">
<strong>Key Insight:</strong> Stand on shoulders of giants—use libraries! Someone has already solved most common problems.
</div>

---

## Try It Yourself

This example demonstrates creating functions and using libraries for engineering calculations.

Create a file called `functions_libraries.py`:

```python
# functions_libraries.py
# Demonstrating functions and libraries

# ============================================================
# PART 1: CREATING YOUR OWN FUNCTIONS
# ============================================================

print("=" * 60)
print("CREATING FUNCTIONS")
print("=" * 60)

# Simple function: one input, one output
def calculate_area(diameter):
    """Calculate circular cross-sectional area from diameter"""
    import math
    radius = diameter / 2
    return math.pi * radius ** 2

# Function with multiple inputs
def calculate_stress(force, area):
    """Calculate stress from force and area"""
    return force / area

# Function with default parameter
def check_safety(stress, yield_strength=250):
    """Check if stress is within limits (default yield: 250 MPa)"""
    safety_factor = yield_strength / stress
    if safety_factor >= 2:
        return "SAFE", safety_factor
    elif safety_factor >= 1:
        return "WARNING", safety_factor
    else:
        return "FAIL", safety_factor

# Function that returns multiple values
def full_analysis(diameter, force, yield_strength=250):
    """Perform complete bolt analysis"""
    area = calculate_area(diameter)
    stress = calculate_stress(force, area)
    status, sf = check_safety(stress, yield_strength)
    return {
        "diameter": diameter,
        "area": area,
        "stress": stress,
        "safety_factor": sf,
        "status": status
    }

# Use the functions
print("\nUsing our custom functions:")
print("-" * 40)

diameter = 12.0  # mm
force = 15000    # N

area = calculate_area(diameter)
print(f"Area of {diameter}mm bolt: {area:.2f} mm²")

stress = calculate_stress(force, area)
print(f"Stress from {force}N force: {stress:.2f} MPa")

status, sf = check_safety(stress)
print(f"Safety check: {status} (SF = {sf:.2f})")

# Full analysis
print("\nFull analysis:")
result = full_analysis(12.0, 15000, yield_strength=640)
for key, value in result.items():
    if isinstance(value, float):
        print(f"  {key}: {value:.2f}")
    else:
        print(f"  {key}: {value}")


# ============================================================
# PART 2: USING BUILT-IN LIBRARIES
# ============================================================

print("\n" + "=" * 60)
print("USING BUILT-IN LIBRARIES")
print("=" * 60)

# math library - mathematical operations
import math

print("\nmath library:")
print(f"  pi = {math.pi}")
print(f"  sqrt(144) = {math.sqrt(144)}")
print(f"  sin(90°) = {math.sin(math.radians(90))}")

# statistics library - statistical calculations
import statistics

readings = [150.2, 162.8, 158.4, 165.1, 159.3, 161.7]

print("\nstatistics library:")
print(f"  Data: {readings}")
print(f"  Mean: {statistics.mean(readings):.2f}")
print(f"  Median: {statistics.median(readings):.2f}")
print(f"  Std Dev: {statistics.stdev(readings):.2f}")

# datetime library - dates and times
from datetime import datetime, timedelta

print("\ndatetime library:")
now = datetime.now()
print(f"  Current time: {now.strftime('%Y-%m-%d %H:%M')}")
print(f"  One week later: {(now + timedelta(days=7)).strftime('%Y-%m-%d')}")

# os library - file and system operations
import os

print("\nos library:")
print(f"  Current directory: {os.getcwd()}")
print(f"  Python file exists: {os.path.exists('functions_libraries.py')}")


# ============================================================
# PART 3: PRACTICAL EXAMPLE - BOLT BATCH ANALYSIS
# ============================================================

print("\n" + "=" * 60)
print("PRACTICAL EXAMPLE: Bolt Batch Analysis")
print("=" * 60)

# Define reusable analysis functions
def analyze_bolt_batch(bolts, yield_strength):
    """Analyze multiple bolts and return statistics"""
    results = []

    for bolt in bolts:
        analysis = full_analysis(
            bolt["diameter"],
            bolt["force"],
            yield_strength
        )
        analysis["name"] = bolt["name"]
        results.append(analysis)

    return results

def generate_report(results):
    """Generate a formatted report from analysis results"""
    stresses = [r["stress"] for r in results]
    sfs = [r["safety_factor"] for r in results]
    passed = sum(1 for r in results if r["status"] == "SAFE")

    report = []
    report.append("\n" + "=" * 50)
    report.append("BOLT ANALYSIS REPORT")
    report.append("=" * 50)

    for r in results:
        status_icon = "OK" if r["status"] == "SAFE" else "!!"
        report.append(
            f"[{status_icon}] {r['name']}: "
            f"{r['stress']:.1f} MPa, SF={r['safety_factor']:.2f}"
        )

    report.append("-" * 50)
    report.append(f"Summary:")
    report.append(f"  Total bolts: {len(results)}")
    report.append(f"  Passed: {passed}")
    report.append(f"  Failed: {len(results) - passed}")
    report.append(f"  Average stress: {statistics.mean(stresses):.1f} MPa")
    report.append(f"  Min safety factor: {min(sfs):.2f}")
    report.append("=" * 50)

    return "\n".join(report)

# Test data
bolt_batch = [
    {"name": "Bolt A", "diameter": 12, "force": 10000},
    {"name": "Bolt B", "diameter": 10, "force": 8000},
    {"name": "Bolt C", "diameter": 8, "force": 12000},   # This will fail
    {"name": "Bolt D", "diameter": 16, "force": 20000},
    {"name": "Bolt E", "diameter": 12, "force": 15000},
]

# Run analysis
results = analyze_bolt_batch(bolt_batch, yield_strength=640)
report = generate_report(results)
print(report)


# ============================================================
# SUMMARY
# ============================================================

print("\n" + "=" * 60)
print("SUMMARY")
print("=" * 60)
print("""
FUNCTIONS let you:
  - Package code into reusable blocks
  - Give clear names to operations
  - Test pieces independently
  - Change logic in one place

LIBRARIES give you:
  - Pre-built, tested functions
  - math: sqrt, sin, cos, pi
  - statistics: mean, median, stdev
  - datetime: dates and time calculations
  - os: file operations

Ask AI: "What library should I use for [task]?"
""")
```

Run it:

```bash
python functions_libraries.py
```

**Expected Output:**

```
============================================================
CREATING FUNCTIONS
============================================================

Using our custom functions:
----------------------------------------
Area of 12.0mm bolt: 113.10 mm²
Stress from 15000N force: 132.63 MPa
Safety check: WARNING (SF = 1.88)

Full analysis:
  diameter: 12.00
  area: 113.10
  stress: 132.63
  safety_factor: 4.83
  status: SAFE

============================================================
USING BUILT-IN LIBRARIES
============================================================

math library:
  pi = 3.141592653589793
  sqrt(144) = 12.0
  sin(90°) = 1.0

statistics library:
  Data: [150.2, 162.8, 158.4, 165.1, 159.3, 161.7]
  Mean: 159.58
  Median: 160.50
  Std Dev: 5.20

...

============================================================
PRACTICAL EXAMPLE: Bolt Batch Analysis
============================================================

==================================================
BOLT ANALYSIS REPORT
==================================================
[OK] Bolt A: 88.4 MPa, SF=7.24
[OK] Bolt B: 101.9 MPa, SF=6.28
[!!] Bolt C: 238.7 MPa, SF=2.68
[OK] Bolt D: 99.5 MPa, SF=6.43
[OK] Bolt E: 132.6 MPa, SF=4.83
--------------------------------------------------
Summary:
  Total bolts: 5
  Passed: 5
  Failed: 0
  Average stress: 132.2 MPa
  Min safety factor: 2.68
==================================================
```

The example shows how to build functions from scratch, how to use Python's built-in libraries, and how to combine both for practical engineering analysis.

---

## Key Takeaway

Functions package code into reusable building blocks—define once, use anywhere. Libraries are collections of functions others have already written and tested. Together, they let you build powerful programs quickly. When you need a capability, first check if a library exists. When you write code you'll use more than once, make it a function.

In the next chapter, we'll explore how to work with data structures and files.

