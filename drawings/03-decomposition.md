# 03: Decomposition

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║                             DECOMPOSITION                                    ║
║                                                                              ║
║    ╔═══════════════════════════════════════════════════════════════════╗     ║
║    ║                                                                   ║     ║
║    ║                        BIG PROBLEM                                ║     ║
║    ║                                                                   ║     ║
║    ║              "Build an inventory management system"               ║     ║
║    ║                                                                   ║     ║
║    ╚═══════════════════════════╤═══════════════════════════════════════╝     ║
║                                │                                             ║
║                   ┌────────────┼────────────┐                                ║
║                   │            │            │                                ║
║                   ▼            ▼            ▼                                ║
║           ┌───────────┐ ┌───────────┐ ┌───────────┐                          ║
║           │   Data    │ │    UI     │ │  Reports  │                          ║
║           │  Storage  │ │           │ │           │                          ║
║           └─────┬─────┘ └─────┬─────┘ └─────┬─────┘                          ║
║                 │             │             │                                ║
║          ┌──────┴──────┐     ─┴─      ┌─────┴─────┐                          ║
║          │             │     ...      │           │                          ║
║          ▼             ▼              ▼           ▼                          ║
║    ┌──────────┐ ┌──────────┐   ┌──────────┐ ┌──────────┐                     ║
║    │ Add item │ │ Get item │   │ Low stock│ │ Monthly  │                     ║
║    └──────────┘ └──────────┘   │  alert   │ │ summary  │                     ║
║          │             │       └──────────┘ └──────────┘                     ║
║          ▼             ▼                                                     ║
║    ┌──────────────────────────────────────────────────────────────────┐      ║
║    │                                                                  │      ║
║    │   SMALL PIECES  ←  Each piece = one clear prompt                 │      ║
║    │                                                                  │      ║
║    └──────────────────────────────────────────────────────────────────┘      ║
║                                                                              ║
║ ═══════════════════════════════════════════════════════════════════════════  ║
║                                                                              ║
║    RULE: If you can't describe it in one sentence, break it down more.       ║
║                                                                              ║
║    ┌────────────────────────────────────────────────────────────────────┐    ║
║    │                                                                    │    ║
║    │  ✗ "Build inventory system"         → Too big, unclear scope      │    ║
║    │                                                                    │    ║
║    │  ✓ "Create function that adds       → One clear action            │    ║
║    │     item with name, quantity,                                     │    ║
║    │     and price to a list"                                          │    ║
║    │                                                                    │    ║
║    └────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

## Reading This Drawing

**The Top Box (BIG PROBLEM):** This is where every project starts—with something too large to tackle at once. "Build an inventory management system" is a real request, but it's not actionable. You can't hand that to AI and expect working code. It's too vague, too broad.

**The First Split (Three Branches):** The big problem breaks into three major areas:
- **Data Storage:** Where and how items are stored
- **UI:** How users interact with the system
- **Reports:** What information comes out

These are still too big to code directly, but they're clearer. Each represents a distinct concern.

**The Second Split (Smaller Boxes):** Each area breaks down further:
- Data Storage → "Add item" and "Get item" (specific operations)
- Reports → "Low stock alert" and "Monthly summary" (specific outputs)
- UI → The `...` indicates more pieces exist but aren't shown

**The Bottom Box (SMALL PIECES):** This is the target. Each small piece equals one clear prompt. "Add item" becomes: "Create a function that adds an item with name, quantity, and price to a list." That's something AI can build in one response.

**The Rule Box:** The test for "small enough" is simple: can you describe it in one sentence? If not, break it down more. The ✗ shows a prompt that's too big. The ✓ shows the same idea broken down to a single, clear action.

**The Visual Pattern:** Notice how the diagram flows top-to-bottom, wide-to-narrow. Big and vague at top, small and specific at bottom. This is the shape of all decomposition.

## What This Shows

Big problems break into smaller problems. Keep breaking until each piece is one clear sentence. Each small piece becomes one prompt. Build pieces, then connect them.

## Key Insight

You can build anything if you can break it down enough. The skill is decomposition, not coding.

## What This Means In Practice

When you have a project idea:
1. Write it down (it will be too big)
2. Ask: "What are the main parts?"
3. For each part, ask: "Can I describe this in one sentence?"
4. If no, break it down further
5. Stop when each piece is one clear action

The number of levels depends on project size. A simple script might need one split. A complex application might need four or five. The process is the same.

---

[← The Loop](02-the-loop.md) | [Next: Operations →](04-operations.md)
