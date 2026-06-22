# Audit Dimension Specification *(Atomic & Terminal / Non-Divisible)*: Exclusion Accuracy - Scope (exclusion_accuracy.dimension.md)

This specification defines the rules for the **Exclusion Accuracy** dimension. It audits the containment of the evaluation universe, ensuring that out-of-scope elements are successfully blocked and prevented from polluting the target asset, answering: *Were out-of-scope details and irrelevant noise successfully blocked from polluting the target asset (maximizing containment)?*

This dimension exists under the [**Domain Delineation (Scope)**](audit-pillar/scope.pillar.md) pillar.

This dimension is [**Objective & Discrete (Zero-Tolerance)**](audit-nature/objective_discrete.nature.md) in nature.

---

## Dimension Constraints

* **Exclusion Accuracy (Scope Enforcement)**:
  - **Constraint**: The evaluation must achieve complete containment, preventing any out-of-scope details or noise from polluting the target asset.
  - **Audit Focus**: Measures and evaluates containment and scope enforcement.
  - **Mutual Exclusive Distinction**: Focuses exclusively on containment/leakage, completely blind to whether required elements were omitted (Inclusion).
