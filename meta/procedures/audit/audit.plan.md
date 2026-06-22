# Technical Audit Procedure (audit.plan.md)

This document defines the generic procedural plan for executing an audit using a companion audit specification against target scope references (which conform to a base specification designed under [**Base Specification Auditability rules**](audit-meta/base_spec_auditability.meta.md)). It outlines how audits are conducted under the unified concurrent evaluation model.

---

## A. Audit Execution Principles

Audits are executed under a single unified **Concurrent Evaluation** model. Under this model:
* **Concurrent Execution**: One or more base dimensions are evaluated in parallel during a single traversal of the target asset. Evaluating a single, isolated dimension is treated as a valid subset of concurrent execution (where the dimension count is 1).
* **Universal Traversal**: The auditor navigates the target asset's structure, evaluating all active constraints simultaneously to minimize context-switching overhead and maximize audit efficiency.

---

## B. Technical Audit Execution Loop

To execute an audit, systematically evaluate target scope references against the active audit ruleset:

* **Target Scope Mapping**: Locate and isolate all sections in target scope references that correspond to the active ruleset.
* **Audit Boundary**: Establish the operational boundary and traversal path over the target scope.
* **Constraint Evaluation**: Evaluate active constraints concurrently.
* **Issue Compilation**: Catalog and detail all technical issues or validation gaps immediately upon discovery, conforming to the schema and formatting rules defined by the dimension types and [audit.spec.md](audit.spec.md).
  - **Identifier Uniqueness**: Assign a unique `issueId` for every compiled issue to prevent duplicate keys across the compiled audit issues.
* **Transaction Resolution**: Exhaustively and rigorously execute the audit to completion to compile all failures into a unified set of audit issues, proposing the compiled issues for review.
