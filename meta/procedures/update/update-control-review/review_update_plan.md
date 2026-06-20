# Procedural Plan for Writing Update Control Reviews (review_update_plan.md)

This document is the **procedural counterpart** to the declarative update control review blueprint (`review_update_spec.md`). It defines the chronological sequence of steps required to write a concrete update control review document at `meta/history/<branch_name>_<version>/[index_2digit]_[feature_name]_control.md`.

---

## Phase 1: Initial Context & Delta Analysis

Establish the document metadata and define the historical baseline or modification deltas.

* **Step 1.1: Name & Index Selection**
  - Determine the directory path using the active branch name and version: `meta/history/<branch_name>_<version>/`
  - Assign the index: use `00` for the baseline review, and increment sequentially (e.g., `01`, `02`) without gaps for subsequent iterations.
* **Step 1.2: Summarize Context & Changes**
  - Populate Section 1 (**Context & Changes Summary**).
  - For baseline (`00`): Describe the technical path chosen, the rationale, and the context.
  - For subsequent deltas (> `00`): Describe the modifications made since the last review, referencing and linking to the previous control document(s) in this series directly within the text.

---

## Phase 2: Issues Identification & Assessment

Conduct an architectural evaluation of design concessions, risks, and technical debt.

* **Step 2.1: Populate the Issues Matrix**
  - Populate Section 2 (**Issues Matrix**).
  - For baseline (`00`): List all initial architectural issues, embedding the required technical debt ID (`[DEBT-XXX]`) in each issue title, and detailing the concession and associated risk/impact.
  - For subsequent deltas (> `00`): Under **New Issues**, document issues introduced in this iteration. Under **Resolved Issues**, document issues resolved or mitigated in this iteration, including a brief explanation of how they were resolved and links to the relevant code changes described in Section 1.
