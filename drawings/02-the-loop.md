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

## Reading This Drawing

**The Flow:** Follow the arrows from top to bottom, then looping back. This is how every task works, from simple scripts to complex applications.

**DESCRIBE (Top):** You start here. Tell AI what you want in plain English. Examples:
- "Create a function that calculates stress from force and area"
- "Build a script that renames all files in a folder"
- "Make a web page with a form that collects user input"

You don't need technical language. Describe the outcome you want.

**GET (Second Step):** AI writes code based on your description. You don't write anything—you receive. The code appears in your project, ready to test.

**RUN (Third Step):** Execute what AI created. This is where you see if it actually works. Run the script, open the web page, call the function. Real results, not theoretical.

**EVALUATE (Decision Point):** Ask yourself: "Does this do what I needed?" Two paths:
- **Yes → DONE:** It works. Task complete. Move on.
- **No → REFINE:** Something's not right. Loop back.

**REFINE (Left Side):** When it's not quite right, you don't start over. You give feedback:
- "Change X to Y"
- "Fix the error on line 15"
- "Add validation for empty input"
- "Make it return the result in millimeters, not meters"

Then you loop back to GET—AI revises based on your feedback.

**The Cycle Count (Bottom Note):** Expect 2-5 loops for simple things, 5-15 for complex. This isn't failure—it's normal. Even experts iterate.

## Key Insight

The first result is a draft, not a final product. Plan for 2-5 cycles. Refinement is not failure—it's the process.

## What This Means In Practice

Don't expect perfection on the first try. When you describe something, AI makes its best guess about what you mean. Running the code reveals the gaps between what you meant and what AI understood. Each refinement closes that gap.

This is faster than traditional coding because:
- You're editing AI's work, not writing from scratch
- Each cycle takes seconds, not hours
- You focus on "what's wrong" not "how to fix it"

---

[← The Core](01-the-core.md) | [Next: Decomposition →](03-decomposition.md)
