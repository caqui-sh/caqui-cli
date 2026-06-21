# Technical Audit Specification: Validity - Structure (validity_structure_audit_dimension.md)

This specification defines the rules for the **Validity** dimension. It audits boundary, limit, and range constraints, ensuring all individual data units and parameter values of the target asset fit within their designated types, domain limits, or logical boundaries, answering: *Do all individual data units and parameters within the target asset fit within their designated types, domain limits, or logical boundaries?*

This dimension exists under the [**Structural Architecture (Blueprint)**](../audit-pillar/structure_audit_pillar.md) pillar.

This dimension is [**Objective & Discrete (Zero-Tolerance)**](../audit-nature/objective_discrete_audit_nature.md) in nature.

---

## Dimension Constraints

* **Validity (Limit & Range Constraints)**:
  - **Constraint**: Every individual data unit, parameter, or value within the target asset must conform to its designated type, domain limit, or logical boundary.
  - **Audit Focus**: Verifies data types, range limits, domain constraints, or logical value boundaries.
  - **Mutual Exclusive Distinction**: An entry can perfectly match the structural layout and syntax rules of the target asset, but still contain an invalid or out-of-bounds value. This audit is blind to overall document layout or semantic truth.
