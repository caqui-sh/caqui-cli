# Technical Audit Specification: Depth - Vertical (depth_vertical_audit_dimension.md)

This specification defines the rules for the **Depth** dimension. It audits the zoom level and perspective layer of the target asset, ensuring its vertical resolution is correctly calibrated to the objective, answering: *Is the chosen layer of vertical zoom for the target asset correctly calibrated to the objective?*

This dimension exists under the [**Resolution & Encoding (Depth)**](../audit-pillar/vertical_audit_pillar.md) pillar.

This dimension is [**Subjective & Spectrum-based**](../audit-nature/subjective_spectrum_audit_nature.md) in nature.

---

## Dimension Constraints

* **Depth (Zoom Level)**:
  - **Constraint**: The chosen layer of vertical zoom for the target asset must be correctly calibrated to the objective.
  - **Audit Focus**: Ensures the analytical perspective layer of the target asset is correctly matched to prevent perspective mismatch.
  - **Mutual Exclusive Distinction**: Measures the layer of perspective itself, ensuring the zoom level matches the needs of the consumer, independent of the correctness of the content.
