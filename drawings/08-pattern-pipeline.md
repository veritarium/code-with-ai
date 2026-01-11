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

## Reading This Drawing

**The Four Stages (Top Row):** This is the core pattern—four boxes connected by arrows:
- **INPUT:** Where data comes from. Could be CSV files, JSON, API responses, database queries. The source material.
- **CLEAN:** Data is never perfect. This stage removes bad data, fixes types (strings that should be numbers), handles missing values.
- **PROCESS:** The actual work. Calculate new values, transform units, aggregate results, apply formulas.
- **OUTPUT:** Where results go. Reports, charts, exported files, database updates.

**The Build Sequence:** How to construct this pattern step by step. Each numbered item is one prompt:
1. **INPUT:** "Read measurements.csv, show first 5 rows and column types" — Start by understanding what you have.
2. **CLEAN:** "Remove rows where pressure is negative or missing" — Fix data quality issues.
3. **PROCESS:** "Add column: stress = force / area" and "Group by material, calculate mean and max stress" — Do the calculations.
4. **OUTPUT:** "Create bar chart of max stress by material" and "Save results to stress_analysis.csv" — Generate deliverables.

Each prompt is testable. You verify each stage works before moving to the next.

**The Variations Section:** Three common modifications to the basic pattern:

**Multi-input:** When data comes from multiple sources (CSV + API), you add a MERGE step that combines them before processing. Example: joining sensor data from a file with calibration data from an API.

**Multi-output:** When one process produces multiple deliverables. After processing, the flow splits—one branch creates a chart, another creates a report. Same data, different formats.

**Loop:** When you need to repeat until a condition is met. Process → Check → if not done, loop back. Example: iterating through calibration until error is below threshold.

## What This Shows

Data pipeline: Input → Clean → Process → Output. Most data tasks follow this shape. Build each stage separately, verify it works, then connect. Variations handle multiple inputs, multiple outputs, or loops.

## Key Insight

Recognize this pattern and you can build any data processing task by filling in the stages.

## What This Means In Practice

When you have a data task:
1. Identify your input source(s)
2. List what cleaning is needed
3. Define the calculations/transformations
4. Specify the output format(s)

Then build each stage with its own prompt, test it, and connect them. A complex analysis becomes four simple prompts.

---

[← Iteration](07-iteration.md) | [Next: Web App Pattern →](09-pattern-webapp.md)
