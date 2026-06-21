# Technical Audit Procedure (audit_plan.md)

This document defines the generic procedural plan for executing an audit using a companion audit specification against target scope references. It outlines how audits are conducted when base dimensions are run concurrently or virtualized under an entangled dimension.

---

## A. Audit Mode Principles

The execution loop and output structure adapt based on the active auditing mode:

* [**Solo Audit Dimension**](audit-mode/solo_audit_mode.md)
* [**Concurrent Composition**](audit-mode/concurrent_audit_mode.md)
* [**Entangled Dimensions (Singular Virtual Dimension)**](audit-mode/entangled_audit_mode.md)

---

## B. Technical Audit Execution Loop

To execute an audit, systematically evaluate target scope references against the active audit ruleset, following the steps and principles defined by the active [Auditing Mode](#a-audit-mode-principles):

* **Target Scope Mapping**: Locate and isolate all sections in target scope references that correspond to the active ruleset.
* **Audit Boundary**: Establish the operational boundary and traversal path over the target scope as defined by the active mode.
* **Constraint Evaluation**: Evaluate active constraints according to the rules defined by the active mode.
* **Issue Compilation**: Catalog and detail all technical issues or validation gaps immediately upon discovery, conforming to the schema and formatting rules defined by the active mode and [audit_spec.md](/meta/procedures/audit/audit_spec.md).
  - **Identifier Uniqueness**: Assign a unique `issueId` for every compiled issue to prevent duplicate keys across the compiled audit issues.
* **Transaction Resolution**: Exhaustively and rigorously execute the audit to completion to compile all failures into a unified set of audit issues, proposing the compiled issues for review.
