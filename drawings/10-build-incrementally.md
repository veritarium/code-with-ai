# 10: Build Incrementally

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║                         BUILD INCREMENTALLY                                  ║
║                                                                              ║
║   Small working steps, not giant leaps                                       ║
║                                                                              ║
║  ┌──────────────────────────────────────────────────────────────────────┐    ║
║  │                                                                      │    ║
║  │   ✗ WRONG: Build everything, then test                               │    ║
║  │                                                                      │    ║
║  │   ┌─────┐    ┌─────┐    ┌─────┐    ┌─────┐         ┌─────┐          │    ║
║  │   │Build│───►│Build│───►│Build│───►│Build│────────►│Test │          │    ║
║  │   │  A  │    │  B  │    │  C  │    │  D  │         │ ALL │          │    ║
║  │   └─────┘    └─────┘    └─────┘    └─────┘         └──┬──┘          │    ║
║  │                                                       │              │    ║
║  │                                                       ▼              │    ║
║  │                                            ┌──────────────────┐      │    ║
║  │                                            │ 💥 Broken mess   │      │    ║
║  │                                            │ Where's the bug? │      │    ║
║  │                                            └──────────────────┘      │    ║
║  │                                                                      │    ║
║  └──────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ┌──────────────────────────────────────────────────────────────────────┐    ║
║  │                                                                      │    ║
║  │   ✓ RIGHT: Build, verify, extend, verify, extend...                  │    ║
║  │                                                                      │    ║
║  │   ┌─────┐    ┌────┐    ┌─────┐    ┌────┐    ┌─────┐    ┌────┐       │    ║
║  │   │Build│───►│Test│───►│Build│───►│Test│───►│Build│───►│Test│       │    ║
║  │   │  A  │    │ A  │    │ +B  │    │A+B │    │ +C  │    │ALL │       │    ║
║  │   └─────┘    └──┬─┘    └─────┘    └──┬─┘    └─────┘    └──┬─┘       │    ║
║  │                 │                    │                    │          │    ║
║  │                 ▼                    ▼                    ▼          │    ║
║  │               ┌──┐                 ┌──┐                 ┌──┐         │    ║
║  │               │✓ │                 │✓ │                 │✓ │         │    ║
║  │               └──┘                 └──┘                 └──┘         │    ║
║  │                                                                      │    ║
║  │   Each step: working software                                        │    ║
║  │   Bug appears: must be in last change                                │    ║
║  │                                                                      │    ║
║  └──────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   THE GOLDEN RULE:                                                           ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │                                                                     │    ║
║   │    ╔═══════════════════════════════════════════════════════════╗    │    ║
║   │    ║                                                           ║    │    ║
║   │    ║   Never add to broken code. Fix first, then extend.       ║    │    ║
║   │    ║                                                           ║    │    ║
║   │    ╚═══════════════════════════════════════════════════════════╝    │    ║
║   │                                                                     │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   EXAMPLE BUILD SEQUENCE:                                                    ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │                                                                     │    ║
║   │   Goal: Calculator with history                                     │    ║
║   │                                                                     │    ║
║   │   Step 1: "Create function that adds two numbers"        → Test ✓   │    ║
║   │   Step 2: "Add subtract, multiply, divide"               → Test ✓   │    ║
║   │   Step 3: "Add input parsing for '5 + 3' format"         → Test ✓   │    ║
║   │   Step 4: "Store each calculation in history list"       → Test ✓   │    ║
║   │   Step 5: "Add command to show history"                  → Test ✓   │    ║
║   │   Step 6: "Add command to clear history"                 → Test ✓   │    ║
║   │                                                                     │    ║
║   │   Each step: small, testable, working                               │    ║
║   │                                                                     │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

## Reading This Drawing

**The WRONG Way (Top Box):** Build A → Build B → Build C → Build D → Test ALL. Four things built before any testing. When the test fails, you have no idea where the bug is. It could be in A, B, C, D, or in how they connect. Result: a broken mess with no clear fix.

**The RIGHT Way (Second Box):** Build A → Test A → Build +B → Test A+B → Build +C → Test ALL. Each step ends with verification (✓). If something breaks after adding +B, you know the bug is in B—there's nowhere else it could be.

**Two Critical Insights:**
- "Each step: working software" — You always have something that works
- "Bug appears: must be in last change" — Debugging is trivial

**The Golden Rule (Highlighted Box):** "Never add to broken code. Fix first, then extend." This is the discipline that makes incremental building work. If step 2 breaks, you don't move to step 3. You fix step 2 first. Otherwise you're building on a broken foundation.

**The Example Build Sequence:** A concrete demonstration with a calculator:
1. "Create function that adds two numbers" → Test ✓ (Start with one tiny thing)
2. "Add subtract, multiply, divide" → Test ✓ (Expand math operations)
3. "Add input parsing for '5 + 3' format" → Test ✓ (User interface)
4. "Store each calculation in history list" → Test ✓ (New feature)
5. "Add command to show history" → Test ✓ (Access the feature)
6. "Add command to clear history" → Test ✓ (Complete the feature)

Each step is one prompt. Each prompt is small enough to be obviously correct or obviously wrong. No ambiguity.

## What This Shows

Build in small verified steps. Each step produces working software. If something breaks, the bug is in the last change. Never extend broken code—fix first.

## Key Insight

The fastest way to build big things is lots of small correct steps. Resist the urge to do too much at once.

## What This Means In Practice

Before each prompt, ask:
1. Is the current code working? (If no, fix it first)
2. What's the smallest useful next step?
3. How will I test this step?

The temptation is always to do more in one step. Resist it. Six small prompts that each work beats one big prompt that creates a debugging nightmare.

---

[← Web App Pattern](09-pattern-webapp.md) | [Next: Automation Pattern →](11-pattern-automation.md)
