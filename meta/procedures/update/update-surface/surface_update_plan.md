# Procedural Plan for Writing Update Surface-Area Specifications (surface_update_plan.md)

This document is the **procedural counterpart** to the declarative update surface-area blueprint (`surface_update_spec.md`). It defines the chronological sequence of steps required to write a concrete update surface-area specification at `meta/history/<branch_name>_<version>/<feature_name>_surface.md`.

---

## Phase 1: Boundary Topography Mapping

Establish the system-level boundary inputs and outputs.

* **Step 1.1: Map Inbound Vectors**
  - Identify and record new or modified inputs at the system boundary under Section 1.1.
* **Step 1.2: Map Outbound Vectors**
  - Identify and record new or modified outputs, side-effects, and external integrations under Section 1.2.

---

## Phase 2: Interface Contract Definition

Formulate the detailed constraints, payload structures, and operational behaviors for each targeted boundary interface.

* **Step 2.1: Define Inputs & Preconditions**
  - Specify input structures, constraints, boundary contracts, and preconditions under Section 2 for each modified or introduced interface.
  - Reference established codebase patterns aligning with the update's conventions.
* **Step 2.2: Define Outputs & Postconditions**
  - Specify nominal and exceptional output structures, diagnostic metadata, and side-effects under Section 2 for each interface.
  - Integrate exceptional outcomes directly within outputs and postconditions, ensuring error payloads omit internal codebase details.
* **Step 2.3: Document Transition Mapping (For Modified Surfaces)**
  - For any existing interface undergoing a boundary modification, detail the mapping from the legacy interface contract to the modified boundary surface-area.
