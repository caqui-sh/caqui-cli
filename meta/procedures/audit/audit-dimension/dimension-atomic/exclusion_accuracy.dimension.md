# Audit Dimension Specification *(Atomic & Terminal)*: Exclusion Accuracy - Scope (exclusion_accuracy.dimension.md)

This specification defines the rules for the **Exclusion Accuracy** dimension. It audits the boundary enforcement of the evaluation universe, ensuring that out-of-scope information is successfully blocked and prevented from polluting the target asset, answering: *Was the defined scope boundary successfully enforced, completely preventing out-of-scope information from entering the target asset (minimizing information pollution / maximizing boundary enforcement)?*

This dimension exists under the [**Domain Delineation (Scope)**](audit-pillar/scope.pillar.md) pillar.

This dimension is [**Objective & Discrete (Zero-Tolerance)**](audit-nature/objective_discrete.nature.md) in nature.

---

## Dimension Constraints

* **Exclusion Accuracy (Scope Enforcement)**:
  - **Constraint**: The evaluation must achieve zero information pollution, preventing any out-of-scope information from entering the target asset.
  - **Audit Focus**: Measures and evaluates information pollution and scope enforcement.
  - **Mutual Exclusive Distinction**: Focuses exclusively on identifying out-of-scope information pollution, completely blind to whether required information was omitted (Inclusion).
