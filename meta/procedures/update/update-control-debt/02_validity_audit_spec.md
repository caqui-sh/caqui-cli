# Technical Audit Specification: Technical Debt Validity & Verification (02_validity_audit_spec.md)

This document defines the rules for auditing the validity and codebase alignment of concrete update technical debt database files (`meta/history/<branch_name>_<version>/<feature_name>_debt.json`). It ensures that only active, verified architectural compromises are logged.

> [!NOTE]
> This specific audit evaluates only the validity and reality alignment of logged technical debt items. All other audit dimensions are deferred to their respective stages.

---

## A. Technical Debt Validity & Verification Constraints

* **Verification of Reality**:
  - Logged debt must map directly to active codebase implementations; resolved issues must not be marked active.
* **Exclusion of Micro-Management**:
  - Items that do not compromise macro-architectural quality—such as local implementation or stylistic details—must not be logged as technical debt.
* **Falsifiable Description**:
  - Each entry must define a concrete, logical description specifying the location or path of the issue, explaining the precise nature of the architectural violation, and detailing its structural or operational impact on the codebase.
