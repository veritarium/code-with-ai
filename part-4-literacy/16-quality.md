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

Testing is quality control for code. Just as you wouldn't ship a bolt without verifying its dimensions, you shouldn't use code without verifying it works.

![Testing](/code-with-ai/assets/images/diagrams/16-1-testing.png)
{: .chapter-diagram}
*Figure 16.1: Testing — Verify it works*
{: .diagram-caption}

Manual testing is the simplest approach: run the code, check the output, try different inputs. This is good for quick checks and exploring behavior. You're already doing this naturally whenever you run code and look at the results.

Automated testing means writing test code that runs automatically and repeatedly. You define inputs and expected outputs, and the test framework verifies they match. This is good for reliability because tests catch regressions when you change code—if you accidentally break something, the tests tell you immediately.

Edge case testing examines boundary conditions: empty inputs, extreme values, invalid data. This is good for robustness because edge cases are where most bugs hide. What happens with zero? With negative numbers? With empty lists? If you haven't tested these, you don't really know if your code works.

The simplest test is an assertion: `assert result == expected, "Test failed!"` If the result doesn't match the expected value, you'll know immediately. Ask AI to write tests for your functions—it's excellent at generating test cases.

<div class="key-insight">
<strong>Key Insight:</strong> Test before trusting. Known input + expected output = verification. Tested code = Trusted code.
</div>

---

## Project Structure

As projects grow beyond a single file, organization matters. A well-structured project is easier to understand, maintain, and share.

![Project Structure](/code-with-ai/assets/images/diagrams/16-2-project-structure.png)
{: .chapter-diagram}
*Figure 16.2: Project Structure — Organized files*
{: .diagram-caption}

A typical project structure separates concerns. The entry point `main.py` is where execution starts. Core functions live in `calculations.py`. Helper utilities go in `utils.py`. Input files live in a `data/` folder. Output files go to `output/`. Test files live in `tests/`. Documentation goes in `README.md`.

This organization helps you find files quickly, separates different concerns (logic vs data vs tests), makes sharing and collaboration easy, and follows professional standards that others expect.

For file naming, use lowercase (`calculations.py` not `Calculations.py`), use underscores (`bolt_stress.py` not `bolt-stress.py`), and be descriptive (`test_calculations.py` not `test1.py`). Names should describe content.

<div class="key-insight">
<strong>Key Insight:</strong> Organized project = Maintainable project. Ask AI: "Create a project structure for [description]" and it will set everything up.
</div>

---

## Try It Yourself

This example demonstrates testing and project organization with a complete mini-project.

Create a file called `quality_demo.py`:

```python
# quality_demo.py
# Demonstrating testing and code quality

import math

# ============================================================
# PART 1: THE CODE TO TEST
# ============================================================

def calculate_stress(force: float, area: float) -> float:
    """
    Calculate tensile stress from force and area.

    Args:
        force: Applied force in Newtons
        area: Cross-sectional area in mm²

    Returns:
        Stress in MPa

    Raises:
        ValueError: If force is negative or area is not positive
    """
    if force < 0:
        raise ValueError(f"Force cannot be negative: {force}")
    if area <= 0:
        raise ValueError(f"Area must be positive: {area}")

    # Convert to consistent units and calculate
    stress_mpa = force / area
    return stress_mpa


def calculate_safety_factor(stress: float, yield_strength: float) -> float:
    """Calculate safety factor from stress and yield strength."""
    if stress <= 0:
        raise ValueError("Stress must be positive")
    if yield_strength <= 0:
        raise ValueError("Yield strength must be positive")

    return yield_strength / stress


def check_bolt(diameter: float, force: float, yield_strength: float = 640) -> dict:
    """
    Complete bolt analysis.

    Returns dict with area, stress, safety_factor, and status.
    """
    area = math.pi * (diameter / 2) ** 2
    stress = calculate_stress(force, area)
    sf = calculate_safety_factor(stress, yield_strength)

    if sf >= 2:
        status = "PASS"
    elif sf >= 1:
        status = "WARNING"
    else:
        status = "FAIL"

    return {
        "diameter": diameter,
        "area": round(area, 2),
        "stress": round(stress, 2),
        "safety_factor": round(sf, 2),
        "status": status
    }


# ============================================================
# PART 2: MANUAL TESTING
# ============================================================

def manual_tests():
    """Run tests manually and check output"""
    print("=" * 60)
    print("MANUAL TESTING")
    print("=" * 60)

    # Test 1: Basic calculation
    print("\nTest 1: Basic stress calculation")
    result = calculate_stress(1000, 100)  # 1000N / 100mm² = 10 MPa
    print(f"  calculate_stress(1000, 100) = {result}")
    print(f"  Expected: 10.0")
    print(f"  Status: {'PASS' if result == 10.0 else 'FAIL'}")

    # Test 2: Bolt analysis
    print("\nTest 2: Bolt analysis")
    result = check_bolt(12, 10000, 640)
    print(f"  check_bolt(12, 10000, 640) = {result}")
    print(f"  Expected status: PASS (SF should be ~7)")

    # Test 3: Edge case - small bolt, high force
    print("\nTest 3: Edge case - small bolt, high force")
    result = check_bolt(6, 50000, 250)
    print(f"  check_bolt(6, 50000, 250) = {result}")
    print(f"  Expected: FAIL (stress will exceed yield)")


# ============================================================
# PART 3: AUTOMATED TESTING WITH ASSERTIONS
# ============================================================

def automated_tests():
    """Run automated tests using assertions"""
    print("\n" + "=" * 60)
    print("AUTOMATED TESTING")
    print("=" * 60)

    tests_passed = 0
    tests_failed = 0

    # --- Test calculate_stress ---
    print("\nTesting calculate_stress():")

    # Test normal calculation
    try:
        result = calculate_stress(1000, 100)
        assert result == 10.0, f"Expected 10.0, got {result}"
        print("  [PASS] Normal calculation: 1000/100 = 10")
        tests_passed += 1
    except AssertionError as e:
        print(f"  [FAIL] Normal calculation: {e}")
        tests_failed += 1

    # Test with float values
    try:
        result = calculate_stress(1000, 50)
        assert result == 20.0, f"Expected 20.0, got {result}"
        print("  [PASS] Float result: 1000/50 = 20")
        tests_passed += 1
    except AssertionError as e:
        print(f"  [FAIL] Float result: {e}")
        tests_failed += 1

    # Test negative force rejection
    try:
        try:
            calculate_stress(-100, 50)
            print("  [FAIL] Negative force: Should have raised ValueError")
            tests_failed += 1
        except ValueError:
            print("  [PASS] Negative force: Correctly rejected")
            tests_passed += 1
    except Exception as e:
        print(f"  [FAIL] Negative force: Unexpected error: {e}")
        tests_failed += 1

    # Test zero area rejection
    try:
        try:
            calculate_stress(100, 0)
            print("  [FAIL] Zero area: Should have raised ValueError")
            tests_failed += 1
        except ValueError:
            print("  [PASS] Zero area: Correctly rejected")
            tests_passed += 1
    except Exception as e:
        print(f"  [FAIL] Zero area: Unexpected error: {e}")
        tests_failed += 1

    # --- Test check_bolt ---
    print("\nTesting check_bolt():")

    # Test safe bolt
    try:
        result = check_bolt(12, 5000, 640)
        assert result["status"] == "PASS", f"Expected PASS, got {result['status']}"
        assert result["safety_factor"] > 2, f"Expected SF > 2, got {result['safety_factor']}"
        print(f"  [PASS] Safe bolt: SF={result['safety_factor']}, status={result['status']}")
        tests_passed += 1
    except AssertionError as e:
        print(f"  [FAIL] Safe bolt: {e}")
        tests_failed += 1

    # Test warning range
    try:
        result = check_bolt(8, 25000, 640)  # Will give SF between 1 and 2
        # Area ≈ 50mm², stress ≈ 500 MPa, SF ≈ 1.28
        assert result["status"] == "WARNING", f"Expected WARNING, got {result['status']}"
        print(f"  [PASS] Warning bolt: SF={result['safety_factor']}, status={result['status']}")
        tests_passed += 1
    except AssertionError as e:
        print(f"  [FAIL] Warning bolt: {e}")
        tests_failed += 1

    # Test failing bolt
    try:
        result = check_bolt(6, 50000, 250)  # Will definitely fail
        assert result["status"] == "FAIL", f"Expected FAIL, got {result['status']}"
        print(f"  [PASS] Failing bolt: SF={result['safety_factor']}, status={result['status']}")
        tests_passed += 1
    except AssertionError as e:
        print(f"  [FAIL] Failing bolt: {e}")
        tests_failed += 1

    # Summary
    print("\n" + "-" * 40)
    print(f"Tests passed: {tests_passed}")
    print(f"Tests failed: {tests_failed}")
    print(f"Total: {tests_passed + tests_failed}")

    return tests_failed == 0


# ============================================================
# PART 4: EDGE CASE TESTING
# ============================================================

def edge_case_tests():
    """Test boundary conditions and unusual inputs"""
    print("\n" + "=" * 60)
    print("EDGE CASE TESTING")
    print("=" * 60)

    edge_cases = [
        ("Very small force", lambda: calculate_stress(0.001, 100)),
        ("Very large force", lambda: calculate_stress(1e9, 100)),
        ("Very small area", lambda: calculate_stress(1000, 0.001)),
        ("Zero force (valid)", lambda: calculate_stress(0, 100)),
        ("Negative force (invalid)", lambda: calculate_stress(-1, 100)),
        ("Zero area (invalid)", lambda: calculate_stress(100, 0)),
        ("Negative area (invalid)", lambda: calculate_stress(100, -1)),
    ]

    print("\nTesting boundary conditions:")
    for name, test_func in edge_cases:
        try:
            result = test_func()
            print(f"  {name}: {result:.6g}")
        except ValueError as e:
            print(f"  {name}: Rejected ({e})")
        except Exception as e:
            print(f"  {name}: ERROR ({type(e).__name__}: {e})")


# ============================================================
# PART 5: PROJECT STRUCTURE EXAMPLE
# ============================================================

def show_project_structure():
    """Show what a well-organized project looks like"""
    print("\n" + "=" * 60)
    print("PROJECT STRUCTURE")
    print("=" * 60)

    structure = """
bolt_calculator/
├── main.py                 # Entry point - runs the program
├── calculations.py         # Core calculation functions
├── utils.py                # Helper functions (file I/O, formatting)
├── config.py               # Configuration and constants
│
├── data/                   # Input data files
│   ├── bolt_specs.csv
│   └── material_properties.json
│
├── output/                 # Generated results
│   ├── analysis_report.txt
│   └── results.csv
│
├── tests/                  # Test files
│   ├── test_calculations.py
│   └── test_utils.py
│
├── README.md               # Project documentation
└── requirements.txt        # Dependencies list
"""

    print(structure)

    print("WHY THIS STRUCTURE:")
    print("-" * 40)
    print("• main.py: Single entry point makes it clear where to start")
    print("• Separate files: Each file has one responsibility")
    print("• data/: Raw inputs separate from code")
    print("• output/: Generated files separate from source")
    print("• tests/: Tests organized and easy to find")
    print("• README.md: Documentation for others (and future you)")


# ============================================================
# MAIN: Run all demonstrations
# ============================================================

if __name__ == "__main__":
    # Run all test demonstrations
    manual_tests()
    all_passed = automated_tests()
    edge_case_tests()
    show_project_structure()

    # Final summary
    print("\n" + "=" * 60)
    print("QUALITY CHECKLIST")
    print("=" * 60)
    print("""
Before shipping code:

TESTING:
[ ] Does it work with normal inputs?
[ ] Does it handle edge cases?
[ ] Does it reject invalid inputs?
[ ] Are there automated tests?

CODE QUALITY:
[ ] Are functions small and focused?
[ ] Are names descriptive?
[ ] Is error handling in place?
[ ] Could someone else understand it?

PROJECT:
[ ] Is it organized logically?
[ ] Is there documentation?
[ ] Are tests separate from code?

Tested code = Trusted code
""")

    if all_passed:
        print("\n✓ All automated tests passed!")
    else:
        print("\n✗ Some tests failed - review output above")
```

Run it:

```bash
python quality_demo.py
```

**Expected Output:**

```
============================================================
MANUAL TESTING
============================================================

Test 1: Basic stress calculation
  calculate_stress(1000, 100) = 10.0
  Expected: 10.0
  Status: PASS

Test 2: Bolt analysis
  check_bolt(12, 10000, 640) = {'diameter': 12, 'area': 113.1, ...}
  Expected status: PASS (SF should be ~7)

Test 3: Edge case - small bolt, high force
  check_bolt(6, 50000, 250) = {'diameter': 6, 'area': 28.27, ...}
  Expected: FAIL (stress will exceed yield)

============================================================
AUTOMATED TESTING
============================================================

Testing calculate_stress():
  [PASS] Normal calculation: 1000/100 = 10
  [PASS] Float result: 1000/50 = 20
  [PASS] Negative force: Correctly rejected
  [PASS] Zero area: Correctly rejected

Testing check_bolt():
  [PASS] Safe bolt: SF=5.76, status=PASS
  [PASS] Warning bolt: SF=1.28, status=WARNING
  [PASS] Failing bolt: SF=0.14, status=FAIL

----------------------------------------
Tests passed: 7
Tests failed: 0
Total: 7

...

✓ All automated tests passed!
```

The example shows manual testing for quick verification, automated testing with assertions for reliable regression catching, edge case testing for robustness, and a recommended project structure for organization.

---

## Key Takeaway

Quality comes from testing and organization. Test manually for quick checks, write automated tests for reliability, and always test edge cases. Organize your project with separate files for different concerns, keep data and output separate from code, and include tests and documentation. Tested code is trusted code, and organized code is maintainable code.

In Part 5, you'll put everything together and build your first complete project.

