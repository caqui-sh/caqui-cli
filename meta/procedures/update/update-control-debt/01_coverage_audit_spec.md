# Technical Audit Specification: Technical Debt Coverage & Exhaustiveness (01_coverage_audit_spec.md)

This document defines the rules for auditing the coverage and exhaustiveness of concrete update technical debt database files (`meta/history/<branch_name>_<version>/<feature_name>_debt.json`). It ensures that every criteria compromise introduced or modified within the scope of the active update is completely cataloged.

> [!NOTE]
> This specific audit evaluates only the coverage and exhaustiveness of technical debt logged within the active update scope. All other audit dimensions are deferred to their respective stages.

---

## A. Technical Debt Coverage & Exhaustiveness Constraints

* **Scope-Bound Evaluation**:
  - The audit must evaluate only the files, interfaces, and execution paths modified or introduced within the active update scope. Evaluative scanning of the wider, unrelated codebase is excluded.
* **100% Coverage of Update Scope Compromises**:
  - Every violation of the following criteria within the update scope must be cataloged as active debt:
    - **No High-Coupling Layer Violations**: Domain/business logic must remain clean and independent of outer subsystems.
    - **No Implicit State Coupling**: Mutable state must not be shared or execution coordinated across subsystem boundaries without explicit, safe interfaces.
    - **No Shoehorned Integrations**: Do not force logic into existing structures; perform clean refactoring instead.
    - **No Unnecessary Indirection**: Intermediate wrappers, interfaces, or classes must not be introduced where direct invocation suffices.
    - **No Premature Generalization**: Avoid generic abstractions when concrete types and simple logic are sufficient.
    - **No Over-Engineering**: Complex design patterns should be avoided when simple procedural or functional constructs suffice.
    - **No Over-Encapsulation**: Visibility must not be restricted or code wrapped beyond actual usage needs.
    - **Undocumented Behaviors**: All new edge cases, mutations, or observable outputs introduced during development must be documented.
    - **Macro‑Architectural Technical Debt**: Any compromise to system scalability, performance, security, or maintainability that introduces long‑term risk, added cost, or inhibits future evolution of the software.
