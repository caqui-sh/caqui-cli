# Technical Audit Specification: Control Review Structure & Referential Integrity (03_structure_audit_spec.md)

This document defines the rules for auditing the document layout, index sequencing, file naming, lineage, and cross-reference referential integrity of concrete update control review documents (`meta/history/<branch_name>_<version>/[index_2digit]_[feature_name]_control.md`).

> [!NOTE]
> This specific audit evaluates only the layout, lineage, and database referential integrity of the control review markdown file. All other audit dimensions are deferred to their respective stages.

---

## A. Control Review Structure & Referential Integrity Constraints

* **Blueprint & Formatting Compliance**:
  - The document must match the exact headings, numbering, and structure defined in the template of `review_update_spec.md`.
  - Issue list items must embed their associated `[DEBT-XXX]` ID directly in the issue title (e.g., `* **Issue Title (DEBT-XXX)**`) and use the sub-bullet structures defined in `review_update_spec.md`.
* **Sequence & Lineage**:
  - Files must be named `[index_2digit]_[feature_name]_control.md`, starting with index `00` and incrementing sequentially (e.g., `01`, `02`) without gaps.
  - For index > `00`, Section 1 (**Context & Changes Summary**) must contain a direct markdown link to the immediate predecessor control review document.
* **Referential Integrity**:
  - Every `[DEBT-XXX]` ID referenced in the Issues Matrix must exist as a unique `debt_id` in the corresponding database file (`<feature_name>_debt.json`).
  - **State Alignment**: New issues in Section 2 must align with database entries having `status` set to `"active"` or `"deferred"`. Resolved issues in Section 2 must align with database entries having `status` set to `"resolved"` or `"partially_resolved"` with their `resolved_at_index` matching the current control review index.
