# Technical Audit Specification: Information Encoding - Vertical (encoding_vertical_audit_dimension.md)

This specification defines the rules for the **Information Encoding** dimension. It audits the presentation profile of the target asset, balancing informational completeness against the usability constraints of the target endpoint across the entangled sub-points of informational fidelity and accessibility, answering: *How must the presentation profile of the target asset balance informational completeness against the usability constraints of the target endpoint?*

This dimension exists under the [**Resolution & Encoding (Depth)**](../audit-pillar/vertical_audit_pillar.md) pillar.

This dimension is [**Subjective & Spectrum-based**](../audit-nature/subjective_spectrum_audit_nature.md) in nature.

---

## Dimension Constraints

* **Information Encoding (Signal Encoding & Usability)**:
  - **Constraint**: The presentation profile of the target asset must balance informational completeness against the usability constraints of the target endpoint.
  - **Audit Focus**: Evaluates the formatting and density properties of the message of the target asset at the chosen depth layer.
  - **Mutual Exclusive Distinction**: Assumes the underlying data model of the target asset is static, isolating the presentation profile from the semantic or factual truth of the content.

* **Informational Fidelity (Precision vs. Brevity)**:
  - **Constraint**: The message of the target asset must be condensed efficiently without omitting vital details.
  - **Audit Focus**: Evaluates signal clarity of the target asset.
  - **Mutual Exclusive Distinction**: Focuses on precision and brevity balance, blind to whether the receiver has the specialized capability to understand it, and blind to whether the content of the target asset itself is factually correct.

* **Accessibility (Readability & Fit)**:
  - **Constraint**: The text of the target asset must be structured and phrased so the specific receiver (human or machine) can ingest it and act on it seamlessly.
  - **Audit Focus**: Measures ingestion friction and receiver fit of the target asset.
  - **Mutual Exclusive Distinction**: Focuses on usability and receiver alignment, completely blind to whether the underlying text of the target asset has sacrificed technical details or contains false data.
