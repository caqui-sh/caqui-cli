# Audit Dimension Specification *(Atomic & Terminal / Non-Divisible)*: Macro Depth - Projection (macro_depth.dimension.md)

This specification defines the rules for the **Macro Depth** dimension. It audits the global, hierarchical layers of zoom and perspective (e.g., Document -> Section -> Subsection -> Paragraph) of the target asset, answering: *Is the global vertical hierarchy of zoom levels and nested abstraction scales correctly calibrated to the objective?*

This dimension exists under the [**Resolution & Projection**](audit-pillar/projection.pillar.md) pillar.

This dimension is [**Subjective & Spectrum-based**](audit-nature/subjective_spectrum.nature.md) in nature.

---

## Dimension Constraints

* **Macro Depth (Hierarchical Abstraction Layers)**:
  - **Constraint**: The overall abstraction layers and zoom levels of the target asset must be nested logically and calibrated to the target objective.
  - **Audit Focus**: Verifies that the nested hierarchy of zoom levels (document, section, subsection) is structurally coherent, does not skip steps in the cascade, and avoids abrupt scale mismatches between parent and child elements.
  - **Mutual Exclusive Distinction**: Focuses on the global, nested hierarchy of zoom scales. It does not audit sentence-by-sentence local detail density (Depth Conformance) or structural conformity (Macro Structure).
