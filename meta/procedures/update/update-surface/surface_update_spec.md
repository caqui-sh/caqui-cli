# Update Surface-Area Specification & Blueprint (surface_update_spec.md)

This document establishes the high-level, black-box, and rigorous blueprint for creating concrete update surface-area specifications (`meta/history/<branch_name>_<version>/<feature_name>_surface.md`).

An update surface-area specification is the **boundary definition** (part two of the three-part specification sequence). It defines the entry points, inbound/outbound contracts, payload structures, and error representations introduced or modified by the change.

---

## 1. Core Principles of Surface-Area Specifications

To ensure exact interface compliance, every concrete surface-area specification must adhere to the following principles:

* **Boundary Decoupling**:
  - The specification must focus exclusively on the interaction contracts at the system's external boundaries.
  - All references to internal codebase structure or implementation details are strictly prohibited.
* **Delta-Focused Contracts**:
  - Document only the added, modified, or deleted boundary surfaces and interface contracts. Unchanged contracts must be omitted.
  - For modified boundary interfaces, the specification must provide a clear transition mapping detailing how the legacy interface contract translates to the new boundary interface.
* **Structural Precision**:
  - Payload structures and interfaces must be defined with exact abstract types, preconditions, and postconditions.
* **Minimalist Guardrails**:
  - Design direct interfaces mapping actions to effects, avoiding indirect orchestration, implicit propagation, or speculative abstractions.
  - Trust the caller to coordinate interactions by prioritizing direct control over state and effects.
* **Codebase Pattern Alignment**:
  - Align boundary surface-areas and interaction models with established codebase conventions, reusing existing patterns unless they are insufficient.

---

## 2. Concrete Update Surface-Area Document Template

Below is the standard, markdown-formatted template that must be used for every concrete update surface-area specification.

---

```markdown
# Target Update Surface Area: [Update Name]

* **Status**: [Draft / Approved / Completed]
* **Target Version / Release**: [X.Y.Z]
* **Abstract Companion**: [Link to <update_name>_abstract.md]
* **Use-Case Companion**: [Link to <update_name>_matrix.json]
* **Tests Companion**: [Link to <update_name>_tests.json]
* **Procedural Companion**: [Link to <update_name>_plan.md]

---

## 1. Boundary Topography

Delineate the modified, added, or deleted entry and exit points at the system boundary.

### 1.1 Inbound Vectors
*   **Entry Points**: [Delineate new or modified inputs.]

### 1.2 Outbound Vectors
*   **Effects & Integrations**: [Delineate new or modified outputs and side-effects.]

---

## 2. Interface Contracts

Define the detailed input/output constraints and boundary surface-areas for each modified or introduced boundary interface.

### [Interface Name]
*   **Inputs & Preconditions**: [Specify the input structures, constraints, preconditions, and references to convention-aligning codebase patterns.]
*   **Outputs & Postconditions**: [Specify nominal and exceptional output structures, side-effects, and diagnostic metadata, omitting internal implementation details.]
*   **Transition & Structural Mapping**: [For modified interfaces, provide a clear mapping showing how the legacy interface contract translates into the modified boundary surface-area.]
```
