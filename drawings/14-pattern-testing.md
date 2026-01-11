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

## What This Shows

Testing: Input → Code → Output → Compare to Expected. Structure tests as Arrange-Act-Assert. Test edge cases: normal, empty, boundary, invalid, large, special. Write tests after code, or write tests first to catch more bugs.

## Key Insight

Tests are your safety net. They catch bugs before users do. Ask AI to write tests for edge cases you might not think of.

---

[← Debugging Pattern](13-pattern-debugging.md) | [Next: Engineering Calculation →](15-pattern-engineering-calc.md)
