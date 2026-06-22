# Audit Dimension Specification *(Atomic & Terminal)*: Macro Topology - Structure (macro_topology.dimension.md)

This specification defines the rules for the **Macro Topology** dimension. It audits the relational structure, logical flow, and network graph of the information space within the target asset, evaluating directional dependencies, transitions, and encapsulation of information units, answering: *Are the internal relationships, logical paths, and dependencies (whether explicitly declared or semantically implied) structurally valid, complete, and free of circular loops or broken linkages (minimizing circularity / maximizing relational integrity)?*

This dimension exists under the [**Structural Architecture (Blueprint)**](audit-pillar/structure.pillar.md) pillar.

This dimension is [**Objective & Discrete (Zero-Tolerance)**](audit-nature/objective_discrete.nature.md) in nature.

---

## Dimension Constraints

* **Macro Topology (Logic Graph)**:
  - **Constraint**: The logical network of information units (nodes) and their dependencies/transitions (edges) must form a valid, non-cyclic graph. Broken linkages, circular reasoning/dependencies, and dangling connections are prohibited.
  - **Audit Focus**: Examines the relational fabric of the asset. This includes both explicit relationships (e.g., key-value linkages, database references, cross-document links) and implied semantic relationships (e.g., narrative flow, logical build-up of claims, step-by-step reasoning).
  - **Mutual Exclusive Distinction**: Looks strictly at the connection graph and dependency relationships of the information, independent of whether those links are represented by physical formatting syntax or are conceptually implied by the content. It is blind to the external factual truth (Semantic Veracity) of the individual nodes themselves.
