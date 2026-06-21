# Technical Audit Specification: Inclusion Accuracy - Breadth (inclusion_breadth_audit_dimension.md)

This specification defines the rules for the **Inclusion Accuracy** dimension. It audits the recall and completeness of the evaluation, ensuring that every single valid element belonging inside the target asset's defined scope is successfully identified and captured, answering: *Was every single valid element that belongs inside the defined fence successfully captured without omission (maximizing recall)?*

This dimension exists under the [**Domain Delineation (Breadth)**](../audit-pillar/breadth_audit_pillar.md) pillar.

This dimension is [**Objective & Spectrum-based**](../audit-nature/objective_spectrum_audit_nature.md) in nature.

---

## Dimension Constraints

* **Inclusion Accuracy (Recall & Completeness)**:
  - **Constraint**: The evaluation must achieve complete recall, identifying and capturing every single valid element belonging inside the target asset's defined scope.
  - **Audit Focus**: Measures and evaluates search completeness and recall.
  - **Mutual Exclusive Distinction**: Measures what percentage of valid items were missed (omissions), completely blind to whether out-of-scope items leaked in.
