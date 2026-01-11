# 14: Pattern — Testing

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║                           PATTERN: TESTING                                   ║
║                                                                              ║
║   Use this pattern when: You need to verify code works correctly             ║
║                                                                              ║
║  ┌──────────────────────────────────────────────────────────────────────┐    ║
║  │                                                                      │    ║
║  │   ┌─────────┐         ┌─────────┐         ┌─────────┐               │    ║
║  │   │         │         │         │         │         │               │    ║
║  │   │  INPUT  │────────►│  CODE   │────────►│ OUTPUT  │               │    ║
║  │   │         │         │         │         │         │               │    ║
║  │   └─────────┘         └─────────┘         └────┬────┘               │    ║
║  │                                                │                     │    ║
║  │                                                ▼                     │    ║
║  │                                     ┌──────────────────┐             │    ║
║  │                                     │                  │             │    ║
║  │                                     │  OUTPUT = EXPECTED?            │    ║
║  │                                     │                  │             │    ║
║  │                                     └────────┬─────────┘             │    ║
║  │                                              │                       │    ║
║  │                                    ┌─────────┴─────────┐             │    ║
║  │                                    │                   │             │    ║
║  │                                   YES                  NO            │    ║
║  │                                    │                   │             │    ║
║  │                                    ▼                   ▼             │    ║
║  │                               ┌────────┐         ┌────────┐          │    ║
║  │                               │   ✓    │         │   ✗    │          │    ║
║  │                               │  PASS  │         │  FAIL  │          │    ║
║  │                               └────────┘         └────────┘          │    ║
║  │                                                                      │    ║
║  └──────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   TEST STRUCTURE:                                                            ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │                                                                     │    ║
║   │   ┌─────────────────────────────────────────────────────────────┐   │    ║
║   │   │                                                             │   │    ║
║   │   │   1. ARRANGE      Set up inputs and expected result         │   │    ║
║   │   │                                                             │   │    ║
║   │   │   2. ACT          Run the code being tested                 │   │    ║
║   │   │                                                             │   │    ║
║   │   │   3. ASSERT       Check output matches expected             │   │    ║
║   │   │                                                             │   │    ║
║   │   └─────────────────────────────────────────────────────────────┘   │    ║
║   │                                                                     │    ║
║   │   Example:                                                          │    ║
║   │   ┌─────────────────────────────────────────────────────────────┐   │    ║
║   │   │  # ARRANGE                                                  │   │    ║
║   │   │  input = 5                                                  │   │    ║
║   │   │  expected = 25                                              │   │    ║
║   │   │                                                             │   │    ║
║   │   │  # ACT                                                      │   │    ║
║   │   │  result = square(input)                                     │   │    ║
║   │   │                                                             │   │    ║
║   │   │  # ASSERT                                                   │   │    ║
║   │   │  assert result == expected                                  │   │    ║
║   │   └─────────────────────────────────────────────────────────────┘   │    ║
║   │                                                                     │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   WHAT TO TEST (Edge Cases):                                                 ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │                                                                     │    ║
║   │   ┌─────────────┬───────────────────────────────────────────────┐  │    ║
║   │   │  CATEGORY   │   TEST CASES                                  │  │    ║
║   │   ├─────────────┼───────────────────────────────────────────────┤  │    ║
║   │   │  Normal     │   Typical input that should work              │  │    ║
║   │   │  Empty      │   Empty string, empty list, zero, null        │  │    ║
║   │   │  Boundary   │   Min value, max value, exactly at limit      │  │    ║
║   │   │  Invalid    │   Wrong type, negative when positive needed   │  │    ║
║   │   │  Large      │   Very big numbers, long strings              │  │    ║
║   │   │  Special    │   Special characters, unicode, whitespace     │  │    ║
║   │   └─────────────┴───────────────────────────────────────────────┘  │    ║
║   │                                                                     │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   TESTING WORKFLOW:                                                          ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │                                                                     │    ║
║   │   METHOD 1: Test After (most common)                                │    ║
║   │                                                                     │    ║
║   │   ┌────────┐    ┌────────┐    ┌────────┐    ┌────────┐             │    ║
║   │   │ Write  │───►│  Run   │───►│ Write  │───►│  Run   │             │    ║
║   │   │  Code  │    │  Code  │    │ Tests  │    │ Tests  │             │    ║
║   │   └────────┘    └────────┘    └────────┘    └────────┘             │    ║
║   │                                                                     │    ║
║   │   ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─    │    ║
║   │                                                                     │    ║
║   │   METHOD 2: Test First (catches more bugs)                          │    ║
║   │                                                                     │    ║
║   │   ┌────────┐    ┌────────┐    ┌────────┐    ┌────────┐             │    ║
║   │   │ Write  │───►│  Run   │───►│ Write  │───►│  Run   │             │    ║
║   │   │ Tests  │    │(fails) │    │  Code  │    │(passes)│             │    ║
║   │   └────────┘    └────────┘    └────────┘    └────────┘             │    ║
║   │                                                                     │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   BUILD SEQUENCE:                                                            ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │                                                                     │    ║
║   │   1. "Create function calculate_area(length, width)"                │    ║
║   │                                                                     │    ║
║   │   2. "Write tests for calculate_area covering:                      │    ║
║   │       - normal case (3, 4 → 12)                                     │    ║
║   │       - zero (0, 5 → 0)                                             │    ║
║   │       - negative (should raise error or return 0?)"                 │    ║
║   │                                                                     │    ║
║   │   3. "Run the tests"                                                │    ║
║   │                                                                     │    ║
║   │   4. "Tests for negative failed. Fix calculate_area to              │    ║
║   │       raise ValueError for negative inputs"                         │    ║
║   │                                                                     │    ║
║   │   5. "Run tests again"                                              │    ║
║   │                                                                     │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │                                                                     │    ║
║   │   TEST PROMPT FORMULA:                                              │    ║
║   │                                                                     │    ║
║   │   ╔═════════════════════════════════════════════════════════════╗   │    ║
║   │   ║  "Write tests for [function] covering [normal case],        ║   │    ║
║   │   ║   [edge case 1], [edge case 2], [error case]"               ║   │    ║
║   │   ╚═════════════════════════════════════════════════════════════╝   │    ║
║   │                                                                     │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

## Reading This Drawing

**The Core Concept (Top Diagram):** Testing is a comparison:
1. Give INPUT to CODE
2. Get OUTPUT
3. Compare: Does OUTPUT equal EXPECTED?
4. YES → ✓ PASS | NO → ✗ FAIL

This is all testing is: automated checking that code produces expected results.

**The AAA Structure:** Every test follows three steps:
- **ARRANGE:** Set up the test. Define inputs and expected result.
- **ACT:** Run the code being tested. Call the function.
- **ASSERT:** Check the result. Does output match expected?

The example shows this concretely:
```
# ARRANGE
input = 5
expected = 25

# ACT
result = square(input)

# ASSERT
assert result == expected
```

**Edge Cases Table:** What to test beyond the happy path:
- **Normal:** Typical input that should work. `square(5)` → `25`
- **Empty:** Zero, null, empty string, empty list. `square(0)` → `0`
- **Boundary:** At the limits. Min value, max value, exactly at threshold
- **Invalid:** Wrong inputs. Negative when positive needed, wrong type
- **Large:** Stress tests. Very big numbers, long strings
- **Special:** Edge characters. Unicode, whitespace, special symbols

Most bugs hide in edge cases, not normal cases.

**Testing Workflows:** Two approaches:

**Method 1 - Test After:** Write code → Run code → Write tests → Run tests
This is how most people start. Build the feature first, then verify it.

**Method 2 - Test First:** Write tests → Run (fails) → Write code → Run (passes)
Tests define what "done" means before you write any code. Forces you to think through requirements first. Catches more bugs.

**The Build Sequence:** A practical example:
1. "Create function calculate_area(length, width)" — Build the function
2. "Write tests for calculate_area covering: normal case, zero, negative" — Define what should happen
3. "Run the tests" — See what passes/fails
4. "Tests for negative failed. Fix calculate_area to raise ValueError for negative inputs" — Fix based on test result
5. "Run tests again" — Verify fix worked

**The Test Prompt Formula (Highlighted):**
```
"Write tests for [function] covering [normal case], [edge case 1], [edge case 2], [error case]"
```

Example: "Write tests for calculate_stress covering: normal (1000N, 50mm²), zero area (should error), negative force (should error), very large values"

## What This Shows

Testing: Input → Code → Output → Compare to Expected. Structure tests as Arrange-Act-Assert. Test edge cases: normal, empty, boundary, invalid, large, special. Write tests after code, or write tests first to catch more bugs.

## Key Insight

Tests are your safety net. They catch bugs before users do. Ask AI to write tests for edge cases you might not think of.

## What This Means In Practice

After writing any important function:
1. Ask AI to write tests covering normal and edge cases
2. Run the tests
3. Fix any failures
4. Keep tests for future changes

Tests let you change code confidently. If tests still pass, you didn't break anything.

---

[← Debugging Pattern](13-pattern-debugging.md) | [Next: Engineering Calculation →](15-pattern-engineering-calc.md)
