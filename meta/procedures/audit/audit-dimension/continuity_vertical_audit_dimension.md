# Technical Audit Specification: Continuity - Vertical (continuity_vertical_audit_dimension.md)

This specification defines the rules for the **Continuity** dimension. It audits the gradient progression across the vertical abstraction range of the target asset, ensuring transitions between adjacent layers are step-wise and free of abrupt gaps or skipped operational steps, answering: *Are the vertical transitions between adjacent layers of resolution step-wise and free of resolution cliffs or missing transitional steps within the target asset?*

This dimension exists under the [**Resolution & Encoding (Depth)**](../audit-pillar/vertical_audit_pillar.md) pillar.

This dimension is [**Subjective & Spectrum-based**](../audit-nature/subjective_spectrum_audit_nature.md) in nature.

---

## Dimension Constraints

* **Continuity (Gradient Progression)**:
  - **Constraint**: The transition between adjacent vertical layers of resolution within the target asset must be smooth, step-wise, and free of resolution gaps or missing transitional steps.
  - **Audit Focus**: Flags resolution cliffs or missing transitional steps within the target asset.
  - **Mutual Exclusive Distinction**: Assumes every layer present within the target asset is accurate and consistent; it looks only for transitional gaps between layers.
