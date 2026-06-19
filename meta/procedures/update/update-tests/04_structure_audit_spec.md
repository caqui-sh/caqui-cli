# Technical Audit Specification: Test Structural Conformance & Labeling (04_structure_audit_spec.md)

This document defines the rules for auditing the schema conformance, structural geometry, and labeling compliance of concrete update test specifications (`meta/history/<branch_name>_<version>/<feature_name>_tests.json`) against the master templates and naming standards.

> [!NOTE]
> This specific audit evaluates only the update test spec's schema conformance, structural geometry, and labeling compliance. All other audit dimensions are deferred to their respective stages.

---

## A. Schema & Structural Conformance

* **Root-Level Array Geometry**:
  - The document must compile as a single, flat JSON array of objects.
* **Node Kind Conformity**:
  - Each object in the array must define `nodeKind` (one of `"suite"`, `"abstractGroup"`, `"functionalGroup"`, or `"validation"`).
  - Each object must define `changeKind` (either `"new"` or `"modification"`).
  - Each object must define a non-empty `description` string.
* **Node Kind Specific Constraints**:
  - **`suite`**:
    - Must contain `e2e_path` specifying a workspace-relative path ending in `.e2e.ts`.
    - Must omit `parentStepId`, `scenarioId`, `preconditions`, and `assertions`.
  - **`abstractGroup`**:
    - Must contain `parentStepId` pointing to the parent's 6-character ID.
    - Must omit `e2e_path`, `scenarioId`, `preconditions`, and `assertions`.
  - **`functionalGroup`**:
    - Must contain `parentStepId` pointing to the parent's 6-character ID.
    - Must contain `preconditions` (a non-empty array of strings).
    - Must omit `e2e_path`, `scenarioId`, and `assertions`.
  - **`validation`**:
    - Must contain `parentStepId` pointing to the parent's 6-character ID.
    - Must contain `scenarioId` (a string matching `^SC-\d{2}$`).
    - Must contain `preconditions` (an array of strings).
    - Must contain `assertions` (a non-empty array of strings).
    - Must omit `e2e_path` and `trace_references`.
* **Field Validity & Type Constraints**:
  - `name`, `nodeKind`, `changeKind`, `description`, `e2e_path`, `parentStepId`, and `scenarioId` must be string types.
  - `preconditions` and `assertions` must be arrays of strings.
  - Undocumented or custom fields, placeholders, empty strings, and null values are prohibited.
* **Parent Step Resolution Invariants**:
  - Every `parentStepId` (string matching `^[a-z0-9]{6}$`) must resolve to either:
    1. A node defined locally within the same JSON array.
    2. A preexisting E2E test step containing the matching 6-character identifier token within the target physical E2E test file (defined by the ancestor suite's `e2e_path`).
  - Circular parent-child reference chains are strictly prohibited.
* **Validation Node Placement & Anti-Shoehorning**:
  - Validation steps must only be nested under a parent group whose setup environment and preconditions match the validation's required state. Shoehorning validation steps into unrelated groups is prohibited.
  - Reusing a pre-existing parent group is permitted as an option only when the setup context aligns. Otherwise, a new group or direct suite attachment must be declared.

---

## B. Caqui Tokenized Labeling Standard Conformance

* **Label Syntax Format**:
  - Every `name` field must strictly match the format: `"{<ID>} [<SCOPE>] <TOPOLOGY> (<STATE>): <DESCRIPTION>"`.
* **Segment Constraints**:
  - **Alphanumeric ID**: Must be a unique, permanent, 6-character alphanumeric string inside `{}`. No sequential naming.
  - **Scope Tag**: Must match one of the allowed system domains inside `[]`:
    * `[Schema Compilation]`
    * `[Graph Retrieval]`
    * `[Graph Mutation]`
    * `[Contract Validation]`
    * `[CLI Command]`
    * `[Lifecycle Infrastructure]`
  - **Verb Mood**: The description segment must use active third-person present tense verbs.
  - **List Delimiters**: Compound elements must be delimited strictly by a comma followed by a space.
  - **No Suite Numbers**: Hardcoded suite/sequence numbers are prohibited.
