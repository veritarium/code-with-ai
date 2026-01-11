# 06: Specificity

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║                             SPECIFICITY                                      ║
║                                                                              ║
║   Input Precision Determines Output Precision                                ║
║                                                                              ║
║   VAGUE                                                          PRECISE     ║
║     │                                                                │       ║
║     ▼                                                                ▼       ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │░░░░░░░░░░░░░░░░░░░░░░░░░│▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒│████████████████████│    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║     "Make it work"            "Fix the bug"        "In auth.py line 42,      ║
║                                                     change == to != in       ║
║     ↓                         ↓                     the role check"          ║
║                                                                              ║
║     AI guesses               AI tries               ↓                        ║
║     everything               its best                                        ║
║                                                     AI does exactly           ║
║     ↓                         ↓                     what you said            ║
║                                                                              ║
║     Usually wrong             Sometimes right        ↓                        ║
║                                                                              ║
║                                                     Exactly right            ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   SPECIFICITY COMPONENTS:                                                    ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │                                                                     │    ║
║   │   ┌─────────┐  ┌─────────┐  ┌─────────┐  ┌─────────┐  ┌─────────┐  │    ║
║   │   │  WHAT   │  │  WHERE  │  │   HOW   │  │  WHY    │  │ EXAMPLE │  │    ║
║   │   │         │  │         │  │         │  │         │  │         │  │    ║
║   │   │ Action  │  │ File /  │  │ Method/ │  │ Purpose/│  │ Sample  │  │    ║
║   │   │ to take │  │ Location│  │ Style   │  │ Goal    │  │ Output  │  │    ║
║   │   └─────────┘  └─────────┘  └─────────┘  └─────────┘  └─────────┘  │    ║
║   │                                                                     │    ║
║   │   More components = More precision = Better result                  │    ║
║   │                                                                     │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   EXAMPLE PROGRESSION:                                                       ║
║                                                                              ║
║   Level 1:  "Calculate stress"                                               ║
║   Level 2:  "Calculate stress in a beam"                                     ║
║   Level 3:  "Calculate bending stress in a simply supported beam"            ║
║   Level 4:  "Create function calc_bending_stress(moment, distance, inertia)  ║
║              that returns stress in MPa using σ = My/I"                      ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │  Level 4 gets exactly what you want on first try.                   │    ║
║   │  Level 1 takes 5+ iterations to get there.                          │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

## Reading This Drawing

**The Gradient Bar:** This is the core visual. Left side (░) is vague. Middle (▒) is moderate. Right side (█) is precise. The bar shows that specificity is a spectrum, not a binary.

**The Three Examples Below the Bar:**
- **"Make it work"** (left, vague): AI has to guess what "it" means, what "work" looks like. The result is usually wrong because there are too many possible interpretations.
- **"Fix the bug"** (middle): Better—AI knows something is wrong and needs fixing. But which bug? In which file? AI still has to guess.
- **"In auth.py line 42, change == to != in the role check"** (right, precise): AI knows exactly what file, what line, what change. No guessing needed.

**The Outcome Chain:** Each specificity level leads to a different outcome:
- Vague → AI guesses → Usually wrong
- Moderate → AI tries its best → Sometimes right
- Precise → AI does exactly what you said → Exactly right

**The Five Components Box:** These are the building blocks of specificity:
- **WHAT:** The action to take ("create", "fix", "change")
- **WHERE:** The file or location ("in auth.py", "line 42")
- **HOW:** The method or style ("using σ = My/I", "with error handling")
- **WHY:** The purpose or goal ("for calculating beam stress")
- **EXAMPLE:** Sample output ("should return 25.5 MPa")

The more components you include, the more precise the result.

**The Progression Example:** Four levels of the same request:
- Level 1: "Calculate stress" (what calculation? what kind of stress?)
- Level 2: "Calculate stress in a beam" (adds where)
- Level 3: "Calculate bending stress in a simply supported beam" (adds how)
- Level 4: Complete with function name, parameters, formula, units (all five components)

**The Bottom Note:** Level 4 works on first try. Level 1 takes 5+ iterations. This is the cost of vagueness—measured in refinement cycles, not difficulty.

## What This Shows

Precision of input directly determines precision of output. Vague prompts force AI to guess. Specific prompts tell AI exactly what to do. The components of specificity: What, Where, How, Why, Example.

## Key Insight

Time spent being specific upfront saves multiple refinement cycles. One detailed prompt beats five vague ones.

## What This Means In Practice

Before prompting, ask yourself these five questions:
1. **What** exactly should AI do? (verb + object)
2. **Where** should it happen? (file, function, line)
3. **How** should it be done? (method, style, constraints)
4. **Why** does this matter? (purpose, goal)
5. **Example** of what success looks like? (expected output)

You don't always need all five. But the more you include, the fewer iterations you'll need. A 30-second investment in specificity saves 5 minutes of refinement.

---

[← Context](05-context.md) | [Next: Iteration →](07-iteration.md)
