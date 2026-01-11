# 02: The Loop

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║                                THE LOOP                                      ║
║                                                                              ║
║                          ┌─────────────────┐                                 ║
║                          │                 │                                 ║
║               ┌──────────│    DESCRIBE     │◄─────────┐                      ║
║               │          │                 │          │                      ║
║               │          │  "Create a..."  │          │                      ║
║               │          └────────┬────────┘          │                      ║
║               │                   │                   │                      ║
║               │                   ▼                   │                      ║
║               │          ┌─────────────────┐          │                      ║
║               │          │                 │          │                      ║
║       ┌───────┴───────┐  │      GET        │          │                      ║
║       │               │  │                 │          │                      ║
║       │    REFINE     │  │   AI writes     │          │                      ║
║       │               │  │   code for you  │          │                      ║
║       │ "Change X..." │  └────────┬────────┘          │                      ║
║       │ "Fix the..."  │           │                   │                      ║
║       │ "Add..."      │           ▼                   │                      ║
║       │               │  ┌─────────────────┐          │                      ║
║       └───────┬───────┘  │                 │          │                      ║
║               │          │      RUN        │          │                      ║
║               │          │                 │   ┌──────┴──────┐               ║
║               │          │  Execute and    │   │             │               ║
║               │          │  observe result │   │    DONE     │               ║
║               │          └────────┬────────┘   │             │               ║
║               │                   │            │  It works!  │               ║
║               │                   ▼            │             │               ║
║               │          ┌─────────────────┐   └─────────────┘               ║
║               │          │                 │          ▲                      ║
║               │          │    EVALUATE     ├──────────┘                      ║
║               │          │                 │  Yes                            ║
║               └──────────┤  Does it work?  │                                 ║
║                    No    │                 │                                 ║
║                          └─────────────────┘                                 ║
║                                                                              ║
║                                                                              ║
║      ┌─────────────────────────────────────────────────────────────────┐     ║
║      │  Typical cycles: 2-5 for simple tasks, 5-15 for complex ones   │     ║
║      └─────────────────────────────────────────────────────────────────┘     ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

## What This Shows

Every task follows this loop. Describe what you want. AI generates code. Run it. Evaluate if it works. If yes, done. If no, refine and loop again.

## Key Insight

The first result is a draft, not a final product. Plan for 2-5 cycles. Refinement is not failure—it's the process.

---

[← The Core](01-the-core.md) | [Next: Decomposition →](03-decomposition.md)
