# Technical Audit Specification: Plan Document Structure & Format (05_structure_audit_spec.md)

This document defines the rules for auditing the **Structure & Format (Structural Topography & Template Conformance)** of concrete update implementation plans (`meta/history/<branch_name>_<version>/<feature_name>_plan.md`) against [plan_update_spec.md](/meta/procedures/update/update-plan/plan_update_spec.md).

> [!NOTE]
> This specific audit evaluates only document form, layout correctness, metadata headers, and template compliance. All other audit dimensions are deferred to their respective stages.

---

## A. Document Anatomy & Template Conformance

* **Mandatory Document Identity Header**:
  - The plan must begin with a level-1 header mapping to the actual update name (e.g., `# Target Update Implementation Plan: [Update Name]`).
  - The metadata block must contain exactly the following keys, fully populated and structured as a bulleted list:
    - `* **Status**:` followed by exactly one of the status values: `Draft`, `Approved`, or `Completed`.
    - `* **Target Version / Release**:` followed by a version identifier.
    - `* **Abstract Companion**:` followed by a valid project-root relative link (starting with `/` and pointing to `/meta/history/<branch_name>_<version>/<update_name>_abstract.md`).
    - `* **Surface-Area Companion**:` followed by a valid project-root relative link (starting with `/` and pointing to `/meta/history/<branch_name>_<version>/<update_name>_surface.md`).
    - `* **Use-Case Companion**:` followed by a valid project-root relative link (starting with `/` and pointing to `/meta/history/<branch_name>_<version>/<update_name>_matrix.json`).
    - `* **Tests Companion**:` followed by a valid project-root relative link (starting with `/` and pointing to `/meta/history/<branch_name>_<version>/<update_name>_tests.json`).
* **Verbatim Guardrails Enforcement**:
  - The document must contain the level-2 header `## Architectural & Process Guardrails` followed verbatim by the constant negative constraints list defined in the master specification.
  - No constraints may be deleted, added, or modified.
* **Dynamic Phase and Step Numbering**:
  - Dynamic phases must follow the heading format: `## Phase [N]: [Dynamic Phase Title]` (where N is a sequential integer starting at 1).
  - Every step within a phase must follow the exact list format: `* **Step [N].[M]: [Step Title]**` (where N is the phase number and M is the sequential step number starting at 1).
  - Each step must include exactly two mandatory indented sub-bullets using hyphens (`-`):
    - An actionable task description bullet detailing the changes to be integrated.
    - A verification checkpoint bullet starting with the bolded label `- **Verification**:` followed by a valid compilation check command.
* **Mandatory Verification End-Block**:
  - The plan must terminate with the verbatim `## Verification Pipeline Run` section linking to `/meta/procedures/verification_plan.md`.
* **Standard Section Dividers**:
  - Main section blocks must be separated by horizontal rule dividers (`---`) exactly as structured in the template.

---

## B. Syntactic & Formatting Constraints

* **Universal Link Portability**:
  - All relative file references and hyperlinks must be project-root relative (starting with `/`). Absolute paths tied to local environments are strictly prohibited.
* **Elimination of Boilerplate Placeholders**:
  - The plan must not contain any placeholder values, template prompts, or empty template brackets (e.g., `[Update Name]`).
