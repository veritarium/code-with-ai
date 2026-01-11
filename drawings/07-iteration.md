# 07: Iteration

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║                              ITERATION                                       ║
║                                                                              ║
║   First Draft → Refinement → Better Draft → Refinement → Done                ║
║                                                                              ║
║                                                                              ║
║        ┌──────────────────────────────────────────────────────────────┐      ║
║        │                                                              │      ║
║        │    V1              V2              V3              V4        │      ║
║        │    ┌───┐           ┌───┐           ┌───┐           ┌───┐     │      ║
║        │    │ ▪ │           │▪▪ │           │▪▪▪│           │███│     │      ║
║        │    │   │           │▪  │           │▪▪ │           │███│     │      ║
║        │    │   │           │   │           │▪  │           │███│     │      ║
║        │    └───┘           └───┘           └───┘           └───┘     │      ║
║        │    10%             40%             75%             100%      │      ║
║        │                                                              │      ║
║        │        ──────►          ──────►          ──────►             │      ║
║        │        refine           refine           refine              │      ║
║        │                                                              │      ║
║        └──────────────────────────────────────────────────────────────┘      ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   GOOD FEEDBACK vs BAD FEEDBACK:                                             ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │                                                                     │    ║
║   │    ✗ BAD                          ✓ GOOD                           │    ║
║   │    ─────                          ──────                           │    ║
║   │                                                                     │    ║
║   │    "Wrong"                        "Output is 42, should be 84"     │    ║
║   │                                                                     │    ║
║   │    "Fix it"                       "Handle the case when input      │    ║
║   │                                    is empty"                        │    ║
║   │                                                                     │    ║
║   │    "Not what I wanted"            "Sort descending instead         │    ║
║   │                                    of ascending"                    │    ║
║   │                                                                     │    ║
║   │    "Try again"                    "Use mm instead of inches        │    ║
║   │                                    for all measurements"            │    ║
║   │                                                                     │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │                                                                     │    ║
║   │   FEEDBACK FORMULA:                                                 │    ║
║   │                                                                     │    ║
║   │   ┌──────────────────────────────────────────────────────────────┐ │    ║
║   │   │  "Got [X]. Expected [Y]. Change [how]."                      │ │    ║
║   │   └──────────────────────────────────────────────────────────────┘ │    ║
║   │                                                                     │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   WHEN TO RESTART vs REFINE:                                                 ║
║                                                                              ║
║   ┌───────────────────────────┐    ┌───────────────────────────────┐         ║
║   │         REFINE            │    │          RESTART              │         ║
║   │                           │    │                               │         ║
║   │  • Structure is right     │    │  • Fundamentally wrong        │         ║
║   │  • Details are wrong      │    │  • Wrong approach             │         ║
║   │  • Missing edge case      │    │  • After 5+ failed refines    │         ║
║   │  • Small behavior change  │    │  • Easier to start fresh      │         ║
║   └───────────────────────────┘    └───────────────────────────────┘         ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

## What This Shows

Software emerges through refinement, not in one shot. Good feedback is specific: what happened, what should happen, how to change it. Know when to keep refining vs. start fresh.

## Key Insight

Iteration is not failure—it's the process. Plan for it. Budget 3-5 cycles for any task.

---

[← Specificity](06-specificity.md) | [Next: Pipeline Pattern →](08-pattern-pipeline.md)
