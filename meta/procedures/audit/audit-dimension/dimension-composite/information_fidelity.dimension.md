# Audit Dimension Specification *(Composite & Entangled / Layered)*: Information Fidelity (information_fidelity.dimension.md)

This specification defines the rules for the **Information Fidelity** dimension. It audits signal quality by balancing token precision against token brevity, answering: *Is the message condensed efficiently without cutting out vital details that make it complete?*

### Composed Dimensions
* [Token Precision](dimension-atomic/token_precision.dimension.md)
* [Token Brevity](dimension-atomic/token_brevity.dimension.md)

---

## Composite Composition & Entanglement

Information Fidelity balances the tension between token precision and token brevity. High token precision can lead to overly long and verbose text, while high token brevity can strip out critical detail and lead to vagueness. Information Fidelity manages this trade-off to optimize signal efficiency.

* **Information Fidelity (Token Precision vs. Token Brevity)**:
  - **Constraint**: The target asset must condense its message efficiently without cutting out vital details that make it complete, answering: *Is the message condensed efficiently without cutting out vital details that make it complete?*
  - **Audit Focus**: Evaluates the balance of signal clarity and completeness relative to the density of the text.
  - **Mutual Exclusive Distinction**: Focuses strictly on detail completeness and signal efficiency. It does not audit readability or reader compatibility (Reader Accessibility).
