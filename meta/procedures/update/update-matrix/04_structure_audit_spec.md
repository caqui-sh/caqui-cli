# Technical Audit Specification: Matrix Structural Topography (04_structure_audit_spec.md)

This document defines the rules for auditing the format, schema compliance, and structural integrity of concrete update use-case matrices against the JSON payload blueprint.

> [!NOTE]
> This specific audit evaluates only the update use-case matrix's format, schema compliance, and structural integrity. All other audit dimensions are deferred to their respective stages.

---

## A. Document Structure & Schema Conformance

* **Schema & Type Integrity**:
  - The document must be a valid JSON array of objects.
  - Each object in the array must contain the required fields: `id`, `description`, `preExistingState`, `inputTrigger`, `expectedPostconditions` (array of strings), and `invariantBounds` (array of strings).
  - Each object must contain `existingTestStepId` if and only if the scenario modifies an established boundary contract. For all other scenarios, this field is prohibited and must be omitted.
* **Identifier Uniqueness & Ordering**:
  - Scenario IDs must be unique, formatted as `^SC-\d{2}$`, and increment sequentially starting at `SC-01` without gaps.
* **Content Completion**:
  - All fields must be complete and fully defined.
  - Symbolic representations of value domains are permitted.
* **Test Step Reference Verification**:
  - The unique 6-character identifier specified in `existingTestStepId` must resolve to an active test case or step within the preexisting E2E test files under `/meta/tests/`.
  - The target E2E test case or step must represent the legacy/pre-modified counterpart of the use case being updated.
* **Classification Accuracy**:
  - Scenarios updating preexisting boundary behaviors must define `existingTestStepId` matching their legacy E2E test's 6-character identifier to prevent misclassification as new additions.
