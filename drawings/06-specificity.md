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

## What This Shows

Precision of input directly determines precision of output. Vague prompts force AI to guess. Specific prompts tell AI exactly what to do. The components of specificity: What, Where, How, Why, Example.

## Key Insight

Time spent being specific upfront saves multiple refinement cycles. One detailed prompt beats five vague ones.

---

[← Context](05-context.md) | [Next: Iteration →](07-iteration.md)
