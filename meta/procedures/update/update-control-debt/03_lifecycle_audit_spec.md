# Technical Audit Specification: Technical Debt Lifecycle & Invariants (03_lifecycle_audit_spec.md)

This document defines the rules for auditing the state transitions, field invariants, and chronology of concrete update technical debt database files (`meta/history/<branch_name>_<version>/<feature_name>_debt.json`). It ensures logical state coherence across control reviews.

> [!NOTE]
> This specific audit evaluates only the lifecycle integrity and state-based field constraints of technical debt database entries. All other audit dimensions are deferred to their respective stages.

---

## A. Technical Debt Lifecycle & Invariant Constraints

* **Chronological Sequence**:
  - For any resolved or partially resolved item, the `resolved_at_index` value must be numerically greater than or equal to the `logged_at_index` value (e.g. debt logged at `"00"` resolved at `"01"`).
* **Unresolved State Constraints**:
  - For items with `status` set to `"active"` or `"deferred"`, the fields `resolved_at_index` and `resolution_details` are prohibited and must be completely omitted from the JSON object.
* **Resolved State Constraints**:
  - For items with `status` set to `"resolved"` or `"partially_resolved"`, the fields `resolved_at_index` and `resolution_details` are strictly required and must contain valid, non-empty values.
* **Identifier Sequencing**:
  - The `debt_id` sequence must be unique, start at `DEBT-001`, and increment sequentially without gaps.
