# Technical Audit Specification: Implementation Agility & Task Granularity (04_granularity_audit_spec.md)

This document defines the rules for auditing the **Implementation Agility & Task Granularity** of concrete update implementation plans (`meta/history/<branch_name>_<version>/<feature_name>_plan.md`) against [plan_update_spec.md](/meta/procedures/update/update-plan/plan_update_spec.md).

> [!NOTE]
> This specific audit evaluates only implementation agility, task descriptions, step atomicity, and the separation of declarative requirements from execution steps. All other audit dimensions are deferred to their respective stages.

---

## A. Implementation Agility & Outcome Focus

* **No Prescribed Implementation Details**:
  - Task descriptions must strictly avoid prescribing internal code mechanics.
* **Focus on Integration Outcomes**:
  - Tasks must define integration goals and specify the interface boundaries to be integrated.
* **Preservation of Design Paths**:
  - Task descriptions must remain focused on the final outcome of the step, leaving the developer free to choose the cleanest design path.

---

## B. Task Atomicity & Separation of Concerns

* **Single-Responsibility Steps**:
  - Every step must be atomic, representing a single logical unit of work. Monolithic tasks grouping disparate concerns are prohibited.
* **Separation of Concerns (No Duplication)**:
  - Plans must not duplicate or summarize declarative specifications.
  - Plans must refer to companion specifications by relative links to prevent out-of-sync documentation.
* **Compilation-Focused Verification Checkpoints**:
  - Intermediate step verification checkpoints must evaluate only the compilability of the codebase, rather than asserting internal code state or running tests.
