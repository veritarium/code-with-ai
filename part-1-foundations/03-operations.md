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

Everything you'll ever do with AI coding falls into six categories. Just six. Once you recognize them, you'll never be confused about what to ask for again.

![Six Operations](/code-with-ai/assets/images/diagrams/03-1-six-operations.png)
{: .chapter-diagram}
*Figure 3.1: The Six Operations — Everything you can do with AI*
{: .diagram-caption}

The first operation is creating something new. This is where most projects begin. You describe what you need—a function that calculates beam deflection, a script that converts file formats, a tool that processes data—and AI generates code that didn't exist before. Creation is exciting but also where beginners often struggle, because you're starting from nothing and the possibilities feel endless.

The second operation is reading and understanding existing code. Maybe you inherited code from a colleague, or you're revisiting something you wrote six months ago and can't remember how it works. AI excels at explanation. Paste in a function and ask what it does. Point to a confusing line and ask why it's there. Reading code is a skill that even experienced programmers need help with, and AI has infinite patience for explaining.

The third operation is editing—taking code that already works and modifying it. You might need to change units from imperial to metric, adjust output formats, or modify how the code handles certain inputs. Editing is often safer than creating from scratch because you're building on a foundation that already works. You know the basic structure is sound; you're just adjusting details.

The fourth operation is running the code, and this is the only one AI cannot do for you. You have to execute the code yourself and observe what happens. This is your reality check. Code that looks perfect might fail in practice. Functions that seem complete might produce wrong answers. Running code connects the abstract world of instructions to the concrete world of results. Never skip this step.

The fifth operation is fixing errors. When code fails—and it will—you enter debugging mode. The best approach is direct: paste the error message exactly as it appears, include the relevant code, and ask AI to fix it. Error messages often look intimidating but usually point directly to the problem. The more context you provide about what you expected versus what happened, the faster AI can diagnose the issue.

The sixth operation is extending functionality. Your basic code works, but now you want it to do more. Perhaps your calculator should also save results to a file, or your data processor should handle a new file format, or your analysis tool should generate charts. Extension means adding capabilities incrementally, building on proven foundations rather than starting over.

When you're stuck and don't know what to ask, identify which operation you need. When your prompt isn't getting good results, check whether you're clearly doing one operation at a time. This vocabulary—create, read, edit, run, fix, extend—makes communication with AI precise and effective.

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

