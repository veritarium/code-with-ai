# 05: Context

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║                               CONTEXT                                        ║
║                                                                              ║
║                        What AI Can See                                       ║
║                                                                              ║
║      ┌────────────────────────────────────────────────────────────────┐      ║
║      │ ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░ │      ║
║      │ ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░ │      ║
║      │ ░░░░░░░░░░░░   YOUR ENTIRE WORLD   ░░░░░░░░░░░░░░░░░░░░░░░░░░░ │      ║
║      │ ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░ │      ║
║      │ ░░░░░░░┌──────────────────────────────────────────┐░░░░░░░░░░░ │      ║
║      │ ░░░░░░░│                                          │░░░░░░░░░░░ │      ║
║      │ ░░░░░░░│          AI'S VISIBLE WINDOW             │░░░░░░░░░░░ │      ║
║      │ ░░░░░░░│                                          │░░░░░░░░░░░ │      ║
║      │ ░░░░░░░│   ┌────────────────────────────────┐     │░░░░░░░░░░░ │      ║
║      │ ░░░░░░░│   │ • Current conversation         │     │░░░░░░░░░░░ │      ║
║      │ ░░░░░░░│   │ • Files it has read            │     │░░░░░░░░░░░ │      ║
║      │ ░░░░░░░│   │ • Command outputs shown        │     │░░░░░░░░░░░ │      ║
║      │ ░░░░░░░│   │ • Errors you paste             │     │░░░░░░░░░░░ │      ║
║      │ ░░░░░░░│   │ • Your working directory       │     │░░░░░░░░░░░ │      ║
║      │ ░░░░░░░│   └────────────────────────────────┘     │░░░░░░░░░░░ │      ║
║      │ ░░░░░░░│                                          │░░░░░░░░░░░ │      ║
║      │ ░░░░░░░└──────────────────────────────────────────┘░░░░░░░░░░░ │      ║
║      │ ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░ │      ║
║      │ ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░ │      ║
║      └────────────────────────────────────────────────────────────────┘      ║
║                                                                              ║
║   ░░░ = Invisible to AI (your goals, preferences, constraints, history)      ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   ┌───────────────────────────────────────────────────────────────────┐      ║
║   │                                                                   │      ║
║   │  AI doesn't know:                AI knows:                        │      ║
║   │                                                                   │      ║
║   │  • Why you're building this      • What you've told it           │      ║
║   │  • What you tried before         • Files it has seen             │      ║
║   │  • Your constraints              • Current session               │      ║
║   │  • Your preferences              • Error messages shown          │      ║
║   │  • Future plans                  • Your project folder           │      ║
║   │                                                                   │      ║
║   └───────────────────────────────────────────────────────────────────┘      ║
║                                                                              ║
║  ┌──────────────────────────────────────────────────────────────────────┐    ║
║  │  More context = Better output.  Say what AI can't see.              │    ║
║  └──────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

## Reading This Drawing

**The Nested Boxes:** The outer box (filled with ░) represents YOUR ENTIRE WORLD—everything you know, everything that matters to your project. The inner clear box is AI'S VISIBLE WINDOW—the small slice AI can actually see.

**The Shaded Area (░):** This represents everything invisible to AI:
- Why you're building this project
- What you tried before that didn't work
- Your deadlines and constraints
- Your preferences for style, libraries, or approaches
- How this fits into a larger plan
- Company requirements or standards

AI cannot see any of this unless you tell it.

**The Clear Window:** What AI actually has access to:
- **Current conversation:** Everything said in this session
- **Files it has read:** Code you've shown or asked it to open
- **Command outputs:** Results from running commands
- **Errors you paste:** Error messages you share
- **Your working directory:** The folder structure it can see

**The Comparison Table:** The left column shows what's hidden. The right column shows what's visible. Notice the asymmetry—the hidden column is larger. Most of what matters is invisible by default.

**The Bottom Box (Key Rule):** "More context = Better output. Say what AI can't see." This is the actionable takeaway. When you provide context, AI performs better.

## What This Shows

AI only sees a small window of your world. Everything outside that window is invisible: your history, goals, constraints, preferences. Anything AI needs to know must be told or shown explicitly.

## Key Insight

When AI gets it wrong, often it's missing context. Ask yourself: "What do I know that AI doesn't?" Then say it.

## What This Means In Practice

Before giving a prompt, consider adding:
- **Why:** "I need this for a client presentation tomorrow"
- **Constraints:** "It must work with Python 3.8, that's what production uses"
- **Preferences:** "I prefer explicit code over clever one-liners"
- **History:** "I already tried using pandas but it was too slow"
- **Standards:** "We use camelCase for function names in this project"

You don't need to include everything every time. But when AI produces something unexpected, the gap is usually context you didn't provide.

---

[← Operations](04-operations.md) | [Next: Specificity →](06-specificity.md)
