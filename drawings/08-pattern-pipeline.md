# 08: Pattern — Data Pipeline

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║                         PATTERN: DATA PIPELINE                               ║
║                                                                              ║
║   Use this pattern when: Processing data from input to output                ║
║                                                                              ║
║  ┌──────────────────────────────────────────────────────────────────────┐    ║
║  │                                                                      │    ║
║  │   ┌─────────┐    ┌─────────┐    ┌─────────┐    ┌─────────┐          │    ║
║  │   │         │    │         │    │         │    │         │          │    ║
║  │   │  INPUT  │───►│  CLEAN  │───►│ PROCESS │───►│ OUTPUT  │          │    ║
║  │   │         │    │         │    │         │    │         │          │    ║
║  │   └─────────┘    └─────────┘    └─────────┘    └─────────┘          │    ║
║  │                                                                      │    ║
║  │   CSV, JSON,     Remove bad     Calculate,     Report,               │    ║
║  │   API, DB        data, fix      transform,     chart,                │    ║
║  │                  types          aggregate      export                │    ║
║  │                                                                      │    ║
║  └──────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   BUILD SEQUENCE (one prompt each):                                          ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │                                                                     │    ║
║   │   1. INPUT                                                          │    ║
║   │      "Read measurements.csv, show first 5 rows and column types"    │    ║
║   │                                                                     │    ║
║   │   2. CLEAN                                                          │    ║
║   │      "Remove rows where pressure is negative or missing"            │    ║
║   │                                                                     │    ║
║   │   3. PROCESS                                                        │    ║
║   │      "Add column: stress = force / area"                            │    ║
║   │      "Group by material, calculate mean and max stress"             │    ║
║   │                                                                     │    ║
║   │   4. OUTPUT                                                         │    ║
║   │      "Create bar chart of max stress by material"                   │    ║
║   │      "Save results to stress_analysis.csv"                          │    ║
║   │                                                                     │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   VARIATIONS:                                                                ║
║                                                                              ║
║   ┌─────────────┐    ┌─────────────────────────────────────────────────┐     ║
║   │ Multi-input │    │   ┌─────┐                                       │     ║
║   │             │    │   │ CSV │──┐                                    │     ║
║   │             │    │   └─────┘  │    ┌───────┐    ┌────────┐         │     ║
║   │             │    │            ├───►│ MERGE │───►│ OUTPUT │         │     ║
║   │             │    │   ┌─────┐  │    └───────┘    └────────┘         │     ║
║   │             │    │   │ API │──┘                                    │     ║
║   │             │    │   └─────┘                                       │     ║
║   └─────────────┘    └─────────────────────────────────────────────────┘     ║
║                                                                              ║
║   ┌─────────────┐    ┌─────────────────────────────────────────────────┐     ║
║   │ Multi-output│    │                          ┌───────┐              │     ║
║   │             │    │                     ┌───►│ Chart │              │     ║
║   │             │    │   ┌───────┐         │    └───────┘              │     ║
║   │             │    │   │PROCESS│─────────┤                           │     ║
║   │             │    │   └───────┘         │    ┌───────┐              │     ║
║   │             │    │                     └───►│ Report│              │     ║
║   │             │    │                          └───────┘              │     ║
║   └─────────────┘    └─────────────────────────────────────────────────┘     ║
║                                                                              ║
║   ┌─────────────┐    ┌─────────────────────────────────────────────────┐     ║
║   │ Loop        │    │                     ▲                           │     ║
║   │             │    │   ┌───────┐    ┌────┴────┐    ┌───────┐         │     ║
║   │             │    │   │ INPUT │───►│ PROCESS │───►│ CHECK │──► Done │     ║
║   │             │    │   └───────┘    └─────────┘    └───┬───┘         │     ║
║   │             │    │                                   │ Not yet     │     ║
║   │             │    │                                   └─────────────│     ║
║   └─────────────┘    └─────────────────────────────────────────────────┘     ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

## What This Shows

Data pipeline: Input → Clean → Process → Output. Most data tasks follow this shape. Build each stage separately, verify it works, then connect. Variations handle multiple inputs, multiple outputs, or loops.

## Key Insight

Recognize this pattern and you can build any data processing task by filling in the stages.

---

[← Iteration](07-iteration.md) | [Next: Web App Pattern →](09-pattern-webapp.md)
