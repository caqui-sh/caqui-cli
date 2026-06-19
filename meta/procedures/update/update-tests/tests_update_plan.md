# Procedural Plan for Writing Update Test Specifications (tests_update_plan.md)

This document is the **procedural counterpart** to the declarative update test specification blueprint (`tests_update_spec.md`). It defines the chronological sequence of steps required to write a concrete update test specification at `meta/history/<branch_name>_<version>/<feature_name>_tests.json`.

---

## Phase 1: Scope & Traceability Mapping

Establish the target execution scopes and map the scenarios requiring verification.

* **Step 1.1: Identify Target Test Files**
  - Locate the target test files, defaulting to existing execution files to preserve cohesion and avoid shoehorning.
* **Step 1.2: Establish Traceability Mapping**
  - Map each test validation node directly to its scenario ID in the companion Use-Case Matrix, verifying that every scenario is accounted for to guarantee complete coverage.
  - For updates to pre-existing behaviors, locate and target the preexisting test step by its unique identifier to modify it in place rather than creating a redundant test path.
  - Integrate new validations within existing test hierarchies where the logical scope and preconditions align.
  - Ensure structural container nodes omit the scenario ID and are generated only to organize the validation nodes.

---

## Phase 2: Test Node & Step Definition

Populate the flat test specification array with declarative, black-box nodes.

* **Step 2.1: Formulate Node Structures**
  - For suite nodes: Specify the target execution path and omit parent references.
  - For group and validation nodes: Specify the parent identifier pointing to their container step.
  - For validation nodes: Specify the companion Use-Case Matrix scenario ID.
  - For all nodes: Declare the classification, update type, descriptive purpose, and a tokenized standard name.
* **Step 2.2: Define Preconditions & Assertions**
  - For validation nodes: Map scenario postconditions and invariants to assertions, and preexisting state to preconditions.
  - For functional group nodes: Define shared preconditions representing the setup environment.
  - For suites and abstract group nodes: Omit all precondition and assertion fields.
* **Step 2.3: Enforce Complete Specification**
  - Specify the complete post-update state for modified nodes (not a partial diff).
