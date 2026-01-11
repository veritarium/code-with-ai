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

## What This Shows

Big problems break into smaller problems. Keep breaking until each piece is one clear sentence. Each small piece becomes one prompt. Build pieces, then connect them.

## Key Insight

You can build anything if you can break it down enough. The skill is decomposition, not coding.

---

[← The Loop](02-the-loop.md) | [Next: Operations →](04-operations.md)
