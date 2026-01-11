---
layout: chapter
title: "Data and Files"
chapter: 15
part: 4
part_title: "Code Literacy"
part_url: "/part-4-literacy/"
prev: "/part-4-literacy/14-functions"
prev_title: "Functions and Libraries"
next: "/part-4-literacy/16-quality"
next_title: "Quality"
---

## Data Structures

Data structures are ways to organize multiple pieces of data. Choosing the right structure makes your code cleaner and faster.

![Data Structures](/code-with-ai/assets/images/diagrams/15-1-data-structures.png)
{: .chapter-diagram}
*Figure 15.1: Data Structures — Organizing data*
{: .diagram-caption}

A **LIST** is an ordered collection. When you write `bolt_sizes = [8, 10, 12, 16]`, you're creating a sequence where order matters. Access items by position: `bolt_sizes[0]` gives you `8` (positions start at 0). You can add items, remove items, and process them in order. Think of it like a shopping list.

A **DICTIONARY** stores key-value pairs. When you write `bolt = {"name": "M12", "grade": "8.8", "diameter": 12.0}`, you're creating named properties. Access items by name: `bolt["grade"]` gives you `"8.8"`. Think of it like a real dictionary where words map to definitions.

A **TUPLE** is a fixed, unchangeable list. When you write `coords = (100.0, 200.5, 50.2)`, you're creating a sequence that can never be modified after creation. Good for coordinates, constants, and data that should never change. Think of it like a sealed envelope.

Use a list when you have a collection of similar items and need to add or remove. Use a dictionary when you have named properties and need to look up by name. Use a tuple when you have a fixed group of values that should never change.

<div class="key-insight">
<strong>Key Insight:</strong> Right structure = Cleaner, faster code. Ask AI: "What data structure should I use for [description]?"
</div>

---

## Files and I/O

Files are permanent storage. When your program ends, variables disappear, but files persist. This is how you save results and load data.

![Files and I/O](/code-with-ai/assets/images/diagrams/15-2-files-io.png)
{: .chapter-diagram}
*Figure 15.2: Files and I/O — Permanent storage*
{: .diagram-caption}

To read a file, you open it and load its contents into memory: `with open("data.csv") as file: content = file.read()`. The data flows from disk into your program where you can process it.

To write a file, you open it for writing and send data to it: `with open("results.txt", "w") as file: file.write("Stress: 250 MPa")`. The data flows from your program to disk where it persists after the program ends.

Common file types fall into two categories. Text files are human-readable: `.txt` for plain text, `.csv` for spreadsheet data, `.json` for structured data. Data files require libraries to read: `.xlsx` for Excel files, `.xml` for structured format, `.db` for databases.

<div class="key-insight">
<strong>Key Insight:</strong> Files = Permanent data that survives program restarts. AI handles the file reading/writing details—you describe what you need.
</div>

---

## Try It Yourself

This example demonstrates data structures and file operations with practical engineering data.

Create a file called `data_files.py`:

```python
# data_files.py
# Demonstrating data structures and file operations

import os
import json
import csv

# ============================================================
# PART 1: DATA STRUCTURES
# ============================================================

print("=" * 60)
print("DATA STRUCTURES")
print("=" * 60)

# --- LISTS: Ordered collections ---
print("\nLISTS: Ordered collections")
print("-" * 40)

bolt_sizes = [6, 8, 10, 12, 16, 20]
print(f"Available sizes: {bolt_sizes}")
print(f"First size: {bolt_sizes[0]}")      # Access by index
print(f"Last size: {bolt_sizes[-1]}")       # Negative index = from end

# Add and remove
bolt_sizes.append(24)                       # Add to end
print(f"After adding 24: {bolt_sizes}")

bolt_sizes.remove(6)                        # Remove specific value
print(f"After removing 6: {bolt_sizes}")

# Process with loop
print("Processing each size:")
for size in bolt_sizes:
    area = 3.14159 * (size/2)**2
    print(f"  M{size}: area = {area:.1f} mm²")

# --- DICTIONARIES: Key-value pairs ---
print("\nDICTIONARIES: Key-value pairs")
print("-" * 40)

bolt = {
    "name": "M12x1.75",
    "diameter": 12.0,
    "pitch": 1.75,
    "grade": "8.8",
    "yield_strength": 640,
    "is_metric": True
}

print(f"Bolt: {bolt['name']}")
print(f"Diameter: {bolt['diameter']} mm")
print(f"Grade: {bolt['grade']}")
print(f"Yield strength: {bolt['yield_strength']} MPa")

# Add new properties
bolt["supplier"] = "FastenerCo"
bolt["cost"] = 0.45

# Check if key exists
if "coating" in bolt:
    print(f"Coating: {bolt['coating']}")
else:
    print("No coating specified")

# Iterate over dictionary
print("\nAll properties:")
for key, value in bolt.items():
    print(f"  {key}: {value}")

# --- TUPLES: Fixed sequences ---
print("\nTUPLES: Fixed sequences")
print("-" * 40)

# Coordinates that shouldn't change
mounting_point = (100.0, 250.5, 75.0)
print(f"Mounting point (x, y, z): {mounting_point}")

# Unpack into variables
x, y, z = mounting_point
print(f"X = {x}, Y = {y}, Z = {z}")

# Multiple return values (common use)
def get_bolt_specs(diameter):
    """Return tuple of specs for a bolt diameter"""
    pitch = diameter * 0.15  # Approximate
    head_size = diameter * 1.5
    return (diameter, pitch, head_size)

d, p, h = get_bolt_specs(12)
print(f"M12 specs: diameter={d}, pitch={p:.2f}, head={h}")

# --- LIST OF DICTIONARIES: Common pattern ---
print("\nLIST OF DICTIONARIES: Common pattern")
print("-" * 40)

bolt_inventory = [
    {"size": "M8", "qty": 100, "location": "Bin A1"},
    {"size": "M10", "qty": 75, "location": "Bin A2"},
    {"size": "M12", "qty": 50, "location": "Bin A3"},
    {"size": "M16", "qty": 25, "location": "Bin B1"},
]

print("Inventory:")
total = 0
for item in bolt_inventory:
    print(f"  {item['size']}: {item['qty']} pcs in {item['location']}")
    total += item["qty"]
print(f"Total bolts: {total}")


# ============================================================
# PART 2: FILE OPERATIONS
# ============================================================

print("\n" + "=" * 60)
print("FILE OPERATIONS")
print("=" * 60)

# --- Writing and reading text files ---
print("\nTEXT FILES")
print("-" * 40)

# Write a simple text file
report_content = """BOLT ANALYSIS REPORT
=====================
Date: 2024-01-15
Analyst: Engineering Team

Results:
- All bolts within tolerance
- Maximum stress: 185 MPa
- Safety factor: 3.5

Status: APPROVED
"""

with open("analysis_report.txt", "w") as file:
    file.write(report_content)
print("Created: analysis_report.txt")

# Read it back
with open("analysis_report.txt", "r") as file:
    content = file.read()
print(f"File contents:\n{content}")

# --- CSV files (spreadsheet format) ---
print("\nCSV FILES")
print("-" * 40)

# Write CSV data
csv_data = [
    ["bolt_id", "diameter", "force", "stress", "status"],
    ["B001", 12, 10000, 88.4, "PASS"],
    ["B002", 10, 8000, 101.9, "PASS"],
    ["B003", 8, 12000, 238.7, "FAIL"],
    ["B004", 16, 20000, 99.5, "PASS"],
]

with open("bolt_data.csv", "w", newline="") as file:
    writer = csv.writer(file)
    writer.writerows(csv_data)
print("Created: bolt_data.csv")

# Read CSV data
with open("bolt_data.csv", "r") as file:
    reader = csv.reader(file)
    print("\nCSV contents:")
    for row in reader:
        print(f"  {row}")

# Read CSV as dictionaries (easier to use)
with open("bolt_data.csv", "r") as file:
    reader = csv.DictReader(file)
    print("\nAs dictionaries:")
    for row in reader:
        print(f"  {row['bolt_id']}: {row['stress']} MPa - {row['status']}")

# --- JSON files (structured data) ---
print("\nJSON FILES")
print("-" * 40)

# Complex structured data
project_data = {
    "project_name": "Bridge Assembly",
    "date": "2024-01-15",
    "engineer": "J. Smith",
    "bolts": [
        {"id": "B001", "type": "M12", "torque": 85},
        {"id": "B002", "type": "M16", "torque": 190},
        {"id": "B003", "type": "M20", "torque": 380}
    ],
    "specifications": {
        "standard": "ISO 898-1",
        "grade": "8.8",
        "coating": "Zinc"
    },
    "approved": True
}

# Write JSON
with open("project_data.json", "w") as file:
    json.dump(project_data, file, indent=2)
print("Created: project_data.json")

# Read JSON
with open("project_data.json", "r") as file:
    loaded_data = json.load(file)

print(f"Project: {loaded_data['project_name']}")
print(f"Standard: {loaded_data['specifications']['standard']}")
print("Bolts:")
for bolt in loaded_data["bolts"]:
    print(f"  {bolt['id']}: {bolt['type']} @ {bolt['torque']} Nm")


# ============================================================
# PART 3: PRACTICAL EXAMPLE
# ============================================================

print("\n" + "=" * 60)
print("PRACTICAL: Load, Process, Save")
print("=" * 60)

# Load data from CSV
def load_bolt_data(filename):
    """Load bolt data from CSV file"""
    bolts = []
    with open(filename, "r") as file:
        reader = csv.DictReader(file)
        for row in reader:
            bolts.append({
                "id": row["bolt_id"],
                "diameter": float(row["diameter"]),
                "force": float(row["force"]),
                "stress": float(row["stress"]),
                "status": row["status"]
            })
    return bolts

# Process data
def analyze_bolts(bolts):
    """Analyze bolt data and return summary"""
    stresses = [b["stress"] for b in bolts]
    passed = sum(1 for b in bolts if b["status"] == "PASS")

    return {
        "total_count": len(bolts),
        "passed": passed,
        "failed": len(bolts) - passed,
        "avg_stress": sum(stresses) / len(stresses),
        "max_stress": max(stresses),
        "min_stress": min(stresses)
    }

# Save results
def save_summary(summary, filename):
    """Save analysis summary to JSON"""
    with open(filename, "w") as file:
        json.dump(summary, file, indent=2)

# Run the workflow
bolts = load_bolt_data("bolt_data.csv")
summary = analyze_bolts(bolts)
save_summary(summary, "analysis_summary.json")

print(f"\nLoaded {summary['total_count']} bolts from CSV")
print(f"Passed: {summary['passed']}, Failed: {summary['failed']}")
print(f"Average stress: {summary['avg_stress']:.1f} MPa")
print(f"Saved summary to analysis_summary.json")


# Clean up demo files
print("\n" + "-" * 40)
print("Cleaning up demo files...")
for f in ["analysis_report.txt", "bolt_data.csv", "project_data.json", "analysis_summary.json"]:
    if os.path.exists(f):
        os.remove(f)
        print(f"  Removed {f}")

print("\n" + "=" * 60)
print("SUMMARY")
print("=" * 60)
print("""
DATA STRUCTURES:
  - LIST: Ordered collection [1, 2, 3]
  - DICT: Key-value pairs {"name": "M12"}
  - TUPLE: Fixed sequence (x, y, z)

FILE FORMATS:
  - .txt: Plain text
  - .csv: Spreadsheet data
  - .json: Structured data

WORKFLOW: Load from file -> Process -> Save results
""")
```

Run it:

```bash
python data_files.py
```

**Expected Output:**

```
============================================================
DATA STRUCTURES
============================================================

LISTS: Ordered collections
----------------------------------------
Available sizes: [6, 8, 10, 12, 16, 20]
First size: 6
Last size: 20
After adding 24: [6, 8, 10, 12, 16, 20, 24]
After removing 6: [8, 10, 12, 16, 20, 24]
Processing each size:
  M8: area = 50.3 mm²
  M10: area = 78.5 mm²
...

============================================================
FILE OPERATIONS
============================================================

TEXT FILES
----------------------------------------
Created: analysis_report.txt
File contents:
BOLT ANALYSIS REPORT
=====================
...

CSV FILES
----------------------------------------
Created: bolt_data.csv

CSV contents:
  ['bolt_id', 'diameter', 'force', 'stress', 'status']
  ['B001', '12', '10000', '88.4', 'PASS']
...
```

The example shows all three main data structures, demonstrates reading and writing text, CSV, and JSON files, and combines them in a practical load-process-save workflow.

---

## Key Takeaway

Data structures organize your data: lists for ordered collections, dictionaries for named properties, tuples for fixed values. Files make data permanent: text files for simple content, CSV for tabular data, JSON for structured data. The typical workflow is load data from files, process it with your code, and save results back to files. AI handles the syntax details—you focus on what data you need and how to organize it.

In the next chapter, we'll cover quality—how to test your code and organize your projects.

