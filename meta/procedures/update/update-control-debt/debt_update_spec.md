# Technical Debt Database Specification (debt_update_spec.md)

This document establishes the specification and structural schema for managing the centralized technical debt database file (`meta/history/<branch_name>_<version>/<feature_name>_debt.json`) associated with an update.

---

## 1. Technical Debt Database Schema & Constraints

All technical debt, both active and resolved, must be managed in a single, unified JSON file located at:
`meta/history/<branch_name>_<version>/<feature_name>_debt.json`

The file must contain a single flat JSON array of objects representing debt items. Each object in the array represents a technical debt node and must belong to one of two configurations depending on its `status` field:
- **Unresolved Debt**: `status` is `"active"` or `"deferred"`.
- **Resolved Debt**: `status` is `"resolved"` or `"partially_resolved"`.

### Schema Fields

| Field | Type | Required | Applicable State | Format / Allowed Values | Description |
| :--- | :--- | :---: | :---: | :--- | :--- |
| `debt_id` | String | Yes | All | `^DEBT-\d{3}$` | Unique identifier assigned to the technical debt item. |
| `title` | String | Yes | All | Free-form string | Short descriptive title of the debt item. |
| `description` | String | Yes | All | Free-form string | Detailed explanation of the debt, its context, and its macro-architectural implications. |
| `severity` | String | Yes | All | `critical` \| `major` \| `minor` | Assessment of the debt's severity. |
| `status` | String | Yes | All | `active` \| `deferred` \| `partially_resolved` \| `resolved` | Current resolution status of the debt item. |
| `logged_at_index` | String | Yes | All | `^\d{2}$` | The index of the control iteration when this debt was first logged (e.g. `"00"`). |
| `compromised_criteria` | String | Yes | All | Free-form string | Nuanced description of which architectural criteria from Section 2 are compromised, and to what degree or spectrum of violation. |
| `resolved_at_index` | String | Yes (Resolved Debt), Prohibited (Unresolved Debt) | Resolved Debt | `^\d{2}$` | The index of the control iteration when this debt was resolved or partially resolved. Must be omitted for Unresolved Debt. |
| `resolution_details` | String | Yes (Resolved Debt), Prohibited (Unresolved Debt) | Resolved Debt | Free-form string | Technical explanation of how the debt was resolved or partially resolved. Must be omitted for Unresolved Debt. |


---

## 2. Technical Debt & Architectural Evaluation Criteria

The following architectural criteria are used to identify and catalog technical debt within `<feature_name>_debt.json`.

### Macro-Architecture & Subsystem Coupling
* **No High-Coupling Layer Violations**: Domain/business logic must remain clean and independent of outer subsystems.
* **No Implicit State Coupling**: Mutable state must not be shared or execution coordinated across subsystem boundaries without explicit, safe interfaces.
* **No Shoehorned Integrations**: Do not force logic into existing structures; perform clean refactoring instead.

### Foundational Design & Simplicity
* **No Unnecessary Indirection**: Intermediate wrappers, interfaces, or classes must not be introduced where direct invocation suffices.
* **No Premature Generalization**: Avoid generic abstractions when concrete types and simple logic are sufficient.
* **No Over-Engineering**: Complex design patterns should be avoided when simple procedural or functional constructs suffice.
* **No Over-Encapsulation**: Visibility must not be restricted or code wrapped beyond actual usage needs.

### Specification & Behavior Alignment
* **Undocumented Behaviors**: All new edge cases, mutations, or observable outputs introduced during development must be documented.

### General Technical Debt
* **Macro‑Architectural Technical Debt**: Any compromise to system scalability, performance, security, or maintainability that introduces long‑term risk, added cost, or inhibits future evolution of the software. This includes architectural shortcuts, deferred core refactoring, and unaddressed cross‑cutting concerns.
