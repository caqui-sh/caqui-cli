# Technical Audit Specification: Dependency-Driven Phase Sequencing (02_sequencing_audit_spec.md)

This document defines the rules for auditing the **Dependency-Driven Phase Sequencing** of concrete update implementation plans (`meta/history/<branch_name>_<version>/<feature_name>_plan.md`) against [plan_update_spec.md](/meta/procedures/update/update-plan/plan_update_spec.md).

> [!NOTE]
> This specific audit evaluates only the implementation plan's phase sequencing, dependency alignment, compilable boundaries, and checkpoint ordering. All other audit dimensions are deferred to their respective stages.

---

## A. Directional Staging & Dependency Alignment

* **Dependency-Compliant Staging**:
  - Sequence implementation phases to align with structural dependencies.
  - Avoid staging dependent changes in a manner that requires temporary adapter interfaces or mocks to compile.

---

## B. Cohesive Phase Boundaries & Verification Gates

* **Self-Contained Milestones**:
  - Each phase must target a logically complete subsystem or interface boundary.
  - Avoid staging changes in a manner that leaves interfaces broken or incomplete at phase boundaries.
* **Compilation-Focused Intermediate Gates**:
  - Verify that intermediate verification commands target compilation or static analysis rather than test execution.
  - All test execution must be deferred until the final integration verification phase.
* **Incremental Progress Checklist**:
  - Each phase must build progressively upon the results of previous phases, establishing a clear chronological lineage from baseline initialization to final integration.
