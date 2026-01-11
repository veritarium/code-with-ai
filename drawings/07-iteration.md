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

## Reading This Drawing

**The Version Boxes (V1 → V4):** Each box shows progress toward completeness. The fill pattern (▪ to █) represents how much of the solution is correct:
- **V1 (10%):** First attempt. Something exists, but mostly incomplete.
- **V2 (40%):** After first refinement. Core structure taking shape.
- **V3 (75%):** Getting close. Most functionality works.
- **V4 (100%):** Done. Everything works as needed.

The arrows labeled "refine" connect each version. This is the heartbeat of AI-assisted development.

**Good Feedback vs Bad Feedback Table:** The critical skill is giving feedback AI can act on.
- **Bad:** "Wrong" → AI doesn't know what's wrong
- **Good:** "Output is 42, should be 84" → AI knows exactly what to fix
- **Bad:** "Fix it" → Fix what, exactly?
- **Good:** "Handle the case when input is empty" → Specific edge case to address
- **Bad:** "Not what I wanted" → AI still doesn't know what you wanted
- **Good:** "Sort descending instead of ascending" → Clear direction for change

**The Feedback Formula:** This is the pattern for effective refinement:
```
"Got [X]. Expected [Y]. Change [how]."
```
Example: "Got 42. Expected 84. Multiply by 2 before returning."

Three components: current state, desired state, direction for fix.

**Refine vs Restart:** Two boxes showing when to use each strategy:
- **REFINE when:** Structure is right, details are wrong, missing edge cases, small behavior changes. The foundation is solid; you're adjusting.
- **RESTART when:** Fundamentally wrong approach, after 5+ failed refinements, easier to describe fresh than to fix. Cut your losses.

The 5-refinement rule is important: if you've tried to fix something 5 times and it's still wrong, the approach is probably wrong. Start over with a clearer description.

## What This Shows

Software emerges through refinement, not in one shot. Good feedback is specific: what happened, what should happen, how to change it. Know when to keep refining vs. start fresh.

## Key Insight

Iteration is not failure—it's the process. Plan for it. Budget 3-5 cycles for any task.

## What This Means In Practice

When giving feedback:
1. Run the code and observe the result
2. Note what actually happened (Got X)
3. State what should have happened (Expected Y)
4. Suggest how to fix it if you know (Change Z)

Don't say: "This doesn't work."
Do say: "This returns null when I pass an empty array. It should return an empty array instead."

The quality of your feedback determines the speed of your progress. Specific feedback = fast iteration. Vague feedback = spinning in circles.

---

[← Specificity](06-specificity.md) | [Next: Pipeline Pattern →](08-pattern-pipeline.md)
