# Technical Audit Specification: Exclusion Accuracy - Breadth (exclusion_breadth_audit_dimension.md)

This specification defines the rules for the **Exclusion Accuracy** dimension. It audits the precision and border integrity of the evaluation, ensuring that out-of-scope elements are successfully blocked and prevented from polluting the target asset, answering: *Were out-of-scope elements successfully prevented from breaching the perimeter and polluting the target asset (maximizing precision)?*

This dimension exists under the [**Domain Delineation (Breadth)**](../audit-pillar/breadth_audit_pillar.md) pillar.

This dimension is [**Objective & Discrete (Zero-Tolerance)**](../audit-nature/objective_discrete_audit_nature.md) in nature.

---

## Dimension Constraints

* **Exclusion Accuracy (Precision & Border Integrity)**:
  - **Constraint**: The evaluation must achieve complete precision, preventing any out-of-scope elements from breaching the perimeter and polluting the target asset.
  - **Audit Focus**: Measures and evaluates boundary precision and pollution prevention.
  - **Mutual Exclusive Distinction**: Calculates what percentage of out-of-scope items accidentally got dragged in (pollution), blind to whether valid items were omitted.
