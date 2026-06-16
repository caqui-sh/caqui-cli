# Procedural Plan for Writing Update Implementation Plans (plan_update_plan.md)

This document is the **procedural counterpart** to the declarative update implementation plan specification ([plan_update_spec.md](/meta/procedures/update/update-plan/plan_update_spec.md)). It defines the chronological sequence of steps required to write and verify a concrete update implementation plan at `meta/history/<branch_name>_<version>/<feature_name>_plan.md`.

---

## Phase 1: Sequencing & Phase Partitioning Design

Analyze the companion declarative specifications and partition the implementation workflow into logical, chronological, and compilable phases.

* **Step 1.1: Map Dependency Hierarchy (Directional Staging)**
  - Map the system's structural dependency hierarchy based on the interface contracts defined in the companion Surface-Area Spec (`<feature_name>_surface.md`).
  - Sequence implementation phases to ensure compilation integrity is preserved at every boundary.
* **Step 1.2: Establish Cohesive Phase Boundaries**
  - Group target subsystems and components so that each phase represents a self-contained, logical milestone.
  - Avoid staging changes in a manner that leaves interfaces broken or incomplete at phase boundaries.
* **Step 1.3: Formulate Phase Headers and Objectives**
  - For each mapped phase, draft a phase header (`## Phase [N]: [Dynamic Phase Title]`) and a brief high-level objective defining the target systems and files to be modified:
    ```markdown
    ## Phase [N]: [Dynamic Phase Title]

    [High-level objective of this phase, defining the target systems and files modified.]
    ```

---

## Phase 2: Micro-Phase Task & Verification Architecture

Build granular, implementation-agile execution steps inside each phase, ensuring each step has a clear verification boundary.

* **Step 2.1: Define Implementation-Agile Step Tasks**
  - For each phase, write the sequential steps using the standard format: `* **Step [N].[M]: [Step Title]**`.
  - Describe each task by its integration outcomes and boundary interfaces, avoiding prescribing internal implementation details.
* **Step 2.2: Establish Milestone Verification Gates**
  - For every step, write a concrete, executable verification command under the **Verification** key.
  - Ensure that intermediate verification stages verify only the compilation of the codebase.
  - Example formatting:
    ```markdown
    * **Step [N].[M]: [Step Title]**
      - [Actionable task description, specifying the changes to be made.]
      - **Verification**: [compilation command]
    ```
* **Step 2.3: Maintain Separation of Concerns**
  - Audit the drafted steps to ensure they focus purely on procedural execution. Do not duplicate content from the declarative specifications; instead, refer to them by section or link.

---

## Phase 3: Verification Gates & Pipeline Integration

Integrate the mandatory system verification checks to verify correctness before integration.

* **Step 3.1: Confirm Verification Pipeline Run Section**
  - Verify that the mandatory `## Verification Pipeline Run` section is correctly placed at the end of the implementation plan and matches the template:
    ```markdown
    ## Verification Pipeline Run

    Verify the correctness of all changes by following the formal test execution and static analysis guidelines outlined in [verification_plan.md](/meta/procedures/verification_plan.md).

    * **Execute Verification Procedures**
      - Follow the step-by-step static analysis and testing pipeline procedures defined in [verification_plan.md](/meta/procedures/verification_plan.md) to ensure compilation correctness and 100% test coverage safety.
    ```
