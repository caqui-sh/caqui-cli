# Audit Dimension Specification *(Atomic & Terminal)*: Exclusion Accuracy - Scope (exclusion_accuracy.dimension.md)

This specification defines the rules for the **Exclusion Accuracy** dimension. It audits the boundary enforcement of the evaluation universe, ensuring that out-of-scope information is successfully identified and excluded, answering: *Was the defined scope boundary successfully enforced, completely preventing out-of-scope information from entering the target asset (minimizing false positives and information pollution / maximizing boundary enforcement)?*

This dimension exists under the [**Domain Delineation (Scope)**](audit-pillar/scope.pillar.md) pillar.

This dimension is [**Objective & Discrete (Zero-Tolerance)**](audit-nature/objective_discrete.nature.md) in nature.

---

## Dimension Constraints

* **Exclusion Accuracy (Scope Enforcement)**:
  - **Constraint**: The evaluation must achieve zero information pollution, preventing out-of-scope details (false positives) and overall content dilution (information pollution) from entering the target asset.
  - **Audit Focus**: Measures and evaluates boundary enforcement, identifying out-of-scope details (false positives) and evaluating the overall density of irrelevant information (information pollution).
  - **Mutual Exclusive Distinction**: Focuses exclusively on identifying out-of-scope intrusions and pollution (false positives and information pollution), completely blind to whether required in-scope information was omitted (Inclusion Accuracy).
