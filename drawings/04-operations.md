# 04: Operations

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║                              OPERATIONS                                      ║
║                                                                              ║
║  Everything you do is one of these six operations:                           ║
║                                                                              ║
║  ┌────────────────────────────────────────────────────────────────────────┐  ║
║  │                                                                        │  ║
║  │   CREATE        "Create [file] that [does what]"                       │  ║
║  │                                                                        │  ║
║  │   ┌─────────┐         ┌─────────┐                                      │  ║
║  │   │ Intent  │────────►│  File   │                                      │  ║
║  │   └─────────┘   AI    └─────────┘                                      │  ║
║  │                                                                        │  ║
║  └────────────────────────────────────────────────────────────────────────┘  ║
║                                                                              ║
║  ┌────────────────────────────────────────────────────────────────────────┐  ║
║  │                                                                        │  ║
║  │   READ          "Show me [file]" / "Explain [thing]"                   │  ║
║  │                                                                        │  ║
║  │   ┌─────────┐         ┌─────────┐                                      │  ║
║  │   │  File   │────────►│ Under-  │                                      │  ║
║  │   └─────────┘   AI    │ standing│                                      │  ║
║  │                       └─────────┘                                      │  ║
║  └────────────────────────────────────────────────────────────────────────┘  ║
║                                                                              ║
║  ┌────────────────────────────────────────────────────────────────────────┐  ║
║  │                                                                        │  ║
║  │   EDIT          "In [file], change [what] to [what]"                   │  ║
║  │                                                                        │  ║
║  │   ┌─────────┐         ┌─────────┐                                      │  ║
║  │   │ File +  │────────►│ Updated │                                      │  ║
║  │   │ Change  │   AI    │  File   │                                      │  ║
║  │   └─────────┘         └─────────┘                                      │  ║
║  └────────────────────────────────────────────────────────────────────────┘  ║
║                                                                              ║
║  ┌────────────────────────────────────────────────────────────────────────┐  ║
║  │                                                                        │  ║
║  │   RUN           "Run [file]" / "Install [package]"                     │  ║
║  │                                                                        │  ║
║  │   ┌─────────┐         ┌─────────┐                                      │  ║
║  │   │ Command │────────►│ Output  │                                      │  ║
║  │   └─────────┘ Execute └─────────┘                                      │  ║
║  │                                                                        │  ║
║  └────────────────────────────────────────────────────────────────────────┘  ║
║                                                                              ║
║  ┌────────────────────────────────────────────────────────────────────────┐  ║
║  │                                                                        │  ║
║  │   FIX           "[error message]. Fix it."                             │  ║
║  │                                                                        │  ║
║  │   ┌─────────┐         ┌─────────┐                                      │  ║
║  │   │  Error  │────────►│  Fixed  │                                      │  ║
║  │   └─────────┘   AI    │  Code   │                                      │  ║
║  │                       └─────────┘                                      │  ║
║  └────────────────────────────────────────────────────────────────────────┘  ║
║                                                                              ║
║  ┌────────────────────────────────────────────────────────────────────────┐  ║
║  │                                                                        │  ║
║  │   EXTEND        "Add [feature] to [file]"                              │  ║
║  │                                                                        │  ║
║  │   ┌─────────┐         ┌─────────┐                                      │  ║
║  │   │ Existing│────────►│ Enhanced│                                      │  ║
║  │   │ + New   │   AI    │  Code   │                                      │  ║
║  │   └─────────┘         └─────────┘                                      │  ║
║  └────────────────────────────────────────────────────────────────────────┘  ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

## Reading This Drawing

**The Six Boxes:** Each box represents one type of operation. Together, these six cover everything you'll ever do when building software with AI. There is no seventh operation.

**CREATE (First Box):**
- Pattern: `"Create [file] that [does what]"`
- Flow: Intent → AI → File
- Use when: You need something that doesn't exist yet
- Example: "Create a Python script that converts CSV to JSON"

**READ (Second Box):**
- Pattern: `"Show me [file]"` or `"Explain [thing]"`
- Flow: File → AI → Understanding
- Use when: You need to understand existing code or have AI explain something
- Example: "Show me the main.py file" or "Explain how this function works"

**EDIT (Third Box):**
- Pattern: `"In [file], change [what] to [what]"`
- Flow: File + Change → AI → Updated File
- Use when: Something exists but needs modification
- Example: "In calculate.py, change the interest rate from 5% to 7%"

**RUN (Fourth Box):**
- Pattern: `"Run [file]"` or `"Install [package]"`
- Flow: Command → Execute → Output
- Use when: You want to execute code or terminal commands
- Example: "Run the tests" or "Install pandas"

**FIX (Fifth Box):**
- Pattern: `"[error message]. Fix it."`
- Flow: Error → AI → Fixed Code
- Use when: Something broke and you have an error message
- Example: "TypeError: cannot add str and int. Fix it."

**EXTEND (Sixth Box):**
- Pattern: `"Add [feature] to [file]"`
- Flow: Existing + New → AI → Enhanced Code
- Use when: Code works but needs more capability
- Example: "Add error handling for missing files to the parser"

**The Arrow Pattern:** Every box shows input → transformation → output. AI sits in the middle, transforming what you have into what you need.

## What This Shows

Six operations. That's the entire vocabulary. Create makes new things. Read shows you things. Edit changes things. Run executes things. Fix repairs things. Extend adds to things.

## Key Insight

Every prompt you ever write is one of these six. Master these patterns and you can express any intent.

## What This Means In Practice

When you're stuck, ask: "Which operation do I need?"
- Nothing exists yet? → CREATE
- Need to understand something? → READ
- Something's wrong with existing code? → EDIT
- Need to see if it works? → RUN
- Got an error? → FIX
- Works but needs more? → EXTEND

This mental framework keeps you moving. You always know what kind of prompt to write next.

---

[← Decomposition](03-decomposition.md) | [Next: Context →](05-context.md)
