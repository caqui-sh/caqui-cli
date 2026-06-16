# Technical Audit Procedure (dimension_audit_plan.md)

This document defines the generic procedural plan for executing an audit using a companion, dimension-specific audit specification against a target file.

---

## A. Technical Audit Execution Loop

To execute an audit, systematically evaluate the target file against the active audit specification ruleset:

* **Target Scope Mapping**: Locate and isolate all sections in the target file that correspond to the active audit ruleset.
* **Sequential Evaluation**: Iterate systematically through each constraint in the active audit specification to verify target compliance.
* **Issue Compilation**: Catalog and detail all technical issues or validation gaps immediately upon discovery during the evaluation, conforming to the schema defined in [dimension_audit_spec.md](/meta/procedures/dimension_audit_spec.md).
* **Transaction Resolution**: Exhaustively and rigorously execute the audit to completion to compile all failures into a unified issue log, proposing the compiled log for review.

---

## B. Audit Strategies

To maximize the coverage and rigor of the evaluation, apply the following complementary audit strategies:

* **Affirmative Verification**:
  - *Method*: Verify that all required elements, success criteria, and direct constraints defined by the active audit specification are explicitly present, well-formed, and internally consistent.
  - *Target Findings*:
    - **Errors and Flaws**: Explicitly present content that violates a direct, explicit rule or is logically invalid within the active constraints.
    - **Discrepancies**: Explicitly present content that is inconsistent or mismatched internally, or misaligned with external specifications defined by the active constraints.
* **Adversarial Refutation**:
  - *Method*: Evaluate the target specification with strict skepticism, questioning implicit assumptions, probing boundaries, and appraising adaptability.
  - *Target Findings*:
    - **Omissions and Blindspots**: Necessary elements, scenarios, or validation rules required by the active constraints that are completely absent.
    - **Ambiguities and Vagueness**: Content that is present but expressed with loose phrasing or insufficient detail, leaving its compliance undefined or unverifiable under the active constraints.
    - **Short-Sightedness**: Content that satisfies immediate rules but violates portability, durability, or adaptability requirements defined by the active constraints.
