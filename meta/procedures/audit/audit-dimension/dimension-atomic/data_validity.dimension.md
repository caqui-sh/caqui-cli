# Audit Dimension Specification *(Atomic & Terminal / Non-Divisible)*: Data Validity - Structure (data_validity.dimension.md)

This specification defines the rules for the **Data Validity** dimension. It audits value sanity and logical boundaries, ensuring all individual data units and parameter values of the target asset are realistic, sane, and fit within their designated types, domain limits, or logical boundaries, answering: *Do all individual data units and parameters within the target asset represent realistic, sane values that fit within their designated types, domain limits, or logical boundaries?*

This dimension exists under the [**Structural Architecture (Blueprint)**](audit-pillar/structure.pillar.md) pillar.

This dimension is context-sensitive in nature: it operates as [**Objective & Discrete (Zero-Tolerance)**](audit-nature/objective_discrete.nature.md) when evaluating structured high-level data (e.g. JSON schemas, API constraints, data types), but behaves as [**Subjective & Spectrum-based**](audit-nature/subjective_spectrum.nature.md) (or [**Objective & Spectrum-based**](audit-nature/objective_spectrum.nature.md)) when auditing technical prose, terminology glossaries, or style guide compliance.

---

## Dimension Constraints

* **Data Validity (Value Sanity & Logical Boundaries)**:
  - **Constraint**: Every individual data unit, parameter, or value within the target asset must be realistic, sane, and conform to its designated type, domain limit, or logical boundary as defined by the asset's active context.
  - **Audit Focus**: Verifies data types, value sanity, domain constraints, or logical boundaries.
  - **Context-Sensitive Nature**:
    - *Structured Contexts*: In JSON data, schemas, or API parameters, evaluation is objective, discrete, and zero-tolerance (exact match or failure).
    - *Prose & Document Contexts*: In technical documentation and natural language guidelines, evaluation is spectrum-based and subjective (degrees of compliance, such as active vs. deprecated terminology or stylistic fit).
  - **Mutual Exclusive Distinction**: An entry can perfectly match the structural layout and syntax rules of the target asset, but still contain an invalid, insane, or out-of-bounds value. This audit is blind to overall document layout or semantic truth.
