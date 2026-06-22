# Universal Audit Cycle Graph (universal_audit_cycle.meta.md)

This document defines the **Universal Audit Cycle Graph**. Rather than pretending audits are perfectly linear, this graph models the audit process as a 5-stage state machine where each stage executes the target [**Audit Plan**](/meta/procedures/audit/audit.plan.md) against a specific subset of dimensions, and transitions are governed by an iterative remediation feedback loop.

---

## 1. The Audit Cycle State Machine

The audit cycle is structured as a 5-stage state machine:

1. **Stage 1: Content Scope & Identity (Graph Boundaries)**
   - **Inputs**: Inclusion, Exclusion, Semantic Uniqueness
   - **Pass Criteria**: All expected content is successfully identified and included (no omissions), out-of-scope details are excluded, and the node set is free of redundant or overlapping elements.
   - **Remediation**: Adjust boundary inputs or merge/delete duplicate elements. Loop back to Stage 1.
   
2. **Stage 2: Macro Graph Architecture (Skeletal & Scale Setup)**
   - **Inputs (Entangled)**: Macro Structure, Macro Depth, Macro Topology, Depth Continuity
   - **Pass Criteria**: Folder tree, file naming, section outline hierarchies, nested zoom scales, reference linkages, and transitional flow steps resolve cleanly as a coherent, continuous, non-cyclic macro graph.
   - **Remediation**: Reconnect reference paths, adjust parent-child hierarchy, rewrite heading templates, or insert transitional nodes. Loops back to Stage 2 (or Stage 1 if changes alter the scope boundary).
   
3. **Stage 3: Substance, Truth & Internal Alignment (Substance Auditing)**
   - **Inputs**: Semantic Relevance, Semantic Veracity, Internal Alignment
   - **Pass Criteria**: All content nodes in the constructed graph are useful/necessary, factually true, and logically consistent with one another (no clashing perspectives or contradictory statements).
   - **Remediation**: Delete superfluous nodes, correct facts, or resolve contradictory perspectives. If edits alter outlines, links, or scales, loop back to Stage 2; otherwise, loop back to Stage 3.
   
4. **Stage 4: Abstraction, Local Scale & Data Validity (Drafting & Formatting)**
   - **Inputs (Entangled)**: Semantic Fidelity, Depth Conformance, Information Encoding (Information Fidelity, Token Precision, Token Brevity, Reader Accessibility), Data Validity
   - **Pass Criteria**: Local text representations, terminal detail densities, packaging density, and context-sensitive range limits conform to specifications and are calibrated to the lowest macro depth constraint.
   - **Remediation**: Adjust details, range limits, or formatting. If changes alter ground-level facts, relevance, or alignment, loop back to Stage 3; otherwise, loop back to Stage 4.
   
5. **Stage 5: Micro Polish (Copy-Editing)**
   - **Inputs**: Notation Conformance
   - **Pass Criteria**: Physical markdown layout, spacing, spelling, and character-level syntax comply with conventions.
   - **Remediation**: Fix cosmetic layout nits. Loop back to Stage 5.

---

## 2. Stage Breakdown & Execution Rules

Each stage of the cycle represents a dedicated run of the [**Audit Plan**](/meta/procedures/audit/audit.plan.md). Within each stage, dimensions are executed in a strict sequential micro-sequence dictated by the step numbers (e.g., Step X.1 must pass before Step X.2 begins). When a downstream step is remediated, it must loop back to check potential regression in earlier steps or stages as detailed in its remediation rules.

### Stage 1: Content Scope & Identity (Graph Boundaries)
* **Step 1.1: Inclusion & Exclusion** (Concurrent or Sequential)
  - *Universal Actions*:
    - **Inclusion**: Verify that every single valid element belonging inside the defined scope is successfully identified and captured.
    - **Exclusion**: Verify that out-of-scope elements are blocked and prevented from polluting the target asset.
  - *Execution Rationale*: Inclusion and Exclusion can be evaluated concurrently or in any sequential order, as they establish distinct, independent aspects of boundary cleanliness (recall and containment, respectively).
  - *Remediation*: If boundaries are incorrect, adjust boundary inputs/mappings. **Loops back to Step 1.1**.
* **Step 1.2: Semantic Uniqueness** (Independent)
  - *Universal Actions*:
    - **Semantic Uniqueness**: Verify that the target asset is free from unnecessary repetition and overlapping information.
  - *Remediation*: If duplicate elements exist, merge or delete them. **Loops back to Step 1.2** (or back to Step 1.1 if resolution alters boundary scope).

### Stage 2: Macro Graph Architecture (Skeletal & Scale Setup)
* **Step 2.1: Macro Graph Architecture** (Entangled: Macro Structure, Macro Depth, Macro Topology, Depth Continuity)
  - *Universal Actions*:
    - **Macro Structure**: Verify that the folder layout, file names, heading hierarchy, and outline skeleton conform to templates. While macro-structure is hierarchical and layered (Folders -> Files -> Sections -> Blocks), micro-formatting operates as the terminal copy-editing check.
    - **Macro Depth**: Verify that the global vertical hierarchy of zoom levels and nested abstraction scales (Document -> Section -> Subsection -> Paragraph) is correctly calibrated to the target objective.
    - **Macro Topology**: Verify that all macro-level linkages, cross-file references, and parent-child dependencies resolve cleanly and form a valid, non-cyclic graph.
    - **Depth Continuity**: Verify that transitions across the vertical abstraction range are step-wise and free of abrupt gaps or skipped operational steps.
  - *Execution Rationale*: Evaluating file relationships (Macro Topology) and transitional steps (Depth Continuity) requires concurrently setting the outline skeleton (Macro Structure) and the global zoom scale constraints (Macro Depth). Because these dimensions define the global container framework, they are deeply co-dependent and must be evaluated together.
  - *Remediation*: Reconnect reference paths, adjust parent-child hierarchies, rewrite heading outlines, or add transitional files/sections. **Loops back to Step 2.1** (or Stage 1, Step 1.1 if changes modify the scope boundary).

### Stage 3: Substance, Truth & Internal Alignment (Substance Auditing)
* **Step 3.1: Semantic Relevance** (Independent)
  - *Universal Actions*:
    - **Semantic Relevance**: Verify that all included content is strictly necessary and useful for achieving the immediate objective function, identifying and flagging superfluous or off-target information.
  - *Remediation*: If content is superfluous or off-target, delete or modify it. **Loops back to Stage 2, Step 2.1** (if deleting content affects topology, depth continuity, or macro depth), or proceeds.
* **Step 3.2: Semantic Veracity** (Independent)
  - *Universal Actions*:
    - **Semantic Veracity**: Verify that all ground-level factual claims and quantitative values within the target asset are correct and align directly when cross-referenced with an objective source of truth.
  - *Remediation*: If a factual claim or quantitative value is incorrect, correct the facts. **Loops back to Step 3.1** (Semantic Relevance), or **Stage 2, Step 2.1** (if correcting facts affects topology, depth continuity, or macro structure).
* **Step 3.3: Internal Alignment** (Independent)
  - *Universal Actions*:
    - **Internal Alignment**: Verify that different components or layers of detail within the target asset assert consistent realities and do not contradict one another.
  - *Remediation*: Resolve the contradiction by rewriting one of the clashing sections. **Loops back to Step 3.2** (Semantic Veracity) and **Stage 2, Step 2.1** (Depth Continuity/Macro Topology) to verify the substance and structural flow of the rewrite.

### Stage 4: Abstraction, Local Scale & Data Validity (Drafting & Formatting)
* **Step 4.1: Abstraction, Local Scale & Data Validity** (Entangled: Semantic Fidelity, Depth Conformance, Information Encoding, Data Validity)
  - *Universal Actions*:
    - **Semantic Fidelity**: Verify that the underlying conceptual representation and model within the target asset faithfully preserve the true logical relationships and intent of what they represent in reality.
    - **Depth Conformance**: Verify that local sentences, fields, and values strictly adhere to the terminal zoom constraint inherited from the lowest active layer of the macro depth cascade, preventing local scale leakage.
    - **Information Encoding**: Verify that the presentation profile balances Information Fidelity (Token Precision and Token Brevity) against reader ingestion friction (Reader Accessibility).
    - **Data Validity**: Verify that all individual data units, parameters, or values within the target asset conform to designated types, range limits, domain constraints, or logical boundaries. In natural language and technical documentation, data validity is context-sensitive and exists on a spectrum (e.g., active vs. deprecated terminology, or levels of schema compliance).
  - *Execution Rationale*: The choice of local terminal zoom level (Depth Conformance) and packaging format (Encoding) directly dictates the context-sensitive data validity constraints (Data Validity) of the data, which in turn shapes the conceptual model representation (Semantic Fidelity). Because human-readable and semi-structured assets rely on spectrum-based validity and layered depth inheritance, they represent a co-dependent design trade-off and must be evaluated concurrently.
  - *Remediation*: Adjust details, model relationships, data boundaries, or formatting. **Loops back to Stage 3, Step 3.3** (Internal Alignment), **Step 3.2** (Semantic Veracity), and **Stage 2, Step 2.1** (Depth Continuity/Macro Topology) to ensure modified content remains true, aligned, and structurally coherent.

### Stage 5: Micro Polish (Copy-Editing)
* **Step 5.1: Notation Conformance** (Independent)
  - *Universal Actions*:
    - **Notation Conformance**: Verify that the physical notation, layout, spacing, cosmetic syntax rules, spelling, and formatting comply with markdown conventions. As a terminal leaf-node validator, notation conformance copy-edits character-level syntax and nits without altering the macro-structure hierarchy.
  - *Remediation*: Fix formatting nits. **Loops back to Step 5.1** (cosmetic sink; does not affect semantics).

---

## 3. Dimension-Level Cycle Graph

When an issue is identified in a specific dimension, the act of **remediating** that issue modifies the target asset. This modification triggers downstream dependency cycles, requiring the auditor to loop back and re-evaluate other dimensions.

The feedback loops and cycles between the 18 active dimensions are defined as follows:

* **Inclusion & Exclusion**: Remediation adds or deletes items, which triggers re-evaluation of **Semantic Fidelity**, **Data Validity**, and **Macro Topology**.
* **Semantic Fidelity**: Rewriting the conceptual model triggers re-evaluation of **Semantic Relevance**, **Semantic Uniqueness**, **Semantic Veracity**, and **Depth Conformance**.
* **Semantic Relevance**: Deleting irrelevant content triggers re-evaluation of **Macro Topology** and **Inclusion**.
* **Semantic Uniqueness**: Merging duplicate entries triggers re-evaluation of **Macro Topology**.
* **Semantic Veracity**: Editing facts to match reality triggers re-evaluation of **Notation Conformance**, **Internal Alignment**, and **Depth Conformance**.
* **Macro Structure**: Modifying skeletal structure triggers re-evaluation of **Macro Depth**, **Depth Continuity**, and **Notation Conformance**.
* **Macro Depth**: Changing the global zoom level triggers re-evaluation of **Macro Structure**, **Depth Continuity**, and **Semantic Veracity**.
* **Depth Conformance**: Adjusting localized detail density triggers re-evaluation of **Semantic Fidelity**, **Data Validity**, and **Semantic Veracity**.
* **Information Encoding**: Modifying overall presentation packaging triggers re-evaluation of **Information Fidelity** and **Reader Accessibility**.
* **Information Fidelity**: Adjusting the density/quality trade-off triggers re-evaluation of **Token Precision** and **Token Brevity**.
* **Token Precision**: Adding technical detail to achieve exactness triggers re-evaluation of **Token Brevity** and **Semantic Veracity**.
* **Token Brevity**: Condensing text to minimize fluff triggers re-evaluation of **Token Precision** and **Depth Continuity**.
* **Reader Accessibility**: Rephrasing or restructuring layout for readability triggers re-evaluation of **Notation Conformance**.
* **Depth Continuity**: Adding transitional text triggers re-evaluation of **Semantic Veracity** and **Notation Conformance**.
* **Data Validity**: Changing classification tags triggers re-evaluation of **Macro Topology**.
* **Macro Topology**: Reconnecting references or paths triggers re-evaluation of **Internal Alignment** and **Semantic Veracity**.
* **Internal Alignment**: Resolving contradictions triggers re-evaluation of **Semantic Veracity** and **Semantic Fidelity**.
* **Notation Conformance**: Formatting corrections require no downstream checks (cosmetic sink).
