# Technical Audit Specification: Test Structural Conformance & Labeling (04_structure_audit_spec.md)

This document defines the rules for auditing the schema conformance, structural geometry, and labeling compliance of concrete update test specifications (`meta/history/<branch_name>_<version>/<feature_name>_tests.json`) against the master templates and naming standards.

> [!NOTE]
> This specific audit evaluates only the update test spec's schema conformance, structural geometry, and labeling compliance. All other audit dimensions are deferred to their respective stages.

---

## A. Schema & Structural Conformance

* **Root-Level Array Geometry**:
  - The document must compile as a single, valid JSON array of objects.
* **Node Categorization Integrity**:
  - **Root Nodes**: Top-level objects in the array must contain the `e2e_path` field specifying a workspace-relative path ending in `.e2e.ts`. It must target a fitting preexisting test file by default, though a new test file is permitted when necessary to avoid shoehorning tests into unrelated scopes.
  - **Leaf Nodes**: Terminal execution steps must contain both `preconditions` and `assertions` (arrays of strings) and must omit the `steps` field.
  - **Parent Nodes**: Grouping steps must contain a non-empty `steps` array of recursively conforming step objects.
* **Strict Type and Field Rules**:
  - `name`, `kind`, `e2e_path`, and `description` must be string types.
  - `kind` must equal either `"new"` or `"modification"`.
  - `preconditions` and `assertions` must be string arrays.
  - `steps` must be an array of objects.
  - Undocumented or custom fields are prohibited.
  - Placeholders, empty strings, and null values are prohibited.

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
