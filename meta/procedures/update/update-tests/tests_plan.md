# Procedural Plan for Implementing Test Specifications (tests_plan.md)

This document is the **procedural plan** for implementing the declarative specifications defined in [tests_update_spec.md](/meta/procedures/update/update-tests/tests_update_spec.md). It outlines the chronological sequence of execution steps, coding practices, and verification commands required to translate a declarative test specification (`meta/history/<branch_name>_<version>/<feature_name>_tests.json`) into executable integration test suites.

---

## Phase 1: Test Case Code Structure & Hierarchical Step Nesting

Set up the test structure in code, utilizing nested steps to map the hierarchical specification.

* **Step 1.1: Locate Target Test Files & Enforce Single File-Level Suite Block**
  - Read the `e2e_path` property from the declarative test specification.
  - Target a fitting preexisting test file by default, permitting new test files only when necessary to avoid shoehorning.
  - Ensure each test file contains exactly **one** top-level test block acting as the container suite for that file. Never create a new top-level suite container when adding tests to a preexisting file. Instead, locate the file's single preexisting block to house the new tests.
* **Step 1.2: Implement Hierarchical Nesting**
  - Map all JSON test scenarios and steps to subtests via native nested step calls.
  - For parent test steps that group child test steps (using the `steps` array in the JSON specification), implement them recursively:
    - Pass the step context parameter to the parent step function.
    - Invoke the child nested steps on that parent context.
* **Step 1.3: Synchronize Labels and Identifiers**
  - Ensure the `name` argument of each test step matches the exact string from the `name` field of the corresponding JSON item 1-to-1.
* **Step 1.4: Handle Test Modifications vs. New Additions**
  - Read the `kind` property for each test case/step from the declarative test specification.
  - **For `"modification"`**: Locate the preexisting test case/step in the target file using its unique, legacy 6-character identifier. Modify and update the existing implementation block in place (inputs, preconditions, and assertions) rather than creating a new test block. Keep the 6-character ID token identical, but update the remaining name segments to reflect the new test structure.
  - **For `"new"`**: Implement a brand-new test block with a newly generated name and a new 6-character identifier.

### Hierarchical Deno Test Structure Template:
```typescript
// Preexisting single top-level suite container in the targeted test file:
Deno.test({
  name: "{<suite_6_glyph_id>} [<scope_tag>] <suite_component_topology> (<suite_action_state>): <active_third_person_present_tense_description>",
  async fn(t) {
    
    // Step of steps (Parent test step):
    await t.step({
      name: "{<parent_6_glyph_id>} [<scope_tag>] <parent_component_topology> (<parent_action_state>): <active_third_person_present_tense_description>",
      async fn(t) {
        
        // Leaf-level step:
        await t.step({
          name: "{<child_6_glyph_id>} [<scope_tag>] <child_component_topology> (<child_action_state>): <active_third_person_present_tense_description>",
          async fn() {
            // 1. Setup preconditions (Phase 2)
            // 2. Execute target operations (Phase 3)
            // 3. Run black-box assertions (Phase 3)
          }
        });
        
      }
    });
    
  }
});
```

---

## Phase 2: Precondition Orchestration & State Initialization

Prepare the system state and configuration templates prior to running the validations.

* **Step 2.1: Initialize Precondition States**
  - Implement the setup routines required to establish the state declared in the `preconditions` array of the JSON item.
  - Initialize required assets or state configurations exclusively through public boundary entry points.
  - Prioritize leveraging and reusing established schema definitions to maintain configuration consistency.
  - Use and extend the established master schema file (`master_test_schema.cq`) unless the test instance dictates using a separate or new schema configuration.
* **Step 2.2: Leverage Closures for Shared Context**
  - Initialize shared context at the parent level.
  - Access parent context within nested child scopes to avoid redundant setup overhead.
* **Step 2.3: Enforce Resource and Environment Isolation**
  - Enforce absolute isolation to prevent environment cross-contamination.
  - Execute test runs over unique, isolated temporary filesystem workspaces.
  - Dynamically allocate interface endpoints to prevent address or binding collisions.

---

## Phase 3: Boundary Execution & Assertion Construction

Execute target operations and validate the boundary outcomes without exposing underlying implementation details.

* **Step 3.1: Execute Target Boundary Action**
  - Trigger the system interaction or transaction at the public interface boundary.
  - Pass the structured inputs or options defined by the preconditions and test triggers.
* **Step 3.2: Construct Black-Box Boundary Assertions**
  - Write assertions that validate the outputs, states, and return shapes emitted at the public boundary interfaces against the assertions list in the JSON spec.
  - Verify behaviors exclusively through public outputs and side-effects. Never inspect internal implementation modules or private state spaces directly.
* **Step 3.3: Assert Error and Exceptional Path Contracts**
  - Verify that exceptional pathways and invalid inputs resolve to expected outcomes.
* **Step 3.4: Enforce Isolation and Teardown**
  - Deterministically clean up all active execution resources and filesystem side-effects under all termination states.

---

## Phase 4: Implementation Completeness & Compliance Verification

Ensure that the implemented test structure matches the declarative specification exactly and conforms to labeling requirements.

* **Step 4.1: Verify Spec-to-Code Coverage**
  - Compare the implemented test blocks in the target physical file under `<e2e_path>` against the declarative test cases in the JSON specification.
  - Confirm that every JSON test case and child step has been implemented 1-to-1, with no omissions or undocumented additions.
* **Step 4.2: Audit Label Synchronization**
  - Verify that the test name strings in the code are identical to the JSON `name` fields.
* **Step 4.3: Verify Syntax and Compilation Integrity**
  - Run syntax and type checks on the test files to ensure they compile cleanly without syntax or import errors:
    ```bash
    deno check <e2e_path>
    ```
  - Note: Do not run the full test suite expecting a passing run, as the underlying update capabilities may not yet be implemented at this stage.
