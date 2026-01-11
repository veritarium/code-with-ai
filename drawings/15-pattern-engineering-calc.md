# 15: Pattern — Engineering Calculation

```
╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║                    PATTERN: ENGINEERING CALCULATION                          ║
║                                                                              ║
║   Use this pattern when: Automating formulas, analysis, design checks        ║
║                                                                              ║
║  ┌──────────────────────────────────────────────────────────────────────┐    ║
║  │                                                                      │    ║
║  │   ┌─────────┐   ┌─────────┐   ┌─────────┐   ┌─────────┐   ┌───────┐ │    ║
║  │   │         │   │         │   │         │   │         │   │       │ │    ║
║  │   │  INPUT  │──►│VALIDATE │──►│ CALCULATE──►│  CHECK  │──►│OUTPUT │ │    ║
║  │   │         │   │         │   │         │   │         │   │       │ │    ║
║  │   └─────────┘   └─────────┘   └─────────┘   └─────────┘   └───────┘ │    ║
║  │                                                                      │    ║
║  │   Dimensions    Units ok?     Apply         Pass/Fail    Report     │    ║
║  │   Material      Range ok?     formulas      criteria     with       │    ║
║  │   Loads         Required      Step by       FoS, limits  units      │    ║
║  │                 fields?       step                                   │    ║
║  │                                                                      │    ║
║  └──────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   CALCULATION STRUCTURE:                                                     ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │                                                                     │    ║
║   │   ┌─────────────────────────────────────────────────────────────┐   │    ║
║   │   │                                                             │   │    ║
║   │   │   1. INPUTS         Define all variables with units         │   │    ║
║   │   │                     P = 1000  # N                           │   │    ║
║   │   │                     L = 2.5   # m                           │   │    ║
║   │   │                                                             │   │    ║
║   │   │   2. PROPERTIES     Material/section data                   │   │    ║
║   │   │                     E = 200e9  # Pa (steel)                 │   │    ║
║   │   │                     I = 8.33e-6  # m⁴                       │   │    ║
║   │   │                                                             │   │    ║
║   │   │   3. CALCULATION    Apply formula step by step              │   │    ║
║   │   │                     δ = (P * L³) / (48 * E * I)             │   │    ║
║   │   │                                                             │   │    ║
║   │   │   4. CONVERT        Output in useful units                  │   │    ║
║   │   │                     δ_mm = δ * 1000                         │   │    ║
║   │   │                                                             │   │    ║
║   │   │   5. CHECK          Compare to criteria                     │   │    ║
║   │   │                     limit = L / 360                         │   │    ║
║   │   │                     ok = δ < limit                          │   │    ║
║   │   │                                                             │   │    ║
║   │   └─────────────────────────────────────────────────────────────┘   │    ║
║   │                                                                     │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   COMMON CALCULATION TYPES:                                                  ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │                                                                     │    ║
║   │   ┌──────────────┬────────────────────────────────────────────┐    │    ║
║   │   │  TYPE        │   PROMPT TEMPLATE                          │    │    ║
║   │   ├──────────────┼────────────────────────────────────────────┤    │    ║
║   │   │              │                                            │    │    ║
║   │   │  Stress      │   "Calculate [stress type] given [loads]   │    │    ║
║   │   │              │    and [geometry]. Check against [σ_allow]"│    │    ║
║   │   │              │                                            │    │    ║
║   │   │  Deflection  │   "Calculate deflection of [beam type]     │    │    ║
║   │   │              │    with [load]. Check against L/[limit]"   │    │    ║
║   │   │              │                                            │    │    ║
║   │   │  Thermal     │   "Calculate expansion/heat transfer       │    │    ║
║   │   │              │    for [material] with ΔT = [value]"       │    │    ║
║   │   │              │                                            │    │    ║
║   │   │  Fluid       │   "Calculate [pressure drop / flow rate]   │    │    ║
║   │   │              │    for [pipe/channel] with [conditions]"   │    │    ║
║   │   │              │                                            │    │    ║
║   │   │  Sizing      │   "Size [component] for [load/flow] with   │    │    ║
║   │   │              │    factor of safety [FoS]"                 │    │    ║
║   │   │              │                                            │    │    ║
║   │   └──────────────┴────────────────────────────────────────────┘    │    ║
║   │                                                                     │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   MATERIAL PROPERTIES PATTERN:                                               ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │                                                                     │    ║
║   │   "Create a materials database with:                                │    ║
║   │    - Steel A36: E=200GPa, σy=250MPa, ρ=7850kg/m³                   │    ║
║   │    - Aluminum 6061-T6: E=69GPa, σy=276MPa, ρ=2700kg/m³             │    ║
║   │    - ...                                                            │    ║
║   │                                                                     │    ║
║   │    Function to lookup by name and return properties"                │    ║
║   │                                                                     │    ║
║   │   ┌─────────────────────────────────────────────────────────────┐   │    ║
║   │   │   material = get_material("Steel A36")                      │   │    ║
║   │   │   E = material.E      # 200e9 Pa                            │   │    ║
║   │   │   σy = material.σy    # 250e6 Pa                            │   │    ║
║   │   └─────────────────────────────────────────────────────────────┘   │    ║
║   │                                                                     │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   BUILD SEQUENCE (Beam Calculator Example):                                  ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │                                                                     │    ║
║   │   1. CORE FORMULA                                                   │    ║
║   │      "Create function beam_deflection(P, L, E, I) that returns     │    ║
║   │       max deflection using δ = PL³/48EI for simply supported beam" │    ║
║   │                                                                     │    ║
║   │   2. ADD UNITS HANDLING                                             │    ║
║   │      "Take inputs in mm and kN, convert internally to m and N"     │    ║
║   │                                                                     │    ║
║   │   3. ADD SECTION CALCULATION                                        │    ║
║   │      "Add function for I of rectangular section: bh³/12"           │    ║
║   │                                                                     │    ║
║   │   4. ADD MATERIAL LOOKUP                                            │    ║
║   │      "Add material database, lookup E by material name"            │    ║
║   │                                                                     │    ║
║   │   5. ADD LIMIT CHECK                                                │    ║
║   │      "Check if deflection exceeds L/360, return pass/fail"         │    ║
║   │                                                                     │    ║
║   │   6. ADD STRESS CHECK                                               │    ║
║   │      "Calculate max stress, check against yield with FoS=1.5"      │    ║
║   │                                                                     │    ║
║   │   7. OUTPUT REPORT                                                  │    ║
║   │      "Print summary: inputs, results, pass/fail, with units"       │    ║
║   │                                                                     │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║  ═══════════════════════════════════════════════════════════════════════     ║
║                                                                              ║
║   OUTPUT FORMAT:                                                             ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │                                                                     │    ║
║   │   ┌─────────────────────────────────────────────────────────────┐   │    ║
║   │   │  BEAM ANALYSIS RESULTS                                      │   │    ║
║   │   │  ═══════════════════════                                    │   │    ║
║   │   │                                                             │   │    ║
║   │   │  Inputs:                                                    │   │    ║
║   │   │    Load:        10.0 kN                                     │   │    ║
║   │   │    Span:        3000 mm                                     │   │    ║
║   │   │    Section:     100 x 200 mm                                │   │    ║
║   │   │    Material:    Steel A36                                   │   │    ║
║   │   │                                                             │   │    ║
║   │   │  Results:                                                   │   │    ║
║   │   │    Deflection:  2.81 mm  (limit: 8.33 mm)     ✓ PASS        │   │    ║
║   │   │    Stress:      112 MPa  (allow: 167 MPa)     ✓ PASS        │   │    ║
║   │   │    FoS:         2.23                                        │   │    ║
║   │   │                                                             │   │    ║
║   │   └─────────────────────────────────────────────────────────────┘   │    ║
║   │                                                                     │    ║
║   │   "Format results as a clear report with units and pass/fail"       │    ║
║   │                                                                     │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
║   ┌─────────────────────────────────────────────────────────────────────┐    ║
║   │  KEY RULE: Always include units. Always check against limits.       │    ║
║   └─────────────────────────────────────────────────────────────────────┘    ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

## What This Shows

Engineering calculations: Input → Validate → Calculate → Check → Output. Always track units. Always check results against limits (deflection limits, yield stress, factor of safety). Build step by step: core formula first, then add units handling, material lookup, checks, and reporting.

## Key Insight

The formulas you already know become reusable tools. Build once, use forever. Let AI handle the code—you focus on the engineering.

---

[← Testing Pattern](14-pattern-testing.md) | [Home](../README.md)
