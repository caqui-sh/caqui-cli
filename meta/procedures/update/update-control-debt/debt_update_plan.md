# Procedural Plan for Managing Technical Debt (debt_update_plan.md)

This document is the **procedural counterpart** to the declarative technical debt database specification (`debt_update_spec.md`). It defines the chronological sequence of steps required to evaluate the codebase and manage the centralized technical debt database file (`meta/history/<branch_name>_<version>/<feature_name>_debt.json`) across control review iterations.

---

## Phase 1: Quality & Architectural Assessment

Evaluate the implementation against the defined architectural quality criteria to identify potential technical debt.

* **Step 1.1: Assess Codebase Against Criteria**
  - Review the codebase against the declarative criteria defined in Section 2 of `debt_update_spec.md`:
    - **Macro-Architecture & Subsystem Coupling**
    - **Foundational Design & Simplicity**
    - **Specification & Behavior Alignment**
    - **General Technical Debt**
* **Step 1.2: Identify Issues**
  - Document any discovered issues that violate criteria.

---

## Phase 2: Database Initialization & Logging

Append newly identified technical debt items to the unified database file.

* **Step 2.1: Locate or Initialize the Database File**
  - Locate the database file at `meta/history/<branch_name>_<version>/<feature_name>_debt.json`.
  - For baseline reviews (`00`) with no identified debt, initialize the file with exactly `[]`.
* **Step 2.2: Add New Debt Items**
  - For each new criteria compromise identified, append a new object to the array:
    - Assign the next sequential ID starting with `DEBT-001`.
    - Populate all core fields: `debt_id`, `title`, `description`, `severity`, `status` (set to `"active"` or `"deferred"`), `logged_at_index` (current control document index), and `compromised_criteria` (describing the spectrum and degree of the violation).
    - Ensure `resolved_at_index` and `resolution_details` are completely omitted.

---

## Phase 3: Status Reconciliation & Resolution Logging

Update the state of preexisting technical debt items when they are resolved, partially resolved, or deferred.

* **Step 3.1: Re-evaluate Preexisting Debt**
  - For subsequent review iterations (> `00`), re-evaluate the status of all active or deferred debt items in the database.
* **Step 3.2: Log Resolutions & Mitigations**
  - For any resolved or partially resolved items:
    - Transition `status` to `"resolved"` or `"partially_resolved"`.
    - Set `resolved_at_index` to the current control document index (e.g. `"01"`).
    - Provide clear technical resolution details in `resolution_details`.
* **Step 3.3: Finalize Database**
  - Ensure all prohibited fields for unresolved items are completely omitted.
