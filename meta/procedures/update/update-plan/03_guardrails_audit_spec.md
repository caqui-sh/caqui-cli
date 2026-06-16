# Technical Audit Specification: Architectural & Process Guardrails Integrity (03_guardrails_audit_spec.md)

This document defines the rules for auditing the **Architectural & Process Guardrails Integrity** of concrete update implementation plans (`meta/history/<branch_name>_<version>/<feature_name>_plan.md`) against [plan_update_spec.md](/meta/procedures/update/update-plan/plan_update_spec.md).

> [!NOTE]
> This specific audit evaluates only compliance with the constant negative constraints (Macro-Architecture, Foundational Design, and Developer Process guardrails). All other audit dimensions are deferred to their respective stages.

---

## A. Macro-Architecture & Staging Guardrails

* **No High-Coupling Layer Violations**:
  - Core domain logic must remain completely independent and must never import or depend on outer subsystems.
* **No Implicit State Coupling**:
  - Tasks must not coordinate execution or share mutable state across subsystem boundaries; localize mutability to avoid implicit temporal dependencies.
* **No Shoehorned Integrations**:
  - Rejects plan steps that substitute localized workarounds, hacks, or ad-hoc adaptations for required structural refactoring.

---

## B. Foundational Design & Process Guardrails

* **No Unnecessary Indirection**:
  - Rejects tasks introducing intermediate layers of indirection when direct usage suffices.
* **No Premature Generalization**:
  - Rejects tasks introducing generic abstractions when a single concrete implementation suffices.
* **No Over-Engineering**:
  - Rejects tasks proposing complex design patterns when simpler constructs suffice.
* **No Over-Encapsulation**:
  - Rejects tasks restricting visibility or wrapping code beyond necessity.
* **No Monolithic Phase Implementation**:
  - Rejects plans that do not complete, compile, and verify each phase chronologically before moving to the next.
* **No Short-Sighted Expediency**:
  - Rejects steps implementing narrow, localized workarounds to satisfy immediate constraints at the expense of clean integration.
* **No Premature Performance Tuning**:
  - Rejects performance optimizations scheduled without profiling evidence.
