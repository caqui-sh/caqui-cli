# Audit Dimension Specification *(Atomic & Terminal / Non-Divisible)*: Notation Conformance - Structure (notation_conformance.dimension.md)

This specification defines the rules for the **Notation Conformance** dimension (formerly Syntax & Formatting). It audits line-by-line syntax, layout, spelling, and cosmetic style guide compliance, answering: *Does the target asset violate any line-level formatting constraints, notation conventions, or spelling and spacing rules?*

This dimension exists under the [**Structural Architecture (Blueprint)**](audit-pillar/structure.pillar.md) pillar.

This dimension is [**Objective & Discrete (Zero-Tolerance)**](audit-nature/objective_discrete.nature.md) in nature.

---

## Dimension Constraints

* **Notation Conformance (Terminal Syntax & Style Compliance)**:
  - **Constraint**: The terminal characters, spelling, spacing, inline syntax, and cosmetic layout must comply with mechanical rules.
  - **Asymmetric & Terminal Nature**: Notation Conformance is terminal and non-layered, operating at the leaf level of text representation (sentences, words, spacing, lint rules). It inherits the container framework established by Macro Structure and copy-edits the leaf contents.
  - **Audit Focus**: Catches spelling errors, markdown spacing nits, invalid inline tags, trailing whitespaces, and general line-level style violations.
  - **Mutual Exclusive Distinction**: Focuses exclusively on micro-level compliance. It is blind to the global heading layout (Macro Structure) and semantic/logical correctness of the content.
