# Audit Dimension Specification *(Atomic & Terminal)*: Depth Conformance - Projection (depth_conformance.dimension.md)

This specification defines the rules for the **Depth Conformance** dimension. It audits localized detail density at the terminal leaf level to ensure alignment with the active perspective layer, answering: *Do the terminal details deviate from the perspective resolution of the active perspective layer (minimizing perspective drift / maximizing resolution alignment)?*

This dimension exists under the [**Resolution & Projection**](audit-pillar/projection.pillar.md) pillar.

This dimension is [**Subjective & Spectrum-based**](audit-nature/subjective_spectrum.nature.md) in nature.

---

## Dimension Constraints

* **Depth Conformance (Terminal Detail Validation)**:
  - **Constraint**: All local leaf-level information units must align with the perspective resolution of the active perspective layer.
  - **Audit Focus**: Identifies and flags local perspective drift, such as introducing premature granularities in a high-level conceptual section, or omitting necessary technical specificity where low-level detail is required.
  - **Mutual Exclusive Distinction**: Operates exclusively as a terminal leaf check. It does not define the global vertical hierarchy of perspective depth levels (Perspective Depth) or audit factual truth (Semantic Veracity).
