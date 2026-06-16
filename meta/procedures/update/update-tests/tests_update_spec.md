# Update Test Specification & Blueprint (tests_update_spec.md)

This document establishes the high-level, black-box, and rigorous blueprint for creating concrete update test specifications (`meta/history/<branch_name>_<version>/<feature_name>_tests.json`).

An update test specification is the **test definition** (the integration and validation scenario mapping) and is part of a four-part specification sequence:
1. **The Abstract**: Defines system-level intent.
2. **The Surface-Area Spec**: Defines boundary and interface contracts.
3. **The Use-Case Matrix**: Maps the MECE scenario matrix.
4. **The Test Spec** (this blueprint): Defines concrete, black-box validation paths.

All four documents for a given update are co-located in the same directory under `meta/history/<branch_name>_<version>/` and share the same `<feature_name>_` prefix.

---

## 1. Core Principles of Update Test Specifications

To ensure verifiability and traceability, every concrete update test specification must adhere to the following principles:

* **Boundary-Isolated Black-Box Validation**:
  - Test specifications must evaluate system behavior strictly from a black-box perspective at public-facing boundaries.
  - References to internal codebase structures or implementation details are prohibited.
* **Behavioral Traceability**:
  - Test spec entries must identify the scenarios they validate.
* **Test File Cohesion**:
  - Test cases should target a fitting preexisting test file by default, permitting new test files only when necessary to avoid shoehorning.
* **Coverage Mapping**:
  - The test specification must target every scenario defined in the companion Use-Case Matrix.
* **Hierarchical Step Grouping**:
  - Group test execution paths using recursive nested step arrays to model sequential parent-child execution flows.
* **Declarative Assertions**:
  - Assertions must focus entirely on what behavioral invariants or contract shapes are verified, omitting execution and implementation details.

---

## 2. Concrete Update Test JSON Schema

All test scenarios must be compiled into a single JSON array. Each object in the array (and nested recursively within `steps`) must conform to the following schema:

### 2.1 Output Payload Blueprint

```json
[
  {
    "name": "<tokenized_test_case_name>",
    "e2e_path": "<relative_path_to_test_file>.e2e.ts",
    "description": "<scenario_purpose_description>",
    "trace_references": [
      "<matrix_scenario_identifier>"
    ],
    "preconditions": [
      "<required_state_assertion>"
    ],
    "assertions": [
      "<validated_behavior_invariant>"
    ],
    "steps": [
      {
        "name": "<tokenized_substep_name>",
        "trace_references": [
          "<matrix_scenario_identifier>"
        ],
        "preconditions": [
          "<required_substep_state>"
        ],
        "assertions": [
          "<validated_substep_invariant>"
        ]
      }
    ]
  }
]
```

### 2.2 Field Specifications & Structural Constraints

Each object in the JSON array must contain the following fields:

| Field Name | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| `name` | String | Yes | The tokenized test or step name following the labeling standard. |
| `e2e_path` | String | Yes (for root) | The relative path to the physical test execution file (must end in `.e2e.ts`). Required for top-level objects. |
| `description` | String | No | Description of the test scenario's purpose. |
| `trace_references` | Array of Strings | Yes | Mapped scenario identifiers from the Use-Case Matrix. |
| `preconditions` | Array of Strings | Yes (for leaf) | Declarative statements defining the required initial states or preconditions. |
| `assertions` | Array of Strings | Yes (for leaf) | Declarative statements defining the validated invariants or outcomes. |
| `steps` | Array of Objects | No | Array of nested child test step objects conforming recursively to this schema. |

---

## 3. Payload Integrity Invariants

* **Identifier & Labeling Compliance**:
  - All test and step names must strictly conform to the repository labeling standard.
* **Content Completion**:
  - All fields must be complete and fully defined.
  - Symbolic representations of value domains are permitted.
* **Trace Reference Resolution & Co-location**:
  - Every trace reference must resolve to a valid scenario ID mapped in the co-located companion Use-Case Matrix (`<feature_name>_matrix.json`).
* **Strict Black-Box Boundaries**:
  - All preconditions and assertions must focus exclusively on external system behavior and states.
  - References to internal codebase structures or implementation details are prohibited.

---

## 4. Caqui Tokenized Labeling Standard

Every test case and step name in the JSON array must strictly adhere to the Caqui Tokenized Labeling Standard.

### 4.1 Name Format
Every test name must conform to the following schema structure:
```
{<Identifier>} [<Scope-Tag>] <Component/Topology> (<Action/State>): <Behavioral Invariant Details>
```

### 4.2 Formatting & Syntax Constraints
* **Immutable 6-Glyph Alphanumeric Identifier**: The first token must be a unique, permanent 6-character alphanumeric anchor enclosed inside curly braces `{}` (e.g. `{tws6vh}`).
* **Standardized Bracketed Scope Tags**: The second token must match one of the system domains enclosed in square brackets `[]`:
  * `[Schema Compilation]`
  * `[Graph Retrieval]`
  * `[Graph Mutation]`
  * `[Contract Validation]`
  * `[CLI Command]`
  * `[Lifecycle Infrastructure]`
* **Grammatical Verb Mood Regulation**: The behavioral description suffix must rely entirely on active third-person present tense verbs (e.g., *Asserts*, *Rejects*, *Bypasses*, *Enforces*, *Suppresses*, *Rolls back*, *Halts*, *Stabilizes*).
* **Comma-Only Component List Delimiter**: If the `<Component/Topology>` or `<Action/State>` represents a compound list of entities or states, all items must be strictly delimited by commas followed by a single space (e.g., `(Delete, Set Conflict)`). The use of other logical operators, ampersands, or conjunctions is strictly forbidden.
* **No Arbitrary Numbers**: Hardcoded suite numbers (e.g., "Suite 1.1") are strictly forbidden within the text literal label to avoid indexing collisions during future refactoring passes.

