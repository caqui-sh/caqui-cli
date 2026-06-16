# Procedural Plan for Writing Update Test Specifications (tests_update_plan.md)

This document is the **procedural counterpart** to the declarative update test specification blueprint (`tests_update_spec.md`). It defines the chronological sequence of steps required to write a concrete update test specification at `meta/history/<branch_name>_<version>/<feature_name>_tests.json`.

---

## Phase 1: Test Vector & Coverage Mapping

Establish the target execution files and map the scenarios requiring verification.

* **Step 1.1: Identify Target Test Files**
  - Identify the physical test execution files targeted by the update (ending in `.e2e.ts`).
  - Target a fitting preexisting test file by default to preserve workspace cohesion, permitting new test files when necessary to avoid shoehorning tests into unrelated scopes.
* **Step 1.2: Establish Traceability Mapping**
  - Map each test scenario directly to the scenario IDs (`SC-XX`) defined in the companion Use-Case Matrix (`<feature_name>_matrix.json`).
  - For any scenario specifying an `existingTestStep`, locate the target preexisting E2E test step by its unique 6-character identifier, ensuring the test specification references and modifies this step directly rather than creating a new one.
  - Ensure every matrix scenario is accounted for to guarantee complete test coverage.

---

## Phase 2: Test Case & Step Definition

Populate the test array with declarative, black-box scenarios and recursive execution steps.

* **Step 2.1: Formulate Root-Level Test Cases**
  - Define top-level test cases in the JSON array with relative `e2e_path` properties, descriptions, and name fields conforming strictly to the **Caqui Tokenized Labeling Standard** defined in `tests_update_spec.md`.
  - Populate the `kind` field with `"new"` if the test case is brand-new, or `"modification"` if it adapts a preexisting test case.
  - Populate the `trace_references` array with the target scenario IDs.
* **Step 2.2: Define Preconditions & Assertions**
  - Specify the required initial system states or inputs under the `preconditions` array.
  - Specify the expected observable system outcomes or boundary invariants under the `assertions` array.
  - Ensure all assertions and preconditions focus exclusively on system boundary behaviors and omit internal codebase or execution details.
* **Step 2.3: Model Step Hierarchies**
  - For sequential execution paths, map recursive nested child step arrays to model parent-child execution flows.
  - For each nested step, specify the `kind` field as `"new"` or `"modification"` as appropriate.
  - For leaf steps, define granular `preconditions` and `assertions` to ensure complete traceability.
