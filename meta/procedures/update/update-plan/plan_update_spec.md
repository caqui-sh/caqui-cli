# Update Implementation Plan Specification & Blueprint (plan_update_spec.md)

This document defines the template and requirements for concrete update implementation plans (`meta/history/<branch_name>_<version>/<feature_name>_plan.md`).

An update implementation plan describes the sequence of phases and static analysis or compiler checks needed to implement an update. It is designed to bridge the declarative specifications—specifically the Update Abstract (`<feature_name>_abstract.md`), Surface-Area Spec (`<feature_name>_surface.md`), Use-Case Matrix (`<feature_name>_matrix.json`), and Test Specification (`<feature_name>_tests.json`)—into concrete codebase changes. The ultimate objective is to successfully implement the update surface-area and pass all of the new and updated implemented tests while not regressing on the established test suite.

---

## 1. Core Principles of Update Implementation Plans

To ensure systematic execution and clean codebase integration, every concrete update implementation plan must adhere to the following principles:

* **Macro-Architectural Focus**:
  - Prioritize defining structural boundaries, dependency directions, and subsystem interfaces.
  - Preserve local implementation autonomy while enforcing global structural alignment.
* **Tailored Sequencing**:
  - Group tasks into logical, chronological phases specific to the update's requirements.
  - Every step must include a verification command confirming successful compilation of the codebase.
* **Separation of Concerns**:
  - Keep the plan focused on execution steps and verification gates.
  - Do not duplicate content from declarative specifications.

---

## 2. Sequencing Strategies

When partitioning an update's implementation into phases, sequence the workflow using these systems-level strategies:

* **Directional Staging**:
  - Sequence implementation phases to ensure compilation integrity is preserved at every boundary.
* **Cohesive Phase Boundaries**:
  - Design each phase to be a self-contained, logical milestone.
  - Avoid staging changes in a manner that leaves interfaces broken or incomplete at phase boundaries.
* **Milestone Verification Gates**:
  - Verify compilability at each phase boundary before proceeding, deferring test execution to the final integration run.

---

## 3. Micro Phase Architecture

When defining individual phases and tasks (steps) in the plan, follow these rules to structure the micro-architecture of each step:

* **Implementation Agility**:
  - Describe tasks by their integration outcomes and boundary interfaces.
  - Avoid prescribing implementation details.
* **Preserving Design Paths**:
  - Keep task descriptions focused on the expected outcome of the step, leaving the developer free to choose the cleanest design path and avoid falling into narrow implementation rabbit holes.
* **Black-Box Checkpoints**:
  - Keep step definitions decoupled from internal code state.
  - Intermediate verification stages must focus exclusively on the compilation of the codebase.

---

## 4. Concrete Update Implementation Plan Document Template

Below is the standard, markdown-formatted template that must be used for every concrete update implementation plan.

---

```markdown
# Target Update Implementation Plan: [Update Name]

* **Status**: [Draft / Approved / Completed]
* **Target Version / Release**: [X.Y.Z]
* **Abstract Companion**: [Link to <update_name>_abstract.md (e.g. /meta/history/<branch_name>_<version>/<update_name>_abstract.md)]
* **Surface-Area Companion**: [Link to <update_name>_surface.md (e.g. /meta/history/<branch_name>_<version>/<update_name>_surface.md)]
* **Use-Case Companion**: [Link to <update_name>_matrix.json (e.g. /meta/history/<branch_name>_<version>/<update_name>_matrix.json)]
* **Tests Companion**: [Link to <update_name>_tests.json (e.g. /meta/history/<branch_name>_<version>/<update_name>_tests.json)]

---

## Architectural & Process Guardrails

All development steps in this plan must comply with the constant negative constraints:

* **Macro-Architecture**:
  - *No High-Coupling Layer Violations*: Domain logic must remain entirely independent and must never import or depend on outer subsystems.
  - *No Implicit State Coupling*: Do not coordinate execution or share mutable state across subsystem boundaries; localize mutability to avoid implicit temporal dependencies.
  - *No Shoehorned Integrations*: Do not force update logic into existing structures using localized workarounds, hacks, or ad-hoc adaptations; stage clean refactoring of core structures if the current design does not naturally support the update.
* **Foundational Design**:
  - *No Unnecessary Indirection*: Do not introduce intermediate layers of indirection when direct usage suffices.
  - *No Premature Generalization*: Do not introduce generic abstractions when a single concrete implementation suffices.
  - *No Over-Engineering*: Do not employ complex design patterns when simpler constructs suffice.
  - *No Over-Encapsulation*: Do not restrict visibility or wrap code beyond necessity.
* **Developer Process**:
  - *No Monolithic Phase Implementation*: Complete, compile, and verify each phase chronologically before moving to the next.
  - *No Short-Sighted Expediency*: Do not implement narrow, localized workarounds or temporary hacks to satisfy immediate constraints, compromising holistic system design and clean integration.
  - *No Premature Performance Tuning*: Do not implement performance optimizations without profiling evidence.

---

<!-- 
ADD UPDATE PHASES HERE
Sequence the development workflow into logical, chronological phases.
Use the following format for each phase and step:

## Phase [N]: [Dynamic Phase Title]
[High-level objective of this phase, defining the target systems and files modified.]

* **Step [N].[M]: [Step Title]**
  - [Actionable task description, specifying the changes to be made.]
  - **Verification**: [compilation command]
-->

---

## Verification Pipeline Run

Verify the correctness of all changes by following the formal test execution and static analysis guidelines outlined in [verification_plan.md](/meta/procedures/verification_plan.md). This process must be executed iteratively (looping through isolation, fixes, and validation) until all verification phases pass cleanly.

* **Execute Verification Procedures**
  - Follow the step-by-step static analysis and testing pipeline procedures defined in [verification_plan.md](/meta/procedures/verification_plan.md) to ensure compilation correctness and 100% test coverage safety.

* **Handling Verification Failures & Recovery**
  - **Isolate the Failure**:
    - For compilation or lint failures, run targeted checks on the specific crate (`cargo check -p <crate_name>` / `cargo clippy -p <crate_name>`) to isolate the error.
    - For E2E test failures, inspect logs to locate the system boundary interface or transition state that failed.
  - **Implement a Recovery Fix**:
    - Focus strictly on correcting implementation logic inside the codebase, ensuring that all fixes still strictly adhere to the constant negative constraints in the **Architectural & Process Guardrails**.
    - Loop back to **Execute Verification Procedures** to re-run Phase 1 and Phase 2, repeating this cycle until the entire pipeline passes successfully.
  - **Exception: E2E Test Alignment**:
    - If a minor E2E test alignment is necessary to match system boundary updates, you must adhere strictly to these constraints:
      > [!CAUTION]
      > **TEST IMMUTABILITY & SPECIFICATION INTEGRITY**
      > * **The Immutable Step Identifier**: The unique 6-character identifier token in the test/step name **MUST NEVER BE CHANGED** under any circumstances, serving as the permanent anchor of the test invariant. Other name segments are malleable and may be updated to reflect the modified test structure.
      > * **Permitted Aesthetic Alterations**: Minor aesthetic adjustments or alterations within the step body are acceptable *only* when absolutely necessary to align with system boundary updates.
      > * **No Dilution or Bending**: Any step body alteration **must not** weaken, bypass, or bend the core functional assertions or logical rigor of the test. Commenting out assertions, deleting logic boundaries, or disabling test checks to bypass failures remains strictly prohibited.
```
