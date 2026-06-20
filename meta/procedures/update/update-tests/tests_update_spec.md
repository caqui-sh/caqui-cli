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
  - Test entries must declare the scenarios they validate.
  - Updates to preexisting behavior must target the corresponding pre-existing test step to modify it directly, preventing redundant test paths.
* **Test File Cohesion & Context Reuse**:
  - Target existing execution files by default, creating new ones only when contextually necessary.
  - Nest steps within existing hierarchies when scope and preconditions align, avoiding duplicate setups.
* **Coverage Mapping**:
  - Validation nodes and companion matrix scenarios must form a strict 1-to-1 mapping; structural nodes are excluded.
* **Hierarchical Step Grouping**:
  - Group test execution paths using recursive nested step arrays to model sequential parent-child execution flows.
* **Declarative Assertions**:
  - Assertions must focus entirely on what behavioral invariants or contract shapes are verified, omitting execution and implementation details.

---

## 2. Concrete Update Test JSON Schema

All test scenarios must be compiled into a single flat JSON array of objects. Each object in the array represents a test step node and must belong to one of four explicit node kinds.

### 2.1 Output Payload Blueprint

```json
[
  {
    "name": "<tokenized_test_suite_name_starting_with_6_glyph_identifier>",
    "nodeKind": "suite",
    "changeKind": "new | modification",
    "description": "<complete_suite_purpose_description>",
    "e2e_path": "<relative_path_to_test_file>.e2e.ts"
  },
  {
    "name": "<tokenized_group_name_starting_with_6_glyph_identifier>",
    "nodeKind": "abstractGroup | functionalGroup",
    "changeKind": "new | modification",
    "description": "<complete_group_purpose_description>",
    "parentStepId": "<parent_6_glyph_identifier>",
    "preconditions": [
      "<required_shared_setup_precondition>"
    ]
  },
  {
    "name": "<tokenized_validation_name_starting_with_6_glyph_identifier>",
    "nodeKind": "validation",
    "changeKind": "new | modification",
    "description": "<complete_validation_purpose_description>",
    "parentStepId": "<parent_6_glyph_identifier>",
    "scenarioId": "<matrix_scenario_identifier>",
    "preconditions": [
      "<required_step_precondition>"
    ],
    "assertions": [
      "<validated_behavior_invariant>"
    ]
  }
]
```

### 2.2 Field Specifications & Structural Constraints

Each object in the flat JSON array must conform to the field rules of its designated `nodeKind`:

| Field Name | Type | Required | Allowed In | Description |
| :--- | :--- | :---: | :--- | :--- |
| `name` | String | Yes | All | The tokenized test or step name conforming to the labeling standard. Must start with `{6-glyph-id}`. |
| `nodeKind` | String | Yes | All | Specifies the node kind: `"suite"`, `"abstractGroup"`, `"functionalGroup"`, or `"validation"`. |
| `changeKind` | String | Yes | All | Specifies if the test or step is newly added (`"new"`) or modifying preexisting tests (`"modification"`). |
| `description` | String | Yes | All | A complete description explaining the purpose of the test suite, group, or validation step. |
| `e2e_path` | String | Yes (for suite) | `suite` only | The relative path to the physical test execution file (must end in `.e2e.ts`). |
| `parentStepId` | String | Yes (for non-suite) | All except `suite` | The unique 6-character identifier token of the parent step. |
| `scenarioId` | String | Yes | `validation` only | The mapped scenario identifier (`SC-XX`) from the Use-Case Matrix. |
| `preconditions` | Array of Strings | Yes | `functionalGroup`, `validation` | Declarative statements defining the required initial states or preconditions. For `functionalGroup`, must be non-empty. |
| `assertions` | Array of Strings | Yes | `validation` only | Declarative statements defining the validated behavioral invariants or outcomes. Must be non-empty. |

Prohibited fields for any `nodeKind` must be omitted from the JSON object (cannot be passed as null or empty values).

## 3. Payload Integrity Invariants

* **Identifier & Labeling Compliance**:
  - All test and step names must strictly conform to the Caqui Tokenized Labeling Standard.
* **Specification & Modification Model**:
  - **File-Level Delta**: The specification document is a delta containing only newly introduced or modified nodes; unaltered pre-existing test steps must be omitted.
  - **Node-Level Completeness**: Every node represents its complete post-update state rather than a partial diff. For modified nodes:
    - The assertions and preconditions must be a complete 1-to-1 transform of the companion Use-Case Matrix scenario's expected postconditions, invariant bounds, and preexisting states.
    - The description must capture the final post-update purpose.
    - The pre-existing unique identifier must be preserved.
* **Parent Step Resolution & Ghost Prevention**:
  - Every parent reference must resolve to either a locally defined node or an active pre-existing step in the target codebase file.
  - Circular reference chains are prohibited.
* **Validation Node Placement & Anti-Shoehorning**:
  - Validation nodes must be nested under parents that align with their logical scope and precondition environment; mismatching nesting is prohibited.
  - Preexisting parents may be reused only if their setup aligns with the required validation context.
* **Scenario ID Resolution & Co-location**:
  - The `scenarioId` field must map to a valid scenario ID defined in the co-located companion Use-Case Matrix (`<feature_name>_matrix.json`).
* **Strict Black-Box Boundaries**:
  - All preconditions and assertions must focus exclusively on external system behavior and states. References to internal codebase structures or implementation details are prohibited.

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

