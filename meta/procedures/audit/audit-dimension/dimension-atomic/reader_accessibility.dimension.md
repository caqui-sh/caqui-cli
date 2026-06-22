# Audit Dimension Specification *(Atomic & Terminal / Non-Divisible)*: Reader Accessibility - Projection (reader_accessibility.dimension.md)

This specification defines the rules for the **Reader Accessibility** dimension. It audits the readability and fit of the target asset, answering: *Is the target asset structured and phrased to minimize ingestion friction for the specific target reader (human or machine)?*

This dimension exists under the [**Resolution & Projection**](audit-pillar/projection.pillar.md) pillar.

This dimension is [**Subjective & Spectrum-based**](audit-nature/subjective_spectrum.nature.md) in nature.

---

## Dimension Constraints

* **Reader Accessibility (Readability & Fit)**:
  - **Constraint**: The presentation layer of the target asset must be structured and phrased to minimize ingestion friction and match the capability of the specific target receiver (human or machine).
  - **Audit Focus**: Identifies and flags overly complex sentence structures, formatting layouts that hinder ingestion, jargon that doesn't fit the consumer's context, and high cognitive-load phrasing.
  - **Mutual Exclusive Distinction**: Focuses on ingestion ease and fit. It does not measure the factual accuracy of the message (Semantic Veracity) or whether detail density has been compressed (Information Fidelity).
