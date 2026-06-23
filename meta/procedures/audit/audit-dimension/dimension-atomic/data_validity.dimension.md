# Audit Dimension Specification *(Atomic & Terminal)*: Data Validity - Structure (data_validity.dimension.md)

This specification defines the rules for the **Data Validity** dimension. It audits value sanity and semantic boundaries, ensuring all individual data elements and values of the target asset are realistic, sane, and fit within their contextual boundaries, answering: *Do all individual data elements and values within the target asset represent realistic, sane values that fit within their contextual boundaries (minimizing value infractions and deviations / maximizing contextual conformance)?*

This dimension exists under the [**Structural Architecture (Blueprint)**](audit-pillar/structure.pillar.md) pillar.

This dimension is context-sensitive in nature: it operates as [**Objective & Discrete (Zero-Tolerance)**](audit-nature/objective_discrete.nature.md) when evaluating deterministic, formally defined rules and absolute boundary constraints, but behaves as [**Subjective & Spectrum-based**](audit-nature/subjective_spectrum.nature.md) (or [**Objective & Spectrum-based**](audit-nature/objective_spectrum.nature.md)) when auditing qualitative constraints, conceptual boundaries, or semantic conventions.

---

## Dimension Constraints

* **Data Validity (Value Sanity & Semantic Boundaries)**:
  - **Constraint**: Every individual data element or value within the target asset must be realistic, sane, and conform to its contextual boundaries as defined by the active context, avoiding value infractions and deviations.
  - **Audit Focus**: Verifies that values conform to all contextual boundaries, identifying out-of-bounds infractions and deviations.
  - **Context-Sensitive Nature**:
    - *Deterministic Contexts*: Where values are governed by strict mathematical, logical, or type boundaries, evaluation is objective, discrete, and zero-tolerance (yielding a binary pass/fail state for each boundary).
    - *Semantic & Qualitative Contexts*: Where values are governed by qualitative constraints, conceptual boundaries, or semantic conventions, evaluation is spectrum-based and subjective (measuring degrees of deviation or conceptual alignment).
  - **Mutual Exclusive Distinction**: Focuses strictly on value validity (infractions and deviations). It is blind to the structural layout and format syntax (Notation Conformance), link connectivity (Macro Topology), or conceptual correctness of the model itself (Semantic Fidelity).
