# Prototype Specification Design: Atomic Dimensions (atomic_dimension.prototype.md)

This document defines the technical schema, formatting rules, and conceptual constraints for creating and managing atomic dimension specifications in JSON prototype format.

---

## 1. JSON Specification Template

Every atomic dimension specification prototype must be written as a valid JSON object matching the following skeleton:

```json
{
  "dimensionName": "[Capitalized Title Case string, e.g., 'Expression Validity']",
  "dimensionKind": "ATOMIC",
  "dimensionPillar": "[Uppercase Enum matching the parent pillar, e.g., 'STRUCTURAL_ARCHITECTURE']",
  "dimensionNature": [
    "[Uppercase Enum representing the technical natures, e.g., 'OBJECTIVE_DISCRETE', 'SUBJECTIVE_SPECTRUM']"
  ],
  "dimensionSubject": "[Sentence case string defining the generic abstract universal target of the pattern match, e.g., 'Information expressions']",
  "dimensionSignal": [
    "[Unique positive aspect/metric representing constructive intent or clear information transmission]",
    "[Additional positive aspect reframed to introduce semantic diversity (pleonastic layering) without word repetition]"
  ],
  "dimensionNoise": [
    "[Unique negative aspect representing structural/cognitive friction, clutter, or unwanted variance]",
    "[Additional negative aspect reframed to introduce semantic diversity without word repetition. Use a grammatically normalized format matching the signal list (e.g., matching adjectives like 'Absurd', or compound nouns like 'Invariant violations')]"
  ],
  "dimensionFloor": [
    "[A discrete, checkable baseline constraint representing the entry-level pass/fail boundary]",
    "[Additional floor constraints, balancing outside-in (extrinsic) and inside-out (intrinsic) perspectives. Use distinct nouns/adjectives, e.g., 'Operational ranges', 'Acceptance bands', 'Inherent bounds', 'Essential limits']"
  ],
  "dimensionDynamics": [
    "[Optimization vector representing a Pushing Up constructive force (Self-Offensive), e.g., 'Coherence amplification']",
    "[Optimization vector representing a Pulling Up attractive force (External-Offensive), e.g., 'External integration']",
    "[Optimization vector representing an internal Resisting Down defensive force (Self-Defensive), e.g., 'Anomaly suppression']",
    "[Optimization vector representing an external Resisting Down defensive force (External-Defensive), e.g., 'Boundary enforcement']",
    "[Ensure dynamics options stay strictly within the dimension's atomic scope to maintain Mutual Exclusion (ME)]"
  ]
}
```

---

## 2. Formatting & Design Constraints

### A. Field-Level Rules
* **`dimensionName`**: Must be formatted in Title Case.
* **`dimensionKind`**: Must be the string `"ATOMIC"`.
* **`dimensionPillar`**: Must be an uppercase enum (using underscores, e.g., `STRUCTURAL_ARCHITECTURE`) matching the parent pillar.
* **`dimensionNature`**: An array of uppercase enums (e.g., `OBJECTIVE_DISCRETE`, `SUBJECTIVE_SPECTRUM`) representing the technical natures of the evaluation.
* **`dimensionSubject`**: Sentence case string describing the target pattern match. Use a qualifier where appropriate (e.g., `"Information expressions"`).

### B. Signal vs. Noise (Asymmetry, Plurality & Locality Heuristics)
* **State Quality & Composition**: Signal and noise represent the relative composition and quality of the expression *within* the viable space. They describe what is present in the static state.
* **Asymmetric Mapping**: The items in `dimensionSignal` and `dimensionNoise` must represent distinct, non-overlapping concepts and **never** be simple mirror-image negations of each other.
* **Semantic Diversity (Pleonastic Layering)**: Multiple options must be provided to capture different conceptual viewpoints of signal/noise.
* **Grammatical Normalization**: All options in `dimensionNoise` must follow a consistent grammatical format that aligns with the projection style of `dimensionSignal` to ensure logical symmetry:
  - **Adjective-based style**: If signals are formulated as adjectives, noises must also be adjectives (e.g., `"Absurd"`, `"Fallacious"`, `"Implausible"`).
  - **Noun-based style**: If signals are formulated as nouns, noises must follow the consistent compound noun format: `[Noun Adjunct] [Plural Noun]` (e.g., `"Expectation deviations"`, `"Invariant violations"`).
* **Locality Heuristics**: To ensure projection diversity without rigid schema constraints, both arrays should cover:
  - **Self/Intrinsic Aspects**: Focusing on internal soundness, logical viability, or local correctness (e.g., `"Constraint satisfaction"` or `"Logical contortions"`).
  - **External/Extrinsic Aspects**: Focusing on relationships to the environment, context, or external expectations (e.g., `"Contextual conformance"` or `"Expectation deviations"`).
  - **Purely Intrinsic Focus**: For universal, context-independent, or highly abstract atomic dimensions (like *Expression Validity*), the specification may choose to omit extrinsic relations entirely. Emphasizing a **purely intrinsic nature** (focusing strictly on internal logical structure, feasibility, sanity, and viability) preserves universality and prevents overlap with environment-specific schema/data constraints (which are handled by *Notation Conformance* or *Data Validity*).

### C. Floor (Inside-Out vs. Outside-In)
* **Perspective Balance**: The floor constraints must balance both **extrinsic** (outside-in, defining the valid space from the outside, e.g., `"Operational ranges"`, `"Acceptance bands"`) and **intrinsic** (inside-out, defining boundaries inherent to the core concept/essence of the expression, e.g., `"Inherent bounds"`, `"Essential limits"`).
* **No Word Repetition**: None of the nouns or adjectives in the `dimensionFloor` array may be repeated.

### D. Dynamics (The Vector Forces Grid)
* **The Active Vector Forces**: The dynamics options represent active steering forces, corrective engines, and directional pressures. They must be formulated as action-oriented or process-based concepts (using nouns of action, active processes, or gerunds) rather than static states or qualitative properties.
* **The Vector Grid**: The dynamics options must map onto four distinct vector directions:
  1. **Self-Offensive**: Pushing up toward the goal from the inside out (e.g., `"Coherence amplification"`).
  2. **External-Offensive**: Pulling up toward the goal from the outside in (e.g., `"External integration"`).
  3. **Self-Defensive**: Resisting internal degradation or anomalies from within (e.g., `"Anomaly suppression"`).
  4. **External-Defensive**: Resisting external drift or breach of contextual boundaries (e.g., `"Boundary enforcement"`).
* **Mutual Exclusion**: Dynamics options must be strictly bounded within the atomic scope of the target dimension, preventing conceptual creep into adjacent dimensions (such as *Reader Accessibility* or *Semantic Fidelity*).
