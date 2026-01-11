---
layout: chapter
title: "Quality"
chapter: 16
part: 4
part_title: "Code Literacy"
part_url: "/part-4-literacy/"
prev: "/part-4-literacy/15-data"
prev_title: "Data and Files"
next: "/part-5-building/17-first-project"
next_title: "Your First Project"
---

## Testing

Testing is quality control for code. You verify it actually works.

![Testing](/code-with-ai/assets/images/diagrams/16-1-testing.png)
{: .chapter-diagram}
*Figure 16.1: Testing — Verify it works*
{: .diagram-caption}

### Types of Testing

**Manual Testing**
- Run the code
- Check the output
- Try different inputs

Good for quick checks.

**Automated Testing**
- Write test code
- Runs automatically
- Catches regressions

Good for reliability.

**Edge Case Testing**
- Empty inputs
- Extreme values
- Invalid data

Good for robustness.

### Simple Test Example

```python
result = calculate_stress(1000, 4)
expected = 250
assert result == expected, "Test failed!"
```

If result doesn't match expected, you'll know immediately.

### Test Results

- **PASS** — Code works!
- **FAIL** — Fix needed.

**Ask AI:** "Write tests for this function"

<div class="key-insight">
<strong>Key Insight:</strong> Test before trusting. Known input + expected output = verification. Tested code = Trusted code.
</div>

---

## Project Structure

Organizing files for bigger projects. Like a well-organized toolbox.

![Project Structure](/code-with-ai/assets/images/diagrams/16-2-project-structure.png)
{: .chapter-diagram}
*Figure 16.2: Project Structure — Organized files*
{: .diagram-caption}

### Typical Project Structure

```
bolt_calculator/
    main.py              # Entry point
    calculations.py      # Core functions
    utils.py             # Helper functions
    data/                # Input files
        bolt_specs.csv
        materials.json
    output/              # Results
        results.txt
    tests/               # Test files
        test_calculations.py
    README.md            # Documentation
```

### Why Organize?

- Find files quickly
- Separate concerns (logic vs data vs tests)
- Easy to share and collaborate
- Professional standard

### File Naming Rules

- Lowercase: `calculations.py` not `Calculations.py`
- Underscores: `bolt_stress.py` not `bolt-stress.py`
- Descriptive: `test_calculations.py` not `test1.py`

Names should describe content.

**Ask AI:** "Create a project structure for [description]" — it will set everything up.

<div class="key-insight">
<strong>Key Insight:</strong> Organized project = Maintainable project.
</div>
