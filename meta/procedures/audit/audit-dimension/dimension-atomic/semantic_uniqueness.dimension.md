# Audit Dimension Specification *(Atomic & Terminal)*: Semantic Uniqueness - Substance (semantic_uniqueness.dimension.md)

This specification defines the rules for the **Semantic Uniqueness** dimension. It audits the target asset for unnecessary repetition and overlapping information, ensuring each information unit is represented exactly once, answering: *Is the target asset free from unnecessary repetition or overlap (minimizing information redundancy / maximizing distinct coverage)?*

This dimension exists under the [**Semantic Content (Substance)**](audit-pillar/substance.pillar.md) pillar.

This dimension is [**Objective & Discrete (Zero-Tolerance)**](audit-nature/objective_discrete.nature.md) in nature.

---

## Dimension Constraints

* **Semantic Uniqueness (Zero Redundancy)**:
  - **Constraint**: The target asset must be free from unnecessary repetition and overlapping information.
  - **Audit Focus**: Flags duplicate or redundant information units within the target asset.
  - **Mutual Exclusive Distinction**: Measures informational bloat and repetition. It flags instances where valid information is repeated needlessly, regardless of Semantic Veracity or Notation Conformance.
