# Audit Dimension Specification *(Atomic & Terminal / Non-Divisible)*: Depth Conformance - Projection (depth_conformance.dimension.md)

This specification defines the rules for the **Depth Conformance** dimension. It audits localized detail density at the terminal leaf level (sentences, tokens, parameters) by inheriting constraints from the active macro depth layer, answering: *Do the terminal sentences or details violate the scale constraint inherited from the lowest macro depth layer?*

This dimension exists under the [**Resolution & Projection**](audit-pillar/projection.pillar.md) pillar.

This dimension is [**Subjective & Spectrum-based**](audit-nature/subjective_spectrum.nature.md) in nature.

---

## Dimension Constraints

* **Depth Conformance (Terminal Detail Validation)**:
  - **Constraint**: Local sentences, fields, and values must strictly adhere to the zoom constraint inherited from the lowest active layer of the macro depth cascade.
  - **Audit Focus**: Identifies and flags local scale violations, such as leaking low-level details (code, memory addresses) in a high-level conceptual section, or hand-waving conceptual summaries where concrete low-level parameters are expected.
  - **Mutual Exclusive Distinction**: Operates exclusively as a terminal leaf check. It does not define the nested zoom scales (Macro Depth) or audit factual truth (Semantic Veracity).
