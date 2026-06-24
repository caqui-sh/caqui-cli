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
  "dimensionPositiveQuestion": "[A positive success-oriented question targeting the ideal state of the subject, e.g., 'Are all expressions realistic and sane...']",
  "dimensionNegativeQuestion": "[A negative infraction-oriented question targeting deviations or violations, e.g., 'Do any expressions deviate...']",
  "dimensionSignal": [
    "[Unique positive aspect/metric representing constructive intent or clear information transmission]",
    "[Additional positive aspect reframed to introduce semantic diversity (pleonastic layering) without word repetition]"
  ],
  "dimensionNoise": [
    "[Unique negative aspect representing structural/cognitive friction, clutter, or unwanted variance]",
    "[Additional negative aspect reframed to introduce semantic diversity without word repetition. Use normalized compound noun format: Noun Adjunct + Plural Noun, e.g., 'Expectation deviations']"
  ],
  "dimensionFloor": [
    "[A discrete, checkable baseline constraint representing the entry-level pass/fail boundary]",
    "[Additional floor constraints, balancing outside-in (extrinsic) and inside-out (intrinsic) perspectives. Use distinct nouns/adjectives, e.g., 'Operational ranges', 'Acceptance bands', 'Inherent bounds', 'Essential limits']"
  ],
  "dimensionCeiling": [
    "[Optimization vector representing a Pushing Up constructive force (Self-Offensive), e.g., 'Expression sanity']",
    "[Optimization vector representing a Pulling Up attractive force (External-Offensive), e.g., 'Domain congruence']",
    "[Optimization vector representing an internal Resisting Down defensive force (Self-Defensive), e.g., 'Anomaly suppression']",
    "[Optimization vector representing an external Resisting Down defensive force (External-Defensive), e.g., 'Range retention']",
    "[Ensure ceiling options stay strictly within the dimension's atomic scope to maintain Mutual Exclusion (ME)]"
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

### B. Questions (Positive & Negative)
* **`dimensionPositiveQuestion`**: Succinctly defines the positive target state of success.
* **`dimensionNegativeQuestion`**: Succinctly defines the negative infraction state (the search target during auditing).

### C. Signal vs. Noise (Asymmetry, Plurality & Locality Heuristics)
* **Asymmetric Mapping**: The items in `dimensionSignal` and `dimensionNoise` must represent distinct, non-overlapping concepts and **never** be simple mirror-image negations of each other.
* **Semantic Diversity (Pleonastic Layering)**: Multiple options must be provided to capture different conceptual viewpoints of signal/noise.
* **Grammatical Normalization**: All options in `dimensionNoise` must follow the consistent compound noun format: `[Noun Adjunct] [Plural Noun]` (e.g., `"Expectation deviations"`, `"Invariant violations"`).
* **Locality Heuristics**: To ensure projection diversity without rigid schema constraints, both arrays should cover:
  - **Self/Intrinsic Aspects**: Focusing on internal soundness, logical viability, or local correctness (e.g., `"Constraint satisfaction"` or `"Logical contortions"`).
  - **External/Extrinsic Aspects**: Focusing on relationships to the environment, context, or external expectations (e.g., `"Contextual conformance"` or `"Expectation deviations"`).

### D. Floor (Inside-Out vs. Outside-In)
* **Perspective Balance**: The floor constraints must balance both **extrinsic** (outside-in, defining the valid space from the outside, e.g., `"Operational ranges"`, `"Acceptance bands"`) and **intrinsic** (inside-out, defining boundaries inherent to the core concept/essence of the expression, e.g., `"Inherent bounds"`, `"Essential limits"`).
* **No Word Repetition**: None of the nouns or adjectives in the `dimensionFloor` array may be repeated.

### E. Ceiling (The 1D Vector Forces Grid)
* **The Vector Grid**: The ceiling options must map onto four distinct vector directions:
  1. **Self-Offensive**: Pushing up toward the goal from the inside out (e.g., `"Expression sanity"`).
  2. **External-Offensive**: Pulling up toward the goal from the outside in (e.g., `"Domain congruence"`).
  3. **Self-Defensive**: Resisting internal degradation or anomalies from within (e.g., `"Anomaly suppression"`).
  4. **External-Defensive**: Resisting external drift or breach of contextual boundaries (e.g., `"Range retention"`).
* **Mutual Exclusion**: Ceiling options must be strictly bounded within the atomic scope of the target dimension, preventing conceptual creep into adjacent dimensions (such as *Reader Accessibility* or *Semantic Fidelity*).
