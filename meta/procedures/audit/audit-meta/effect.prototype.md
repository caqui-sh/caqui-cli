# Prototype Specification Design: Audit Effects (effect.prototype.md)

This document defines the technical schema, formatting rules, and conceptual constraints for creating and managing Audit Effects in JSON prototype format.

---

## 1. JSON Specification Template

Every Audit Effect specification prototype must be written as a valid JSON object matching the following skeleton:

```json
{
  "effectKind": "[Uppercase Enum representing effect type/evaluation style, e.g., 'ATOMIC']",
  "effectKey": "[snake_case identifier matching file name prefix, e.g., 'representation_brevity']",
  "effectScope": "[parent scopeKey, e.g., 'information_representation']",
  "effectGoal": "[Sentence case string, e.g., 'Representation brevity']",
  "effectSubject": "[Sentence case string defining the target subject of the evaluation, e.g., 'Information expressions']",
  "effectPerspective": "[Technical statement of directional mapping and convergence behavior, e.g., 'Intrinsic 1-to-1 mapping-constraint resolving a representation to a sole semantic concept.']",
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
* **`effectKey`**: snake_case string matching the file name prefix.
* **`effectGoal`**: Must be formatted in Sentence case, defining the qualitative goal evaluated.
* **`effectScope`**: Must match the scopeKey of the parent scope (e.g., `'information_domain'`, `'information_representation'`, or `'information_semantic'`).
* **`effectKind`**: Uppercase enum representing effect type/evaluation style (e.g., `"ATOMIC"`).
* **`effectSubject`**: Sentence case string describing the target subject of the evaluation (e.g., `"Information expressions"`).
* **`effectPerspective`**: A short string describing the technical, directional mapping vector and convergence behavior of the effect.
* **`effectMaximize`**: Array of unique positive aspects representing constructive intent.
* **`effectMinimize`**: Array of unique negative aspects representing friction, clutter, or unwanted variance.

### B. Maximize vs. Minimize Poles (Asymmetry & Grammatical Normalization)
* **Asymmetric Mapping**: The items in `effectMaximize` and `effectMinimize` must represent distinct, non-overlapping concepts and **never** be simple mirror-image negations of each other.
* **Semantic Diversity (Pleonastic Layering)**: Multiple options must be provided to capture different conceptual viewpoints of the pole.

### C. Formulating effectPerspective
The `effectPerspective` string defines the qualitative vector force or structural dynamic of the effect, acting as the angle of approach. To prevent auditor anchoring and ensure consistency, all perspective strings must adhere to this single universal formulation:

#### 1. The Universal Pattern
```
[Nature] [Active Force/Relationship Dynamics].
```
* *Example (Mapping)*: `"Intrinsic 1-to-1 mapping-constraint from a sole representation to a sole semantic concept."`
* *Example (Boundary)*: `"Extrinsic segregation of the core scope from foreign concepts."`

#### 2. Token Definitions
* **`[Nature]`**: 
  * **`Intrinsic`**: Used for inward parsing flows ($R \rightarrow S$), internal boundary containment, or internal structural coherence.
  * **`Extrinsic`**: Used for outward generation flows ($S \rightarrow R$), external boundary interfaces, or external compliance/grounding rules.
* **`[Active Force/Relationship Dynamics]`**: An active technical noun phrase describing the exact directional vector or structural boundary action.

#### 3. The "Sole" Rule for Singular Targets
To prevent many-to-many naming implications, singular and plural terms must be strictly formatted:
* **Singular Points**: Must always use the prefix **`a sole`** (e.g., `"a sole representation"`, `"a sole semantic concept"`).
* **Plural Points**: Must always use the prefix **`multiple`** (e.g., `"multiple representations"`).

#### 4. Anti-Anchoring Invariant
To prevent design fixation and auditor anchoring, the formulated `effectPerspective` string must **never** contain any words from the `effectGoal`, `effectMaximize`, or `effectMinimize` lists.



* **Grammatical Normalization**: All options in `effectMinimize` must follow a consistent grammatical format that aligns with the projection style of `effectMaximize` to ensure logical symmetry:
  - **Adjective-based style**: If positive poles are formulated as adjectives, negative poles must also be adjectives (e.g., `"Absurd"`, `"Fallacious"`, `"Implausible"`).
  - **Noun-based style**: If positive poles are formulated as nouns, negative poles must follow the consistent compound noun format: `[Noun Adjunct] [Plural Noun]` (e.g., `"Expectation deviations"`, `"Invariant violations"`).
