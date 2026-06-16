# Update Use-Case Matrix Specification & Blueprint (matrix_update_spec.md)

This document defines the rules and JSON payload schema for concrete update use-case matrix files (`meta/history/<branch_name>_<version>/<feature_name>_matrix.json`). 

An update use-case matrix is the **behavioral definition** (part three of the three-part specification sequence). It defines the full MECE behavioral scenario matrix, transitions, and edge cases as a structured JSON array.

---

## A. Output Payload Blueprint

All use-case scenarios must be compiled into a single JSON array. Each object in the array must conform to the following schema:

```json
[
  {
    "id": "<unique_scenario_id>",
    "description": "<clear_objective_description_of_the_scenario>",
    "preExistingState": "<system_state_prior_to_the_trigger>",
    "inputTrigger": "<input_payload_or_boundary_event_triggering_the_scenario>",
    "expectedPostconditions": [
      "<expected_system_state_or_observable_output>"
    ],
    "invariantBounds": [
      "<safety_constraint_or_bound_preserved>"
    ]
  }
]
```

---

## B. Field Specifications & Structural Constraints

Each object in the JSON array must contain the following fields:

| Field | Type | Required | Format / Allowed Values | Description |
| :--- | :--- | :---: | :--- | :--- |
| `id` | String | Yes | `^SC-\d{2}$` | Unique scenario identifier, starting at `SC-01` and incrementing sequentially. |
| `description` | String | Yes | Free-form string | Objective description of the behavioral scenario. |
| `preExistingState` | String | Yes | Free-form string | The state of the system before the trigger occurs. |
| `inputTrigger` | String | Yes | Free-form string | The specific boundary event or input payload that triggers the scenario. |
| `expectedPostconditions` | Array of Strings | Yes | Array of free-form strings | List of resulting system states, observable outputs, and side-effects. |
| `invariantBounds` | Array of Strings | Yes | Array of free-form strings | List of safety boundaries or system rules that must remain preserved. |

---

## C. Payload Integrity Invariants

* **Identifier Uniqueness & Ordering**:
  - Every scenario object in the array must have a unique `id` value.
  - Scenario IDs must begin at `SC-01` and increment sequentially without gaps.
* **MECE Completeness & Determinism**:
  - **Determinism**: Scenarios sharing states and triggers must have disjoint predicates.
  - **Coverage**: Scenarios must cover the entire behavioral spectrum of the modified surface area.
* **Semantic Correctness & Realizability**:
  - **State-Trigger Compatibility**: The trigger defined in each scenario must be logically possible within the declared pre-existing state.
  - **Post-Condition Realizability**: Post-conditions must be logically reachable from the pre-existing state.
  - **Invariant Preservation**: Scenario post-conditions must preserve the defined invariant bounds.
  - **Error Pathway Mapping**: Failure scenarios must map directly to exceptional outputs defined in the companion surface contract.
* **State Machine & Transition Integrity**:
  - **Initial State Entry**: The matrix must establish a clear entry point (initial state) for the behavioral lifecycle.
  - **State Reachability**: Every state referenced in the matrix must be reachable from the initial state through a sequence of valid scenario transitions.
  - **Terminal State Resolution**: The matrix must contain no terminal traps where a non-terminal state is unable to reach a terminal state.
  - **Deterministic Transitions**: Every transition from a pre-existing state under a given trigger must map to a single, deterministic target state.
* **Strict Black-Box Boundaries**:
  - All field values must focus exclusively on external system behavior and states.
  - References to internal codebase structures or implementation details are prohibited.
* **Content Completion**:
  - All fields must be complete and fully defined.
  - Symbolic representations of value domains are permitted.

