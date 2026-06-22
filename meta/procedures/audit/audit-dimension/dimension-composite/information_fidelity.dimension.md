# Audit Dimension Specification *(Composite & Entangled / Layered)*: Information Fidelity (information_fidelity.dimension.md)

This specification defines the rules for the **Information Fidelity** dimension. It audits the trade-off between representation volume (Expression Brevity) and detail preservation (Expression Precision), answering: *Is the semantic signal represented with minimal volume while preserving necessary detail?*

### Composed Dimensions
* [Expression Precision](dimension-atomic/expression_precision.dimension.md)
* [Expression Brevity](dimension-atomic/expression_brevity.dimension.md)

---

## Composite Composition & Entanglement

Information Fidelity balances the tension between expression precision and expression brevity. Minimizing representation volume can lead to a loss of detail, while maximizing detail preservation can increase representation volume. Information Fidelity manages this trade-off to optimize signal efficiency.

* **Information Fidelity (Expression Precision vs. Expression Brevity)**:
  - **Constraint**: Represent the semantic signal with minimal representation volume while preserving necessary detail.
  - **Audit Focus**: Evaluates the trade-off between representation footprint and detail preservation to optimize signal efficiency.
  - **Mutual Exclusive Distinction**: Focuses strictly on the trade-off between representation volume and detail preservation. It does not audit readability or reader compatibility (Reader Accessibility).
