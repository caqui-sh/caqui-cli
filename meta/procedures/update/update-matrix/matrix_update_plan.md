# Procedural Plan for Writing Update Use-Case Matrices (matrix_update_plan.md)

This document is the **procedural counterpart** to the declarative update use-case matrix blueprint (`matrix_update_spec.md`). It defines the chronological sequence of steps required to write a concrete update use-case matrix at `meta/history/<branch_name>_<version>/<feature_name>_matrix.json`.

---

## Phase 1: State Space & Trigger Definition

Establish the behavioral context and initial conditions for the update delta.

* **Step 1.1: Define State Boundaries**
  - Identify the pre-existing system states and terminal target states involved in the change.
* **Step 1.2: Identify Input Triggers**
  - Delineate the entry events and payloads that initiate state transitions.

---

## Phase 2: Scenario Formulation

Populate the scenario array sequentially, mapping behaviors from initial entry to terminal resolution.

* **Step 2.1: Formulate Scenarios**
  - Write scenario entries starting at `SC-01` and incrementing sequentially.
  - Define the pre-existing state and input trigger for each scenario.
* **Step 2.2: Define Postconditions & Invariants**
  - Specify the resulting system states, outputs, and side-effects under the expected postconditions array.
  - Specify the safety rules and limits that must remain preserved under the invariant bounds array.
  - Ensure failure scenarios map directly to exceptional outputs defined in the companion surface contract.
* **Step 2.3: Map Modified Scenarios to Existing Tests**
  - For use cases that modify established boundary interfaces, specify the `existingTestStepId` string.
  - Locate the corresponding preexisting E2E test step by its unique, immutable 6-character alphanumeric identifier.
  - Map this identifier directly to ensure that rather than implementing redundant tests, the target existing test step is explicitly identified to be updated.
