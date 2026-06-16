# Technical Audit Specification: Plan Staging Strategy & Macro-Path Optimization (01_strategy_audit_spec.md)

This document defines the rules for auditing the **Staging Strategy & Macro-Path Optimization** of concrete update implementation plans (`meta/history/<branch_name>_<version>/<feature_name>_plan.md`) against the master specification [plan_update_spec.md](/meta/procedures/update/update-plan/plan_update_spec.md).

> [!NOTE]
> This specific audit evaluates only the implementation plan's high-level staging strategy, macro execution path, and architectural fit. All other audit dimensions are deferred to their respective stages.

---

## A. Macro-Path Selection & Architectural Fit (Anti-Shoehorning)

* **Natural Architectural Fit**:
  - The proposed changes must align with and respect the codebase's existing architectural boundaries and paradigms.
  - Plans are strictly prohibited from "shoehorning" update logic into existing modules using localized workarounds, hacks, or ad-hoc adaptations.
* **Mandatory Core Refactoring Stages**:
  - If the target update cannot be cleanly integrated within the current codebase design, the plan must explicitly stage a core structural refactoring phase first.
  - Forcing update logic into an unsupportive architecture is prohibited.
* **Path Selection & Strategic Alternatives**:
  - The plan must select the execution route that minimizes technical debt.
  - Leverage or extend existing domain models and subsystems rather than introducing redundant parallel pipelines.

---

## B. Staging, Coupling, & Complexity Optimization

* **Temporal Coupling & Ordering Minimization**:
  - Order execution phases to minimize intermediate dependencies and transitional overhead.
* **Architectural Decoupling**:
  - Minimize structural coupling and dependencies across subsystem boundaries.
* **Complexity & Path Minimization**:
  - Prioritize direct staging paths that minimize intermediate delegation layers.
