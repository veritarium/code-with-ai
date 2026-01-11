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

Ways to organize multiple pieces of data.

![Data Structures](/code-with-ai/assets/images/diagrams/15-1-data-structures.png)
{: .chapter-diagram}
*Figure 15.1: Data Structures — Organizing data*
{: .diagram-caption}

**LIST** — Ordered collection
```python
bolt_sizes = [8, 10, 12, 16]
```
Access by position: `bolt_sizes[0]` gives you `8`.
Can add/remove items. Like a shopping list.

**DICTIONARY** — Key-value pairs
```python
bolt = {"name": "M12", "grade": "8.8", "diameter": 12.0}
```
Access by name: `bolt["grade"]` gives you `"8.8"`.
Like a real dictionary: word → definition.

**TUPLE** — Fixed, unchangeable list
```python
coords = (100.0, 200.5, 50.2)
```
Can't change after creation. Good for coordinates, constants.
Like a sealed envelope.

### When to Use What

| Structure | Use When |
|-----------|----------|
| LIST | Collection of similar items, need to add/remove |
| DICTIONARY | Named properties, need to look up by name |
| TUPLE | Fixed group of values, should never change |

**Ask AI:** "What data structure should I use for [description]?"

<div class="key-insight">
<strong>Key Insight:</strong> Right structure = Cleaner, faster code.
</div>

---

## Files and I/O

Files are permanent storage. Data survives when the program ends.

![Files and I/O](/code-with-ai/assets/images/diagrams/15-2-files-io.png)
{: .chapter-diagram}
*Figure 15.2: Files and I/O — Permanent storage*
{: .diagram-caption}

### Reading Files

```python
with open("data.csv") as file:
    content = file.read()
```

File on disk → Your program → Data in memory

### Writing Files

```python
with open("results.txt", "w") as file:
    file.write("Stress: 250 MPa")
```

Your program → File on disk → Permanent storage

### Common File Types

**Text files** (human readable)
- `.txt` — Plain text
- `.csv` — Spreadsheet data
- `.json` — Structured data

**Data files** (use libraries to read)
- `.xlsx` — Excel files
- `.xml` — Structured format
- `.db` — Databases

### Ask AI

- "Read this CSV file into a list"
- "Write results to a new file"
- "Parse this JSON data"

AI handles the details. You describe what you need.

<div class="key-insight">
<strong>Key Insight:</strong> Files = Permanent data that survives restarts.
</div>
