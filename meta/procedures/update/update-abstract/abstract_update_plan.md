# Procedural Plan for Writing Update Abstracts (abstract_update_plan.md)

This document is the **procedural counterpart** to the declarative update abstract blueprint (`abstract_update_spec.md`). It defines the chronological sequence of steps required to write a concrete update abstract at `meta/history/<branch_name>_<version>/<feature_name>_abstract.md`.

---

## Phase 1: Context & Narrative Definition

Establish the high-level intent and nature of the change.

* **Step 1.1: Define Intent and Value**
  - Identify the problem being solved and the value delivered by the target end-state.
  - Record the system context and high-level narrative in Section 1.
* **Step 1.2: Characterize the Change**
  - Summarize the nature of the change at a system level in Section 1.

---

## Phase 2: Operational Guarantees Formulation

Identify the behavioral rules and non-negotiables of the system.

* **Step 2.1: Map Constraints and Guarantees**
  - Define the high-level rules, constraints, or behavioral promises that the update must preserve or newly establish.
  - Record these commitments in Section 2.

---

## Phase 3: Scope & Containment Delineation

Define the black-box boundaries of the change.

* **Step 3.1: Delineate the Containment Boundary**
  - Delineate the targeted surfaces (the whitelist) and the untouched areas (the blacklist) along a spectrum of containment.
  - Document these boundaries in Section 3.
