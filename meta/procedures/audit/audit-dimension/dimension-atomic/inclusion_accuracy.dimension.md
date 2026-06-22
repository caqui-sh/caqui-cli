# Audit Dimension Specification *(Atomic & Terminal)*: Inclusion Accuracy - Scope (inclusion_accuracy.dimension.md)

This specification defines the rules for the **Inclusion Accuracy** dimension. It audits the recall and completeness of the evaluation, ensuring that all required information belonging inside the target asset's defined scope is successfully identified and captured, answering: *Was all required information that belongs inside the defined fence successfully captured without omission (minimizing omissions / maximizing information recall)?*

This dimension exists under the [**Domain Delineation (Scope)**](audit-pillar/scope.pillar.md) pillar.

This dimension is [**Objective & Spectrum-based**](audit-nature/objective_spectrum.nature.md) in nature.

---

## Dimension Constraints

* **Inclusion Accuracy (Recall & Completeness)**:
  - **Constraint**: The evaluation must achieve complete recall, identifying and capturing all required information belonging inside the target asset's defined scope.
  - **Audit Focus**: Measures and evaluates search completeness and recall.
  - **Mutual Exclusive Distinction**: Measures what percentage of required information was missed (omissions), completely blind to whether out-of-scope information polluted the target asset.
