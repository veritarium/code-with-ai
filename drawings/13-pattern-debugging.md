# 13: Pattern — Debugging

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║                          PATTERN: DEBUGGING                                  ║
║                                                                              ║
║   Use this pattern when: Something doesn't work                              ║
║                                                                              ║
║  ┌──────────────────────────────────────────────────────────────────────┐    ║
║  │                                                                      │    ║
║  │   ┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐          │    ║
║  │   │         │    │         │    │         │    │         │          │    ║
║  │   │ SYMPTOM │───►│ LOCATE  │───►│  UNDER- │───►│   FIX   │          │    ║
║  │   │         │    │         │    │  STAND  │    │         │          │    ║
║  │   └─────────┘    └─────────┘    └─────────┘    └─────────┘          │    ║
║  │                                                                      │    ║
║  │   What's wrong?  Where?         Why?           Change it             │    ║
║  │                                                                      │    ║
║  └──────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   ERROR TYPES AND RESPONSES:                                                 ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │                                                                     │    ║
║   │   ┌────────────┬─────────────────────┬───────────────────────────┐ │    ║
║   │   │  TYPE      │  LOOKS LIKE         │  SAY                      │ │    ║
║   │   ├────────────┼─────────────────────┼───────────────────────────┤ │    ║
║   │   │            │                     │                           │ │    ║
║   │   │  Syntax    │  SyntaxError        │  "[error]" fix syntax     │ │    ║
║   │   │            │  Unexpected token   │                           │ │    ║
║   │   │            │                     │                           │ │    ║
║   │   │  Runtime   │  TypeError          │  "[error]" why does       │ │    ║
║   │   │            │  NameError          │  this happen?             │ │    ║
║   │   │            │  NullPointer        │                           │ │    ║
║   │   │            │                     │                           │ │    ║
║   │   │  Logic     │  No error, but      │  Expected [X] but got     │ │    ║
║   │   │            │  wrong output       │  [Y]. Why?                │ │    ║
║   │   │            │                     │                           │ │    ║
║   │   │  Import    │  ModuleNotFound     │  Install [module]         │ │    ║
║   │   │            │  Cannot find        │                           │ │    ║
║   │   │            │                     │                           │ │    ║
║   │   │  Data      │  KeyError           │  Data issue: [error]      │ │    ║
║   │   │            │  IndexError         │  Show me the data shape   │ │    ║
║   │   │            │                     │                           │ │    ║
║   │   └────────────┴─────────────────────┴───────────────────────────┘ │    ║
║   │                                                                     │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   DEBUGGING DECISION TREE:                                                   ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │                                                                     │    ║
║   │                    ┌─────────────────┐                              │    ║
║   │                    │ Something broke │                              │    ║
║   │                    └────────┬────────┘                              │    ║
║   │                             │                                       │    ║
║   │                             ▼                                       │    ║
║   │                    ┌─────────────────┐                              │    ║
║   │               ┌────┤ Error message?  ├────┐                         │    ║
║   │               │    └─────────────────┘    │                         │    ║
║   │              YES                          NO                        │    ║
║   │               │                           │                         │    ║
║   │               ▼                           ▼                         │    ║
║   │    ┌──────────────────┐        ┌──────────────────┐                 │    ║
║   │    │ Paste error,     │        │ "Expected [X]    │                 │    ║
║   │    │ ask "Fix this"   │        │  got [Y]. Why?"  │                 │    ║
║   │    └──────────────────┘        └──────────────────┘                 │    ║
║   │                                                                     │    ║
║   │                             │                                       │    ║
║   │                             ▼                                       │    ║
║   │                    ┌─────────────────┐                              │    ║
║   │               ┌────┤    Fixed?       ├────┐                         │    ║
║   │               │    └─────────────────┘    │                         │    ║
║   │              YES                          NO                        │    ║
║   │               │                           │                         │    ║
║   │               ▼                           ▼                         │    ║
║   │           ┌──────┐             ┌──────────────────┐                 │    ║
║   │           │ Done │             │ "Still broken:   │                 │    ║
║   │           └──────┘             │  [new symptom]"  │                 │    ║
║   │                                └──────────────────┘                 │    ║
║   │                                                                     │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   ISOLATION TECHNIQUE:                                                       ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │                                                                     │    ║
║   │   When bug hides in complex code:                                   │    ║
║   │                                                                     │    ║
║   │   ┌─────────────────────────────────────────────────────────────┐   │    ║
║   │   │                                                             │   │    ║
║   │   │    FULL CODE (broken)                                       │   │    ║
║   │   │         │                                                   │   │    ║
║   │   │         ▼                                                   │   │    ║
║   │   │    ┌─────────┐    ┌─────────┐    ┌─────────┐               │   │    ║
║   │   │    │ Part A  │    │ Part B  │    │ Part C  │               │   │    ║
║   │   │    │  works  │    │ BROKEN  │    │  works  │               │   │    ║
║   │   │    └─────────┘    └─────────┘    └─────────┘               │   │    ║
║   │   │                        │                                    │   │    ║
║   │   │                        ▼                                    │   │    ║
║   │   │               "Test only Part B with                        │   │    ║
║   │   │                simple input"                                │   │    ║
║   │   │                                                             │   │    ║
║   │   └─────────────────────────────────────────────────────────────┘   │    ║
║   │                                                                     │    ║
║   │   "Comment out parts until it works, then add back one by one"      │    ║
║   │                                                                     │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   THE DEBUG PROMPT FORMULA:                                                  ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │                                                                     │    ║
║   │   ╔═════════════════════════════════════════════════════════════╗   │    ║
║   │   ║                                                             ║   │    ║
║   │   ║   "I tried [action]. Got [result]. Expected [expected].     ║   │    ║
║   │   ║    Here's the error: [paste]. Fix it."                      ║   │    ║
║   │   ║                                                             ║   │    ║
║   │   ╚═════════════════════════════════════════════════════════════╝   │    ║
║   │                                                                     │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

## Reading This Drawing

**The Four-Step Process (Top):** Every debugging session follows this flow:
- **SYMPTOM:** What's wrong? An error message, wrong output, unexpected behavior
- **LOCATE:** Where is it? Which file, function, or line
- **UNDERSTAND:** Why does this happen? Root cause, not just surface problem
- **FIX:** Change it. Apply the solution

Don't skip steps. Fixing without understanding leads to new bugs.

**Error Types Table:** Different errors need different approaches:
- **Syntax:** The code isn't valid. "SyntaxError," "Unexpected token." Prompt: `"[error]" fix syntax`
- **Runtime:** Code is valid but fails when running. "TypeError," "NameError," "NullPointer." Prompt: `"[error]" why does this happen?`
- **Logic:** No error, but wrong output. The hardest to debug. Prompt: `Expected [X] but got [Y]. Why?`
- **Import:** Missing dependency. "ModuleNotFound." Prompt: `Install [module]`
- **Data:** Problem with the data itself. "KeyError," "IndexError." Prompt: `Data issue: [error] Show me the data shape`

Each type has a pattern for how to ask AI for help.

**The Decision Tree:** A flowchart for debugging:
1. Something broke
2. Is there an error message?
   - YES → Paste error, ask "Fix this"
   - NO → Describe "Expected [X] got [Y]. Why?"
3. Is it fixed?
   - YES → Done
   - NO → "Still broken: [new symptom]"

Keep looping until fixed.

**Isolation Technique:** When the bug hides in complex code:
- The full code is broken, but you don't know which part
- Split into Part A, Part B, Part C
- Test each part independently with simple input
- Find the broken part, fix it there
- Alternative: "Comment out parts until it works, then add back one by one"

Isolation narrows the search space. Instead of searching 1000 lines, you search 100.

**The Debug Prompt Formula (Highlighted):** The optimal structure for debugging prompts:
```
"I tried [action]. Got [result]. Expected [expected]. Here's the error: [paste]. Fix it."
```

Example: "I tried calling calculate(5, 0). Got a ZeroDivisionError. Expected it to return 0 when dividing by zero. Here's the error: [paste traceback]. Fix it."

This gives AI everything it needs: context, actual result, expected result, and the error.

## What This Shows

Debugging flow: Symptom → Locate → Understand → Fix. Different error types need different responses. Use the decision tree to navigate. When stuck, isolate the problem by testing parts separately.

## Key Insight

The error message is your friend. Paste it, describe what you expected, let AI figure out the rest. Most bugs are found in the last thing you changed.

## What This Means In Practice

When something breaks:
1. Copy the entire error message (don't summarize)
2. Describe what you were trying to do
3. Describe what you expected to happen
4. Ask AI to fix it

If the fix doesn't work, say "Still broken" and describe the new symptom. Debugging is iterative—expect 2-3 rounds for complex bugs.

---

[← API Pattern](12-pattern-api.md) | [Next: Testing Pattern →](14-pattern-testing.md)
