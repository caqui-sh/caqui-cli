# Technical Audit Specification: Technical Debt Database Schema & Formatting (04_structure_audit_spec.md)

This document defines the rules for auditing the database shape, schema fields, and syntactic validation of concrete update technical debt database files (`meta/history/<branch_name>_<version>/<feature_name>_debt.json`).

> [!NOTE]
> This specific audit evaluates only the structural schema and formatting of the technical debt JSON file. All other audit dimensions are deferred to their respective stages.

---

## A. Technical Debt Database Schema & Formatting Constraints

* **JSON Shape**:
  - The file must contain exactly a single flat JSON array of objects.
* **Strict Type Validation**:
  - All fields must strictly match their expected data types and formatting regexes as defined in `debt_update_spec.md`:
    - `debt_id` must match `^DEBT-\d{3}$`.
    - `logged_at_index` and `resolved_at_index` (when applicable) must match `^\d{2}$`.
* **Enum Constancy**:
  - The `status` field must be exactly one of: `"active"`, `"deferred"`, `"partially_resolved"`, or `"resolved"`.
  - The `severity` field must be exactly one of: `"critical"`, `"major"`, or `"minor"`.
* **Normalized Empty State**:
  - When no technical debt has been identified for the update, the JSON file must contain exactly `[]` with no whitespaces, newlines, or placeholder contents.
