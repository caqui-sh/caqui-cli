# Technical Audit Mode: Solo Audit (solo_audit_mode.md)

This specification defines the **Solo Audit** mode, which evaluates a target scope against a single, isolated dimension.

---

## A. Mode Definition
A single, independent base dimension is evaluated on its own, independent of all other dimensions.

* **Constraint Treatment**: The constraints of the single base dimension are evaluated in isolation.
* **Scope Boundaries**: All other audit dimensions are explicitly out of scope and ignored during the evaluation pass.
