---
layout: chapter
title: "Six Operations"
chapter: 3
part: 1
part_title: "Foundations"
part_url: "/part-1-foundations/"
prev: "/part-1-foundations/02-loop"
prev_title: "The Loop"
next: "/part-2-skills/04-decomposition"
next_title: "Decomposition"
---

Everything you'll ever do with AI coding falls into six categories. Just six.

![Six Operations](/code-with-ai/assets/images/diagrams/03-1-six-operations.png)
{: .chapter-diagram}
*Figure 3.1: The Six Operations — Everything you can do with AI*
{: .diagram-caption}

Understanding these operations transforms vague requests into precise instructions. When you're stuck, ask yourself: "Which operation am I trying to do?" Then structure your prompt around that operation.

**CREATE** means making something new. This is where you start most projects. You might say "Create a function that calculates beam deflection" or "Build a script that converts CSV to JSON." The key word is *new*—you're generating code that doesn't exist yet.

**READ** means understanding existing code. When you inherit someone else's code or revisit your own after months away, you need to understand what it does before you can work with it. Ask AI "Explain what this function does" or "What does line 15 mean?" Reading code is a skill unto itself, and AI excels at explaining.

**EDIT** means changing existing code. You have something that works, but it needs modification. "Change this to use metric units instead of imperial" or "Modify the output format to include headers." Editing is often safer than creating from scratch because you're building on proven foundations.

**RUN** is the only operation AI can't do for you. You must execute the code and observe the results. This is your reality check. Code might look correct but fail in practice. Run it. See what happens.

**FIX** is debugging—finding and correcting errors. When you see an error message, paste it directly: "I'm getting this error: [error message]. Here's the code. Fix it." The more context you provide, the better AI can diagnose the problem.

**EXTEND** means adding capabilities to existing code. Your calculator works, but now you want it to save results to a file. "Add a feature that exports results to CSV" or "Now make it also handle negative numbers." Extension builds incrementally on what you've already achieved.

<div class="key-insight">
<strong>Key Insight:</strong> Knowing these six operations gives you a vocabulary for working with AI. You're not just "asking AI to help"—you're performing specific operations that have specific patterns.
</div>

---

## Try It Yourself

This example demonstrates all six operations in a single workflow. You'll create code, read it, edit it, run it, fix an error, and extend its functionality.

Create a file called `six_operations.py`:

```python
# six_operations.py
# Demonstrating CREATE, READ, EDIT, RUN, FIX, EXTEND

import os

# === CREATE: Make a new file with data ===
def create_data_file(filename):
    """Create a simple data file with measurements"""
    data = """measurement,value,unit
    length,2.5,meters
    width,1.8,meters
    height,3.2,meters
    """
    with open(filename, 'w') as f:
        f.write(data)
    print(f"CREATE: File '{filename}' created")

# === READ: Load and display the file contents ===
def read_data_file(filename):
    """Read and explain what's in the file"""
    with open(filename, 'r') as f:
        content = f.read()
    print(f"READ: Contents of '{filename}':")
    print(content)
    print("This file contains measurement data in CSV format")
    print("with columns for measurement name, value, and unit.")

# === EDIT: Modify the data ===
def edit_data_file(filename):
    """Change meters to feet (multiply by 3.281)"""
    with open(filename, 'r') as f:
        lines = f.readlines()

    new_lines = [lines[0]]  # Keep header
    for line in lines[1:]:
        if line.strip():
            parts = line.strip().split(',')
            if parts[2] == 'meters':
                new_value = float(parts[1]) * 3.281
                new_lines.append(f"    {parts[0]},{new_value:.2f},feet\n")

    with open(filename, 'w') as f:
        f.writelines(new_lines)
    print(f"EDIT: Converted all values from meters to feet")

# === FIX: Handle potential errors ===
def safe_read_file(filename):
    """Read file with error handling"""
    try:
        with open(filename, 'r') as f:
            return f.read()
    except FileNotFoundError:
        print(f"FIX: File '{filename}' not found!")
        return None
    except Exception as e:
        print(f"FIX: Error reading file: {e}")
        return None

# === EXTEND: Add volume calculation ===
def calculate_volume(filename):
    """Extend functionality to calculate volume from measurements"""
    content = safe_read_file(filename)
    if not content:
        return

    measurements = {}
    lines = content.strip().split('\n')
    for line in lines[1:]:  # Skip header
        if line.strip():
            parts = line.strip().split(',')
            measurements[parts[0]] = float(parts[1])

    if all(k in measurements for k in ['length', 'width', 'height']):
        volume = measurements['length'] * measurements['width'] * measurements['height']
        print(f"EXTEND: Calculated volume = {volume:.2f} cubic feet")
    else:
        print("EXTEND: Cannot calculate volume - missing measurements")

# === RUN: Execute the workflow ===
if __name__ == "__main__":
    filename = "measurements.csv"

    print("=" * 50)
    create_data_file(filename)
    print()

    print("=" * 50)
    read_data_file(filename)
    print()

    print("=" * 50)
    edit_data_file(filename)
    print()

    print("=" * 50)
    read_data_file(filename)  # See the edited version
    print()

    print("=" * 50)
    calculate_volume(filename)
    print()

    # Test error handling
    print("=" * 50)
    safe_read_file("nonexistent.csv")

    # Clean up
    os.remove(filename)
    print(f"\nCleaned up: removed {filename}")
```

Run it:

```bash
python six_operations.py
```

**Expected Output:**

```
==================================================
CREATE: File 'measurements.csv' created

==================================================
READ: Contents of 'measurements.csv':
measurement,value,unit
    length,2.5,meters
    width,1.8,meters
    height,3.2,meters

This file contains measurement data in CSV format
with columns for measurement name, value, and unit.

==================================================
EDIT: Converted all values from meters to feet

==================================================
READ: Contents of 'measurements.csv':
measurement,value,unit
    length,8.20,feet
    width,5.91,feet
    height,10.50,feet

This file contains measurement data in CSV format
with columns for measurement name, value, and unit.

==================================================
EXTEND: Calculated volume = 509.05 cubic feet

==================================================
FIX: File 'nonexistent.csv' not found!

Cleaned up: removed measurements.csv
```

Each function demonstrates one operation. Notice how they build on each other—you create data, read it to verify, edit it to transform, extend it with new calculations, and fix potential errors. This is the natural flow of development.

---

## Key Takeaway

Every interaction with AI for coding is one of six operations: Create, Read, Edit, Run, Fix, or Extend. When you're confused about what to ask, identify which operation you need. When your prompt isn't working, make sure you're clearly performing one operation at a time. This vocabulary makes communication with AI precise and effective.

In Part 2, we'll develop the skills you need to perform these operations well—starting with how to break big problems into small pieces.

