# Audit Meta-Specification: Base Specification Auditability (base_spec_auditability.meta.md)

This specification defines the rules and guidelines for designing base specifications (declarative blueprints for documents, databases, or processes) to ensure they are fully and objectively auditable. It outlines how a base specification must frame and define context for audit dimensions, and establishes mitigation rules against the risk of incomplete or low-quality audits.

A standard copy-pasteable blueprint is provided in the [**Base Specification Template**](base_spec_template.meta.md).

---

## 1. The Core Principle: Auditability by Design

A base specification cannot merely define a file format or template. To support objective evaluation, it must act as the primary source of truth for the constraints, boundaries, and invariants that audit dimensions will verify.

> [!IMPORTANT]
> **Ground Truth Rule**:
> Every audit constraint defined in a companion audit specification must correspond to a declarative rule, boundary, or invariant explicitly defined in the base specification. Audit specifications must not introduce ad-hoc constraints that lack a baseline in the base specification.

---

## 2. Framing Context for Audit Dimensions

To ensure that audit dimensions have clear criteria for evaluation, a base specification must explicitly frame what each relevant audit pillar means within its domain:

* **Domain Delineation (Scope)**:
  - The base specification must define the exact boundary lines (the perimeter) of the evaluation universe. It must state what is explicitly in-scope, what is out-of-scope, and what inputs are ignored.
  - *Audit Translation*: Provides the ground truth for auditing the [**Inclusion**](audit-dimension/dimension-atomic/inclusion_accuracy.dimension.md) and [**Exclusion**](audit-dimension/dimension-atomic/exclusion_accuracy.dimension.md) dimensions.
* **Structural Architecture (Blueprint)**:
  - The base specification must provide a deterministic template (for documents) or schema (for data payloads) with precise syntax and formatting rules. It must specify section sequences, naming conventions, and relationship linkages.
  - *Audit Translation*: Provides the ground truth for auditing the [**Macro Structure**](audit-dimension/dimension-atomic/macro_structure.dimension.md), [**Macro Topology**](audit-dimension/dimension-atomic/macro_topology.dimension.md), and [**Notation Conformance**](audit-dimension/dimension-atomic/notation_conformance.dimension.md) dimensions.
* **Semantic Substance (Content)**:
  - The base specification must define the semantic criteria for valid content. It must state what constitutes a "falsifiable description," "objective justification," or "remediable item" rather than allowing generic placeholders.
  - *Audit Translation*: Provides the ground truth for auditing the [**Data Validity**](audit-dimension/dimension-atomic/data_validity.dimension.md), [**Semantic Relevance**](audit-dimension/dimension-atomic/semantic_relevance.dimension.md), [**Semantic Fidelity**](audit-dimension/dimension-atomic/semantic_fidelity.dimension.md), [**Semantic Veracity**](audit-dimension/dimension-atomic/semantic_veracity.dimension.md), and [**Internal Alignment**](audit-dimension/dimension-atomic/internal_alignment.dimension.md) dimensions.
* **Resolution & Projection**:
  - The base specification must define the analytical zoom level (abstraction layer) and the readability target (audience fit, token precision vs. token brevity) of the asset.
  - *Audit Translation*: Provides the ground truth for auditing the [**Macro Depth**](audit-dimension/dimension-atomic/macro_depth.dimension.md), [**Depth Conformance**](audit-dimension/dimension-atomic/depth_conformance.dimension.md), [**Depth Continuity**](audit-dimension/dimension-atomic/depth_continuity.dimension.md), [**Information Encoding**](audit-dimension/dimension-composite/information_encoding.dimension.md), [**Information Fidelity**](audit-dimension/dimension-composite/information_fidelity.dimension.md), [**Token Precision**](audit-dimension/dimension-atomic/token_precision.dimension.md), [**Token Brevity**](audit-dimension/dimension-atomic/token_brevity.dimension.md), and [**Reader Accessibility**](audit-dimension/dimension-atomic/reader_accessibility.dimension.md) dimensions.

---

## 3. Mitigating the Risk of Incomplete Audits

Focusing only on structural compliance or high-level context risks producing incomplete audits where files pass syntax checks but contain shallow, missing, or unverifiable information (the **Specification-Audit Gap**). To prevent this, base specifications must enforce the following rules:

### A. Semantic Validation Rules
The base specification must define explicit rules that prevent non-functional or empty placeholders.
* **Rule**: For every text section or field, the base specification must define what qualifies as a complete and valid entry (e.g., requiring concrete file paths, specific architectural principles, or operational impact details).
* **Impact**: Without these semantic validation rules, the **Data Validity** and **Semantic Relevance** dimensions cannot objectively detect incomplete or superficial content.

### B. Complete Coverage of the Four Pillars
When designing a base specification, the author must verify that the spec defines rules addressing all four architectural pillars:
1. **Scope**: Is the boundary of the evaluated universe clearly defined?
2. **Structure**: Is the template or schema rigid, preventing arbitrary layouts?
3. **Substance**: Are the content requirements qualitative, objective, and falsifiable?
4. **Projection**: Are the abstraction layers and readability constraints defined?

### C. Falsifiable Criteria
Every requirement in the base specification must be written in a falsifiable manner. If a requirement is subjective or cannot be verified as true or false, it cannot be audited objectively, resulting in a failed or incomplete audit.

### D. The Colocation Rule (Eliminating Indirection)
To prevent mental dislocation and maintain readability, rules must not be split into separate top-level sections (e.g., separating layout templates from their semantic validation rules). 
* **Rule**: All format, semantic, resolution, and auditability rules governing a specific component or section must be defined together in a single colocated component specification block.

---

## 4. Inversion of Control & Auditor Discretion (Interpretive Fallbacks)

For target mediums or formats where certain dimensions (such as **Macro Topology** or **Depth Continuity**) cannot be governed by rigid, deterministic rules (e.g., free-form essays or unstructured text), the base specification must implement an **Inversion of Control (IoC)** fallback.

### A. Intent-Based Framing
Instead of prescribing a rigid template or schema for that dimension, the base specification declares the **Evaluative Intent** of the dimension within that specific context.
* **Example**: For a free-form essay, the base specification might define Macro Topology's intent as: *"Audits the logical layout and dependency tree of the core arguments. There must be no circular reasoning or disconnected narrative threads."*

### B. Delegation of Mapping
The base specification explicitly delegates the responsibility of mapping physical content structures to the auditor's professional discretion:
* The auditor dynamically defines the semantic nodes (e.g., arguments, assertions, paragraphs) and edges (e.g., transitions, logical dependencies) during traversal.
* The auditor evaluates compliance against the declared intent of the dimension.

### C. The Justification Rule
To prevent auditor discretion from introducing subjective, non-falsifiable audit issues, the auditor must satisfy the **Justification Rule** for all discretionary findings:
* Every compiled audit issue generated under an interpretive fallback must explicitly document the auditor's semantic mapping and outline the logical path connecting the target content to the observed violation.
