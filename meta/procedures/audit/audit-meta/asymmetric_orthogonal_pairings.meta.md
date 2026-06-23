# Technical Audit Philosophy: Asymmetric Orthogonal Pairings in Information Dimensions

This document defines the philosophical frameworks and asymmetric orthogonal pairings used to conceptualize, define, and audit information dimensions across the specification architecture.

---

## 1. Core Philosophy of Coordinate Mapping

In qualitative specification systems, single-dimensional definitions lead to auditor anchoring and shallow, checklist-based reviews. To achieve complete cognitive capture, we define dimensions by intersecting contrasting, non-symmetrical coordinate axes. 

Every information dimension is conceptualized by mapping its active forces along four key orthogonal pairings.

---

## 2. The Four Asymmetric Orthogonal Pairings

### Axis A: Signal (Content) vs. Medium (Encoding)
* **The Pairing**: The pure semantic meaning being conveyed vs. the physical structure/format used to package it.
* **Orthogonal Nature**: You can have a perfectly accurate semantic concept that is completely unreadable due to formatting noise (poor notation/accessibility). Conversely, you can have a beautifully formatted markdown table that contains logically inconsistent or factually false data.
* **Audit Application**: Prevents the auditor from confusing formatting polish with factual truth (e.g., separating Notation Conformance from Semantic Veracity).
* **Metric Example**: `(minimizing representation overhead / maximizing semantic transfer)`

### Axis B: Local (Micro/Node) vs. Global (Macro/Graph)
* **The Pairing**: The properties of an individual line, value, or block vs. the structural topology and skeleton of the entire asset.
* **Orthogonal Nature**: A document can have zero local errors (every sentence is grammatically correct and every data type is valid), yet be a global failure due to cyclic references, missing outline steps, or disjointed flow. Conversely, a globally perfect skeleton can be filled with invalid local data elements.
* **Audit Application**: Ensures validation is run at both the leaf level (e.g., Data Validity, Notation) and the graph level (e.g., Macro Topology, Macro Structure).
* **Metric Example**: `(minimizing local drift / maximizing topological integrity)`

### Axis C: Static (Boundaries/Invariants) vs. Dynamic (Flow/Transitions)
* **The Pairing**: The boundaries and rules governing the information at rest vs. the rules governing how the reader (or system) transitions between concepts.
* **Orthogonal Nature**: Static rules define the "fences" (e.g., Scope boundaries, Schema constraints). Dynamic rules define the "gradients" (e.g., Abstraction gradients, logical transitions, parent-child flows). An asset can have perfect static boundary enforcement but be a choppy, jumpy, and disjointed reading experience.
* **Audit Application**: Separates the auditing of boundary correctness (Inclusion/Exclusion) from flow correctness (Continuity).
* **Metric Example**: `(minimizing transition friction / maximizing boundary containment)`

### Axis D: Objective Alignment (Truth) vs. Subjective Calibration (Ingestion)
* **The Pairing**: Factual correctness relative to external reality vs. readability calibrated to the reader's cognitive capacity.
* **Orthogonal Nature**: A highly detailed scientific proof is 100% objectively aligned (Truth), but exhibits low subjective calibration for a lay audience (Ingestion friction). Conversely, a highly readable, simplified summary is easy to ingest but may be a coarse, low-fidelity approximation of reality.
* **Audit Application**: Balance information density against cognitive load (e.g., balancing Expression Precision/Brevity against Reader Accessibility).
* **Metric Example**: `(minimizing ingestion barrier / maximizing factual fidelity)`

---

## 3. The Dimension Coordinate Box

By intersecting these four orthogonal pairings, we can locate any information dimension at a specific coordinate within a four-dimensional conceptual space:

| Dimension | Signal / Medium | Local / Global | Static / Dynamic | Objective / Subjective |
| :--- | :--- | :--- | :--- | :--- |
| **Notation Conformance** | Medium | Local | Static | Objective |
| **Data Validity** | Medium | Local | Static | Hybrid (Context-Sensitive) |
| **Macro Structure** | Medium | Global | Static | Objective |
| **Macro Topology** | Medium | Global | Static | Objective |
| **Depth Conformance** | Medium | Local | Static | Subjective |
| **Depth Continuity** | Medium | Global | Dynamic | Subjective |
| **Perspective Depth** | Medium | Global | Static | Subjective |
| **Semantic Veracity** | Signal | Local | Static | Objective |
| **Semantic Consistency** | Signal | Local | Static | Objective |
| **Semantic Relevance** | Signal | Local | Static | Subjective |
| **Semantic Fidelity** | Signal | Global | Static | Subjective |
| **Semantic Diversity** | Signal | Global | Static | Subjective |
| **Inclusion Accuracy** | Signal | Global | Static | Objective |
| **Exclusion Accuracy** | Signal | Global | Static | Objective |
