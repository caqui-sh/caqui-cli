# Prototype Specification Design: Audit Effects (effect.prototype.md)

This document defines the technical schema, formatting rules, and conceptual constraints for creating and managing Audit Effects in JSON prototype format.

---

## 1. JSON Specification Template

Every Audit Effect specification prototype must be written as a valid JSON object matching the following skeleton:

```json
{
  "effectKind": "[Uppercase Enum representing effect type/evaluation style, e.g., 'ATOMIC']",
  "effectId": "[snake_case identifier matching file name prefix, e.g., 'expression_brevity']",
  "effectAxis": "[Capitalized Title Case string, e.g., 'Expression Brevity']",
  "effectSubject": "[Sentence case string defining the target subject of the evaluation, e.g., 'Information expressions']",
  "effectMaximize": [
    "[Unique positive aspect/metric representing constructive intent or clear information transmission]",
    "[Additional positive aspect reframed to introduce semantic diversity without word repetition]"
  ],
  "effectMinimize": [
    "[Unique negative aspect representing structural/cognitive friction, clutter, or unwanted variance]",
    "[Additional negative aspect reframed to introduce semantic diversity without word repetition. Use a grammatically normalized format matching the effectMaximize list (e.g., matching adjectives like 'Absurd', or compound nouns like 'Invariant violations')]"
  ]
}
```

---

## 2. Formatting & Design Constraints

### A. Field-Level Rules
* **`effectId`**: snake_case string matching the file name prefix.
* **`effectAxis`**: Must be formatted in Title Case, defining the qualitative axis evaluated.
* **`effectKind`**: Uppercase enum representing effect type/evaluation style (e.g., `"ATOMIC"`).
* **`effectSubject`**: Sentence case string describing the target subject of the evaluation (e.g., `"Information expressions"`).
* **`effectMaximize`**: Array of unique positive aspects representing constructive intent.
* **`effectMinimize`**: Array of unique negative aspects representing friction, clutter, or unwanted variance.

### B. Maximize vs. Minimize Poles (Asymmetry & Grammatical Normalization)
* **Asymmetric Mapping**: The items in `effectMaximize` and `effectMinimize` must represent distinct, non-overlapping concepts and **never** be simple mirror-image negations of each other.
* **Semantic Diversity (Pleonastic Layering)**: Multiple options must be provided to capture different conceptual viewpoints of the pole.
* **Grammatical Normalization**: All options in `effectMinimize` must follow a consistent grammatical format that aligns with the projection style of `effectMaximize` to ensure logical symmetry:
  - **Adjective-based style**: If positive poles are formulated as adjectives, negative poles must also be adjectives (e.g., `"Absurd"`, `"Fallacious"`, `"Implausible"`).
  - **Noun-based style**: If positive poles are formulated as nouns, negative poles must follow the consistent compound noun format: `[Noun Adjunct] [Plural Noun]` (e.g., `"Expectation deviations"`, `"Invariant violations"`).
