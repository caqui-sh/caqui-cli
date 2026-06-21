# Technical Audit Specification: Uniqueness - Substance (uniqueness_substance_audit_dimension.md)

This specification defines the rules for the **Uniqueness** dimension. It audits the target asset for unnecessary repetition and overlapping information, ensuring each conceptual element is represented exactly once, answering: *Is the target asset free from unnecessary repetition or overlap?*

This dimension exists under the [**Semantic Content (Substance)**](../audit-pillar/substance_audit_pillar.md) pillar.

This dimension is [**Objective & Discrete (Zero-Tolerance)**](../audit-nature/objective_discrete_audit_nature.md) in nature.

---

## Dimension Constraints

* **Uniqueness (Zero Redundancy)**:
  - **Constraint**: The target asset must be free from unnecessary repetition and overlapping information.
  - **Audit Focus**: Flags duplicate elements and redundant information units within the target asset.
  - **Mutual Exclusive Distinction**: Measures informational bloat and repetition. It flags instances where valid information is repeated needlessly, regardless of veracity or formatting.
