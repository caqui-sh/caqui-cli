# Pruned Ceiling Concepts Mapping Reference

This document serves as a temporary reference mapping the ceiling concepts pruned from **Expression Validity** to their proper, mutually exclusive dimensions within the audit specification library. This ensures each dimension's optimization vectors remain tightly bounded and free of dimensional drift.

| Pruned Concept | Target Audit Dimension | Rationale for Relocation |
| :--- | :--- | :--- |
| **`"Intuitive clarity"`** | **[Reader Accessibility](file:///home/coder/project/meta/procedures/audit/audit-dimension/dimension-atomic/reader_accessibility.dimension.md)** | Audits the cognitive ease, legibility, and reader decoding effort of the content. Validity should remain blind to reading difficulty. |
| **`"Semantic integrity"`** | **[Semantic Fidelity](file:///home/coder/project/meta/procedures/audit/audit-dimension/dimension-atomic/semantic_fidelity.dimension.md)** | Audits the truthfulness, accuracy, and completeness of representational meaning relative to a source facts/model. |
| **`"Conceptual coherence"`** | **[Semantic Consistency](file:///home/coder/project/meta/procedures/audit/audit-dimension/dimension-atomic/semantic_consistency.dimension.md)** | Audits the uniform application of concepts and rules across the entire asset, preventing contradictions between separate definitions. |
