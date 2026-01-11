---
layout: chapter
title: "Your First Project"
chapter: 17
part: 5
part_title: "Building"
part_url: "/part-5-building/"
prev: "/part-4-literacy/16-quality"
prev_title: "Quality"
next: "/part-5-building/18-forward"
next_title: "Moving Forward"
---

Everything you've learned comes together now. You understand the loop, you know how to decompose problems, you can communicate precisely with AI, and you can read and verify code. Time to build something real.

## The Three Phases

Every successful project follows three phases: plan, build, and refine. This isn't bureaucracy—it's how working software gets made.

![Your First Project](/code-with-ai/assets/images/diagrams/17-1-your-first-project.png)
{: .chapter-diagram}
*Figure 17.1: Your First Project — The approach*
{: .diagram-caption}

Planning means defining your goal before touching the keyboard. What should the program do? What goes in, what comes out? What's the simplest version that would still be useful? Write it in one sentence. If you can't describe it simply, you don't understand it yet.

Building means working with AI to create each piece. Start with the core feature. Get it working. Test it. Then add the next feature. One piece at a time, one working step at a time. Get it working before making it perfect. Perfection is the enemy of done.

Refining means polishing what you've built. Handle edge cases. Add helpful error messages. Clean up the code so others can understand it. Ask AI to review your code and suggest improvements. This is where good becomes great.

<div class="key-insight">
<strong>Key Insight:</strong> Done is better than perfect. Ship version 1, then improve it based on real usage.
</div>

---

## Project Checklist

Before calling a project complete, run through this mental checklist. It catches the issues that trip up beginners.

![Project Checklist](/code-with-ai/assets/images/diagrams/17-2-project-checklist.png)
{: .chapter-diagram}
*Figure 17.2: Project Checklist — Before you ship*
{: .diagram-caption}

Before starting, verify your goal is clearly defined, you've identified inputs and outputs, and you've broken the work into small testable tasks. If any of these are fuzzy, clarify them first—time spent planning saves time debugging.

While building, make sure you're testing each piece as you go, understanding the code AI generates rather than blindly trusting it, and saving working versions so you can roll back if something breaks.

Before finishing, confirm it works with normal inputs, handles edge cases gracefully, and provides clear error messages when things go wrong.

For quality, check that the code is readable, names are descriptive, and comments explain the non-obvious parts. Code you can't understand tomorrow isn't really done today.

The ultimate test: Can someone else use this without your help? Would you trust this code to run on important data? If yes to both, you're ready to ship.

<div class="key-insight">
<strong>Key Insight:</strong> A checklist catches what excitement misses. Use it every time.
</div>

---

## Try It Yourself

This is a complete project that brings together everything from this tutorial. It's an engineering calculator that analyzes bolts, generates reports, and saves results to files.

Create a file called `bolt_project.py`:

```python
# bolt_project.py
# A complete mini-project: Engineering Bolt Calculator
# This combines everything: functions, files, testing, user input

import math
import json
import os
from datetime import datetime

# ============================================================
# PART 1: CORE CALCULATION FUNCTIONS
# ============================================================

def calculate_area(diameter: float) -> float:
    """Calculate cross-sectional area from diameter (mm²)"""
    if diameter <= 0:
        raise ValueError(f"Diameter must be positive: {diameter}")
    return math.pi * (diameter / 2) ** 2


def calculate_stress(force: float, area: float) -> float:
    """Calculate stress from force (N) and area (mm²) -> MPa"""
    if force < 0:
        raise ValueError(f"Force cannot be negative: {force}")
    if area <= 0:
        raise ValueError(f"Area must be positive: {area}")
    return force / area


def calculate_safety_factor(stress: float, yield_strength: float) -> float:
    """Calculate safety factor from stress and yield strength"""
    if stress <= 0:
        raise ValueError("Stress must be positive")
    if yield_strength <= 0:
        raise ValueError("Yield strength must be positive")
    return yield_strength / stress


def get_status(safety_factor: float) -> str:
    """Determine pass/fail status based on safety factor"""
    if safety_factor >= 2.0:
        return "PASS"
    elif safety_factor >= 1.5:
        return "WARNING"
    elif safety_factor >= 1.0:
        return "MARGINAL"
    else:
        return "FAIL"


# ============================================================
# PART 2: BOLT ANALYSIS
# ============================================================

def analyze_bolt(name: str, diameter: float, force: float,
                 yield_strength: float = 640) -> dict:
    """
    Complete analysis of a single bolt.

    Args:
        name: Identifier for the bolt
        diameter: Bolt diameter in mm
        force: Applied force in N
        yield_strength: Material yield strength in MPa (default: Grade 8.8)

    Returns:
        Dictionary with all analysis results
    """
    area = calculate_area(diameter)
    stress = calculate_stress(force, area)
    sf = calculate_safety_factor(stress, yield_strength)
    status = get_status(sf)

    return {
        "name": name,
        "diameter_mm": diameter,
        "force_N": force,
        "area_mm2": round(area, 2),
        "stress_MPa": round(stress, 2),
        "yield_strength_MPa": yield_strength,
        "safety_factor": round(sf, 2),
        "status": status
    }


def analyze_batch(bolts: list, yield_strength: float = 640) -> list:
    """Analyze multiple bolts and return list of results"""
    results = []
    for bolt in bolts:
        try:
            result = analyze_bolt(
                bolt["name"],
                bolt["diameter"],
                bolt["force"],
                yield_strength
            )
            results.append(result)
        except (ValueError, KeyError) as e:
            results.append({
                "name": bolt.get("name", "Unknown"),
                "error": str(e),
                "status": "ERROR"
            })
    return results


# ============================================================
# PART 3: REPORT GENERATION
# ============================================================

def generate_report(results: list, title: str = "Bolt Analysis Report") -> str:
    """Generate a formatted text report from analysis results"""
    lines = []

    # Header
    lines.append("=" * 60)
    lines.append(title.upper())
    lines.append(f"Generated: {datetime.now().strftime('%Y-%m-%d %H:%M:%S')}")
    lines.append("=" * 60)

    # Individual results
    lines.append("\nINDIVIDUAL RESULTS:")
    lines.append("-" * 60)

    for r in results:
        if "error" in r:
            lines.append(f"\n[ERROR] {r['name']}: {r['error']}")
        else:
            icon = "OK" if r["status"] == "PASS" else "!!"
            lines.append(f"\n[{icon}] {r['name']}")
            lines.append(f"    Diameter: {r['diameter_mm']} mm")
            lines.append(f"    Force: {r['force_N']} N")
            lines.append(f"    Stress: {r['stress_MPa']} MPa")
            lines.append(f"    Safety Factor: {r['safety_factor']}")
            lines.append(f"    Status: {r['status']}")

    # Summary statistics
    valid_results = [r for r in results if "error" not in r]
    if valid_results:
        stresses = [r["stress_MPa"] for r in valid_results]
        safety_factors = [r["safety_factor"] for r in valid_results]

        passed = sum(1 for r in valid_results if r["status"] == "PASS")
        warnings = sum(1 for r in valid_results if r["status"] == "WARNING")
        marginal = sum(1 for r in valid_results if r["status"] == "MARGINAL")
        failed = sum(1 for r in valid_results if r["status"] == "FAIL")

        lines.append("\n" + "-" * 60)
        lines.append("SUMMARY:")
        lines.append(f"    Total analyzed: {len(valid_results)}")
        lines.append(f"    Passed (SF >= 2.0): {passed}")
        lines.append(f"    Warning (SF 1.5-2.0): {warnings}")
        lines.append(f"    Marginal (SF 1.0-1.5): {marginal}")
        lines.append(f"    Failed (SF < 1.0): {failed}")
        lines.append(f"    Average stress: {sum(stresses)/len(stresses):.2f} MPa")
        lines.append(f"    Max stress: {max(stresses):.2f} MPa")
        lines.append(f"    Min safety factor: {min(safety_factors):.2f}")

    if len(results) != len(valid_results):
        lines.append(f"    Errors: {len(results) - len(valid_results)}")

    lines.append("\n" + "=" * 60)

    return "\n".join(lines)


# ============================================================
# PART 4: FILE OPERATIONS
# ============================================================

def save_report(report: str, filename: str) -> str:
    """Save report to text file"""
    with open(filename, "w") as f:
        f.write(report)
    return filename


def save_results_json(results: list, filename: str) -> str:
    """Save results to JSON file for further processing"""
    output = {
        "generated": datetime.now().isoformat(),
        "results": results
    }
    with open(filename, "w") as f:
        json.dump(output, f, indent=2)
    return filename


def load_bolts_from_json(filename: str) -> list:
    """Load bolt data from JSON file"""
    with open(filename, "r") as f:
        data = json.load(f)
    return data.get("bolts", data)  # Handle both formats


# ============================================================
# PART 5: INTERACTIVE INTERFACE
# ============================================================

def get_user_bolt() -> dict:
    """Get bolt data from user input"""
    print("\n--- Enter Bolt Data ---")
    name = input("Bolt name/ID: ").strip() or "Unnamed"

    while True:
        try:
            diameter = float(input("Diameter (mm): "))
            if diameter <= 0:
                print("Diameter must be positive. Try again.")
                continue
            break
        except ValueError:
            print("Please enter a valid number.")

    while True:
        try:
            force = float(input("Applied force (N): "))
            if force < 0:
                print("Force cannot be negative. Try again.")
                continue
            break
        except ValueError:
            print("Please enter a valid number.")

    return {"name": name, "diameter": diameter, "force": force}


def run_interactive():
    """Run interactive mode - analyze bolts one at a time"""
    print("\n" + "=" * 60)
    print("BOLT STRESS CALCULATOR - Interactive Mode")
    print("=" * 60)

    # Get yield strength
    print("\nDefault yield strength: 640 MPa (Grade 8.8 Steel)")
    custom = input("Press Enter to use default, or enter custom value: ").strip()
    yield_strength = float(custom) if custom else 640

    results = []

    while True:
        bolt = get_user_bolt()
        result = analyze_bolt(bolt["name"], bolt["diameter"],
                            bolt["force"], yield_strength)
        results.append(result)

        # Show immediate result
        print(f"\n>>> {result['name']}: {result['stress_MPa']} MPa, "
              f"SF={result['safety_factor']}, {result['status']}")

        another = input("\nAnalyze another bolt? (y/n): ").strip().lower()
        if another != 'y':
            break

    return results


# ============================================================
# PART 6: DEMONSTRATION
# ============================================================

def run_demo():
    """Demonstrate all features with sample data"""
    print("=" * 60)
    print("BOLT STRESS CALCULATOR - Demo Mode")
    print("=" * 60)

    # Sample bolt data
    sample_bolts = [
        {"name": "Main Beam A1", "diameter": 16, "force": 25000},
        {"name": "Main Beam A2", "diameter": 16, "force": 28000},
        {"name": "Cross Brace B1", "diameter": 12, "force": 15000},
        {"name": "Cross Brace B2", "diameter": 12, "force": 18000},
        {"name": "Support C1", "diameter": 10, "force": 8000},
        {"name": "Support C2", "diameter": 8, "force": 12000},  # Will be stressed
        {"name": "Anchor D1", "diameter": 20, "force": 40000},
    ]

    # Analyze all bolts
    print("\nAnalyzing bolt assembly...")
    results = analyze_batch(sample_bolts, yield_strength=640)

    # Generate and display report
    report = generate_report(results, "Bridge Assembly Analysis")
    print("\n" + report)

    # Save files
    save_report(report, "bolt_report.txt")
    save_results_json(results, "bolt_results.json")

    print("\nFiles saved:")
    print("  - bolt_report.txt (human-readable report)")
    print("  - bolt_results.json (data for further processing)")

    return results


# ============================================================
# PART 7: TESTS
# ============================================================

def run_tests():
    """Verify all calculations are correct"""
    print("\n" + "=" * 60)
    print("RUNNING TESTS")
    print("=" * 60)

    tests_passed = 0
    tests_failed = 0

    # Test area calculation
    try:
        area = calculate_area(10)
        expected = math.pi * 25  # pi * 5^2
        assert abs(area - expected) < 0.01, f"Expected {expected}, got {area}"
        print("[PASS] Area calculation")
        tests_passed += 1
    except AssertionError as e:
        print(f"[FAIL] Area calculation: {e}")
        tests_failed += 1

    # Test stress calculation
    try:
        stress = calculate_stress(1000, 100)
        assert stress == 10.0, f"Expected 10.0, got {stress}"
        print("[PASS] Stress calculation")
        tests_passed += 1
    except AssertionError as e:
        print(f"[FAIL] Stress calculation: {e}")
        tests_failed += 1

    # Test safety factor
    try:
        sf = calculate_safety_factor(100, 250)
        assert sf == 2.5, f"Expected 2.5, got {sf}"
        print("[PASS] Safety factor calculation")
        tests_passed += 1
    except AssertionError as e:
        print(f"[FAIL] Safety factor calculation: {e}")
        tests_failed += 1

    # Test status thresholds
    try:
        assert get_status(2.5) == "PASS"
        assert get_status(1.8) == "WARNING"
        assert get_status(1.2) == "MARGINAL"
        assert get_status(0.8) == "FAIL"
        print("[PASS] Status thresholds")
        tests_passed += 1
    except AssertionError as e:
        print(f"[FAIL] Status thresholds: {e}")
        tests_failed += 1

    # Test error handling
    try:
        try:
            calculate_area(-5)
            print("[FAIL] Should reject negative diameter")
            tests_failed += 1
        except ValueError:
            print("[PASS] Rejects negative diameter")
            tests_passed += 1
    except Exception as e:
        print(f"[FAIL] Error handling: {e}")
        tests_failed += 1

    # Test full analysis
    try:
        result = analyze_bolt("Test", 12, 10000, 640)
        assert result["status"] in ["PASS", "WARNING", "MARGINAL", "FAIL"]
        assert result["stress_MPa"] > 0
        assert result["safety_factor"] > 0
        print("[PASS] Full bolt analysis")
        tests_passed += 1
    except (AssertionError, KeyError) as e:
        print(f"[FAIL] Full analysis: {e}")
        tests_failed += 1

    print("-" * 40)
    print(f"Tests passed: {tests_passed}")
    print(f"Tests failed: {tests_failed}")

    return tests_failed == 0


# ============================================================
# MAIN ENTRY POINT
# ============================================================

if __name__ == "__main__":
    print("\n" + "=" * 60)
    print("BOLT STRESS CALCULATOR")
    print("A Complete Engineering Mini-Project")
    print("=" * 60)

    print("\nChoose mode:")
    print("  1. Demo (analyze sample data)")
    print("  2. Interactive (enter your own bolts)")
    print("  3. Run tests")

    choice = input("\nEnter choice (1/2/3): ").strip()

    if choice == "1":
        results = run_demo()
    elif choice == "2":
        results = run_interactive()
        if results:
            report = generate_report(results)
            print("\n" + report)

            save = input("\nSave report to file? (y/n): ").strip().lower()
            if save == 'y':
                save_report(report, "my_bolt_analysis.txt")
                save_results_json(results, "my_bolt_results.json")
                print("Files saved!")
    elif choice == "3":
        all_passed = run_tests()
        if all_passed:
            print("\nAll tests passed!")
        else:
            print("\nSome tests failed - review output above")
    else:
        print("Running demo by default...")
        results = run_demo()

    # Cleanup demo files
    print("\n" + "-" * 40)
    cleanup = input("Clean up generated files? (y/n): ").strip().lower()
    if cleanup == 'y':
        for f in ["bolt_report.txt", "bolt_results.json",
                  "my_bolt_analysis.txt", "my_bolt_results.json"]:
            if os.path.exists(f):
                os.remove(f)
                print(f"  Removed {f}")

    print("\n" + "=" * 60)
    print("PROJECT COMPLETE")
    print("=" * 60)
    print("""
This project demonstrates:

FUNCTIONS: Small, focused, reusable pieces
  - calculate_area(), calculate_stress(), etc.

DATA STRUCTURES: Organized information
  - Dictionaries for bolt data and results
  - Lists for batch processing

FILES: Permanent storage
  - JSON for data, TXT for reports

TESTING: Verified correctness
  - Automated tests for all calculations

ERROR HANDLING: Graceful failures
  - Validates inputs, catches exceptions

USER INTERFACE: Interactive and batch modes
  - Choose how to use it

You built this. You can build anything.
""")
```

Run it:

```bash
python bolt_project.py
```

**Expected Output (Demo Mode):**

```
============================================================
BOLT STRESS CALCULATOR
A Complete Engineering Mini-Project
============================================================

Choose mode:
  1. Demo (analyze sample data)
  2. Interactive (enter your own bolts)
  3. Run tests

Enter choice (1/2/3): 1
============================================================
BOLT STRESS CALCULATOR - Demo Mode
============================================================

Analyzing bolt assembly...

============================================================
BRIDGE ASSEMBLY ANALYSIS
Generated: 2024-01-15 14:30:00
============================================================

INDIVIDUAL RESULTS:
------------------------------------------------------------

[OK] Main Beam A1
    Diameter: 16 mm
    Force: 25000 N
    Stress: 124.34 MPa
    Safety Factor: 5.15
    Status: PASS

[OK] Main Beam A2
    Diameter: 16 mm
    Force: 28000 N
    Stress: 139.26 MPa
    Safety Factor: 4.6
    Status: PASS

...

------------------------------------------------------------
SUMMARY:
    Total analyzed: 7
    Passed (SF >= 2.0): 6
    Warning (SF 1.5-2.0): 1
    Marginal (SF 1.0-1.5): 0
    Failed (SF < 1.0): 0
    Average stress: 154.32 MPa
    Max stress: 238.73 MPa
    Min safety factor: 2.68

============================================================

Files saved:
  - bolt_report.txt (human-readable report)
  - bolt_results.json (data for further processing)
```

This project combines everything from the tutorial: functions for reusable logic, data structures for organizing information, file operations for persistence, testing for verification, and error handling for robustness. It's a complete, professional-quality tool that you built.

---

## Key Takeaway

Building your first real project follows three phases: plan what you want, build it piece by piece, and refine it until it's ready. Start small, get it working, then expand. Use the checklist to catch issues before shipping. The project above demonstrates that with the skills you've learned, you can build real, useful tools. Now it's your turn to create something that solves a problem you care about.

In the final chapter, we'll look at where to go from here.

