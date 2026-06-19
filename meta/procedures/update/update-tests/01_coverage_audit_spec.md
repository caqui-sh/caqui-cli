# Technical Audit Specification: Test Traceability & Coverage (01_coverage_audit_spec.md)

This document defines the rules for auditing the traceability and coverage alignment of concrete update test specifications (`meta/history/<branch_name>_<version>/<feature_name>_tests.json`) against the companion Use-Case Matrix. It ensures that the test specification completely covers all behavioral scenarios defined for the update.

> [!NOTE]
> This specific audit evaluates only the update test spec's traceability and scenario coverage. All other audit dimensions are deferred to their respective stages.

---

## A. Test Traceability & Coverage Constraints

* **100% Scenario Coverage**:
  - Every scenario identifier defined in the co-located Use-Case Matrix (`<feature_name>_matrix.json`) must be targeted by the `scenarioId` of exactly one `validation` node in the flat Test Spec.
* **Scenario ID Resolution**:
  - The `scenarioId` value declared in each `validation` node must match an existing scenario ID in the Use-Case Matrix.
* **Assertion Sufficiency**:
  - Test assertions must verify the expected postconditions and preserve the invariant bounds defined for each scenario in the matrix.
* **Non-Redundant Validation Paths**:
  - Duplicate validation paths targeting identical state transitions and inputs are prohibited.
* **Existing Test Case Refinement**:
  - Matrix scenarios defining `existingTestStepId` must map to validation steps with `changeKind` as `"modification"` that preserve the pre-existing 6-character ID token.
