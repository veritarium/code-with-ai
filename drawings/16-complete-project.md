# 16: Complete Project Walkthrough

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║                       COMPLETE PROJECT WALKTHROUGH                           ║
║                                                                              ║
║   How everything fits together: Idea → Working Software                      ║
║                                                                              ║
║  ┌──────────────────────────────────────────────────────────────────────┐    ║
║  │                                                                      │    ║
║  │   ┌──────┐   ┌──────┐   ┌──────┐   ┌──────┐   ┌──────┐   ┌──────┐   │    ║
║  │   │      │   │      │   │      │   │      │   │      │   │      │   │    ║
║  │   │DEFINE│──►│BREAK │──►│BUILD │──►│ TEST │──►│REFINE│──►│ USE  │   │    ║
║  │   │      │   │ DOWN │   │      │   │      │   │      │   │      │   │    ║
║  │   └──────┘   └──────┘   └──────┘   └──────┘   └──────┘   └──────┘   │    ║
║  │                                                                      │    ║
║  │   What do    What       One piece  Does it   Fix        Done!       │    ║
║  │   I need?    pieces?    at a time  work?     issues                 │    ║
║  │                                                                      │    ║
║  └──────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   EXAMPLE: Build a Bolt Stress Calculator                                    ║
║                                                                              ║
║  ┌──────────────────────────────────────────────────────────────────────┐    ║
║  │                                                                      │    ║
║  │   PHASE 1: DEFINE                                          Drawing 3│    ║
║  │   ════════════════                                    (Decomposition)│    ║
║  │                                                                      │    ║
║  │   "I need a tool that:                                               │    ║
║  │    - Takes bolt size, material, and applied load                     │    ║
║  │    - Calculates tensile stress in the bolt                           │    ║
║  │    - Compares to allowable stress                                    │    ║
║  │    - Tells me if the bolt is adequate"                               │    ║
║  │                                                                      │    ║
║  │   ┌─────────────────────────────────────────────────────────────┐    │    ║
║  │   │  Break into pieces:                                         │    │    ║
║  │   │                                                             │    │    ║
║  │   │  ┌─────────────┐                                            │    │    ║
║  │   │  │ Bolt        │                                            │    │    ║
║  │   │  │ Calculator  │                                            │    │    ║
║  │   │  └──────┬──────┘                                            │    │    ║
║  │   │         │                                                   │    │    ║
║  │   │    ┌────┴────┬────────────┬────────────┐                    │    │    ║
║  │   │    ▼         ▼            ▼            ▼                    │    │    ║
║  │   │ ┌──────┐ ┌──────┐   ┌──────────┐ ┌──────────┐               │    │    ║
║  │   │ │ Bolt │ │Stress│   │ Material │ │  Check   │               │    │    ║
║  │   │ │ Data │ │ Calc │   │  Lookup  │ │ & Report │               │    │    ║
║  │   │ └──────┘ └──────┘   └──────────┘ └──────────┘               │    │    ║
║  │   │                                                             │    │    ║
║  │   └─────────────────────────────────────────────────────────────┘    │    ║
║  │                                                                      │    ║
║  └──────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ┌──────────────────────────────────────────────────────────────────────┐    ║
║  │                                                                      │    ║
║  │   PHASE 2: BUILD PIECE BY PIECE                           Drawing 10│    ║
║  │   ══════════════════════════════                  (Build Incremental)│    ║
║  │                                                                      │    ║
║  │   Step 1: Bolt data                                                  │    ║
║  │   ┌─────────────────────────────────────────────────────────────┐    │    ║
║  │   │  "Create a dictionary of bolt sizes with tensile area:      │    │    ║
║  │   │   M6: 20.1 mm², M8: 36.6 mm², M10: 58.0 mm², M12: 84.3 mm²" │    │    ║
║  │   └─────────────────────────────────────────────────────────────┘    │    ║
║  │                           │                                          │    ║
║  │                           ▼                                          │    ║
║  │                    ┌────────────┐                                    │    ║
║  │                    │ Test: show │                                    │    ║
║  │                    │ M10 area   │ → 58.0 ✓                           │    ║
║  │                    └────────────┘                                    │    ║
║  │                                                                      │    ║
║  │   Step 2: Stress calculation                                         │    ║
║  │   ┌─────────────────────────────────────────────────────────────┐    │    ║
║  │   │  "Create function calc_stress(force_N, area_mm2) that       │    │    ║
║  │   │   returns stress in MPa using σ = F/A"                      │    │    ║
║  │   └─────────────────────────────────────────────────────────────┘    │    ║
║  │                           │                                          │    ║
║  │                           ▼                                          │    ║
║  │                    ┌────────────┐                                    │    ║
║  │                    │ Test: 1000N│                                    │    ║
║  │                    │ / 58 mm²   │ → 17.2 MPa ✓                       │    ║
║  │                    └────────────┘                                    │    ║
║  │                                                                      │    ║
║  │   Step 3: Material properties                                        │    ║
║  │   ┌─────────────────────────────────────────────────────────────┐    │    ║
║  │   │  "Add material data: Grade 8.8 σy=640MPa, Grade 10.9        │    │    ║
║  │   │   σy=940MPa. Function to get allowable = σy / FoS"          │    │    ║
║  │   └─────────────────────────────────────────────────────────────┘    │    ║
║  │                           │                                          │    ║
║  │                           ▼                                          │    ║
║  │                    ┌────────────┐                                    │    ║
║  │                    │ Test: 8.8  │                                    │    ║
║  │                    │ FoS=2      │ → 320 MPa ✓                        │    ║
║  │                    └────────────┘                                    │    ║
║  │                                                                      │    ║
║  │   Step 4: Combine + Check                                            │    ║
║  │   ┌─────────────────────────────────────────────────────────────┐    │    ║
║  │   │  "Create check_bolt(size, grade, force_kN, fos) that        │    │    ║
║  │   │   returns stress, allowable, and PASS/FAIL"                 │    │    ║
║  │   └─────────────────────────────────────────────────────────────┘    │    ║
║  │                           │                                          │    ║
║  │                           ▼                                          │    ║
║  │                    ┌────────────┐                                    │    ║
║  │                    │ Test: M10  │                                    │    ║
║  │                    │ 8.8, 15kN  │ → 259MPa < 320MPa PASS ✓           │    ║
║  │                    └────────────┘                                    │    ║
║  │                                                                      │    ║
║  └──────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ┌──────────────────────────────────────────────────────────────────────┐    ║
║  │                                                                      │    ║
║  │   PHASE 3: TEST & DEBUG                            Drawings 13 & 14 │    ║
║  │   ═════════════════════                         (Debugging & Testing)│    ║
║  │                                                                      │    ║
║  │   ┌─────────────────────────────────────────────────────────────┐    │    ║
║  │   │  "Write tests for check_bolt:                               │    │    ║
║  │   │   - Normal case: M10, 8.8, 10kN → PASS                      │    │    ║
║  │   │   - Edge case: exactly at limit → PASS                       │    │    ║
║  │   │   - Fail case: M6, 8.8, 20kN → FAIL                         │    │    ║
║  │   │   - Invalid: unknown bolt size → error"                      │    │    ║
║  │   └─────────────────────────────────────────────────────────────┘    │    ║
║  │                           │                                          │    ║
║  │                           ▼                                          │    ║
║  │   ┌─────────────────────────────────────────────────────────────┐    │    ║
║  │   │  "Run tests"                                                 │    │    ║
║  │   │                                                             │    │    ║
║  │   │   ✓ Pass  ✓ Pass  ✓ Pass  ✗ FAIL - no error handling       │    │    ║
║  │   └─────────────────────────────────────────────────────────────┘    │    ║
║  │                           │                                          │    ║
║  │                           ▼                                          │    ║
║  │   ┌─────────────────────────────────────────────────────────────┐    │    ║
║  │   │  "Add error handling for unknown bolt size. Run tests again"│    │    ║
║  │   │                                                             │    │    ║
║  │   │   ✓ Pass  ✓ Pass  ✓ Pass  ✓ Pass                           │    │    ║
║  │   └─────────────────────────────────────────────────────────────┘    │    ║
║  │                                                                      │    ║
║  └──────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ┌──────────────────────────────────────────────────────────────────────┐    ║
║  │                                                                      │    ║
║  │   PHASE 4: REFINE & EXTEND                          Drawings 6 & 7  │    ║
║  │   ════════════════════════                    (Specificity/Iteration)│    ║
║  │                                                                      │    ║
║  │   ┌─────────────────────────────────────────────────────────────┐    │    ║
║  │   │  "Add formatted output report with all values and units"    │    │    ║
║  │   └─────────────────────────────────────────────────────────────┘    │    ║
║  │                                                                      │    ║
║  │   ┌─────────────────────────────────────────────────────────────┐    │    ║
║  │   │  "Add more bolt sizes: M14, M16, M20"                       │    │    ║
║  │   └─────────────────────────────────────────────────────────────┘    │    ║
║  │                                                                      │    ║
║  │   ┌─────────────────────────────────────────────────────────────┐    │    ║
║  │   │  "Add shear stress check for bolts in shear"                │    │    ║
║  │   └─────────────────────────────────────────────────────────────┘    │    ║
║  │                                                                      │    ║
║  └──────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ┌──────────────────────────────────────────────────────────────────────┐    ║
║  │                                                                      │    ║
║  │   PHASE 5: DONE                                                      │    ║
║  │   ══════════                                                         │    ║
║  │                                                                      │    ║
║  │   ┌─────────────────────────────────────────────────────────────┐    │    ║
║  │   │                                                             │    │    ║
║  │   │   BOLT STRESS CHECK                                         │    │    ║
║  │   │   ══════════════════                                        │    │    ║
║  │   │                                                             │    │    ║
║  │   │   Input:                                                    │    │    ║
║  │   │     Bolt:      M10                                          │    │    ║
║  │   │     Grade:     8.8                                          │    │    ║
║  │   │     Load:      15.0 kN                                      │    │    ║
║  │   │     FoS:       2.0                                          │    │    ║
║  │   │                                                             │    │    ║
║  │   │   Calculation:                                              │    │    ║
║  │   │     Area:      58.0 mm²                                     │    │    ║
║  │   │     Stress:    258.6 MPa                                    │    │    ║
║  │   │     Yield:     640.0 MPa                                    │    │    ║
║  │   │     Allowable: 320.0 MPa                                    │    │    ║
║  │   │                                                             │    │    ║
║  │   │   Result:      ✓ PASS (σ < σ_allow)                         │    │    ║
║  │   │     Margin:    19% under allowable                          │    │    ║
║  │   │                                                             │    │    ║
║  │   └─────────────────────────────────────────────────────────────┘    │    ║
║  │                                                                      │    ║
║  │   Tool built. Use it. Extend it. Build the next one.                 │    ║
║  │                                                                      │    ║
║  └──────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

## Reading This Drawing

**The Six-Phase Flow (Top):** Every project goes through these phases:
- **DEFINE:** What do I need? Clarify the goal before starting.
- **BREAK DOWN:** What pieces? Decompose into manageable parts (Drawing 03).
- **BUILD:** One piece at a time. Each piece is one prompt (Drawing 10).
- **TEST:** Does it work? Verify each piece (Drawing 14).
- **REFINE:** Fix issues. Iterate until correct (Drawing 07).
- **USE:** Done! Deploy and use the tool.

**Phase 1: DEFINE (with Decomposition Tree):** The example project: "Build a Bolt Stress Calculator"

First, break it into pieces:
```
Bolt Calculator
    ├── Bolt Data
    ├── Stress Calc
    ├── Material Lookup
    └── Check & Report
```

Four components, each buildable independently. This uses the decomposition pattern from Drawing 03.

**Phase 2: BUILD PIECE BY PIECE:** Four steps, each with a prompt and test:

**Step 1 - Bolt data:**
- Prompt: "Create a dictionary of bolt sizes with tensile area: M6: 20.1 mm², M8: 36.6 mm²..."
- Test: show M10 area → 58.0 ✓

**Step 2 - Stress calculation:**
- Prompt: "Create function calc_stress(force_N, area_mm2) that returns stress in MPa using σ = F/A"
- Test: 1000N / 58 mm² → 17.2 MPa ✓

**Step 3 - Material properties:**
- Prompt: "Add material data: Grade 8.8 σy=640MPa, Grade 10.9 σy=940MPa. Function to get allowable = σy / FoS"
- Test: 8.8 with FoS=2 → 320 MPa ✓

**Step 4 - Combine + Check:**
- Prompt: "Create check_bolt(size, grade, force_kN, fos) that returns stress, allowable, and PASS/FAIL"
- Test: M10 8.8, 15kN → 259MPa < 320MPa PASS ✓

Each step builds on the last. Each has its own test.

**Phase 3: TEST & DEBUG:** Write formal tests covering edge cases:
- Normal case: M10, 8.8, 10kN → PASS
- Edge case: exactly at limit → PASS
- Fail case: M6, 8.8, 20kN → FAIL
- Invalid: unknown bolt size → error

When a test fails (no error handling for unknown bolt), fix it and retest. This uses the debugging pattern from Drawing 13.

**Phase 4: REFINE & EXTEND:** Once it works, make it better:
- "Add formatted output report with all values and units"
- "Add more bolt sizes: M14, M16, M20"
- "Add shear stress check for bolts in shear"

Each refinement is optional. Stop when you have what you need.

**Phase 5: DONE:** The final output shows a professional report with all inputs, calculations, results, and pass/fail indicators. A complete tool built through the process.

The closing statement: "Tool built. Use it. Extend it. Build the next one."

## What This Shows

A complete project from idea to working tool. Five phases: Define → Break Down → Build Piece by Piece → Test & Debug → Refine. Each phase uses concepts from earlier drawings. The example shows a real engineering calculator built step by step.

## Key Insight

Every project follows this pattern. The size changes, not the process. A small calculator or a large system—same phases, same approach.

## What This Means In Practice

To build any project:
1. Write down what you need (one paragraph)
2. Break it into pieces (tree diagram)
3. Build smallest piece first, test it
4. Build next piece, test combined
5. Continue until all pieces work together
6. Add polish (formatting, edge cases, documentation)

The bolt calculator example took about 10-15 prompts from start to finish. Larger projects take more prompts but follow the same pattern.

---

[← Engineering Calculation](15-pattern-engineering-calc.md) | [Home](../README.md)
