# [Name of Target Asset] Specification & Blueprint ([filename]_spec.md)

[Provide a high-level summary of what document, payload, or process this specification defines, and what consumer or system it serves.]

---

## 1. Core Principles

[Define the high-level intent, core goals, and philosophies governing this asset (e.g., Awareness over perfection, zero micro-management, positive realism).]

* **[Principle 1]**: [Definition/Rule]
* **[Principle 2]**: [Definition/Rule]

---

## 2. Global Scope Boundaries (Domain Delineation)

[Explicitly outline the boundaries of the universe defined by this specification. This provides the global ground truth for Scope, Inclusion, and Exclusion audits.]

* **Explicitly In-Scope**:
  - [Define item/domain in-scope]
* **Explicitly Out-of-Scope**:
  - [Define item/domain out-of-scope]
* **Ignored Inputs / Non-Blockers**:
  - [Define items that are ignored or do not block verification]

---

## 3. Global Storage & Naming

* **Storage Location**: `[path/to/folder/or/pattern]`
* **Naming & Versioning**: `[naming_convention_pattern]`

---

## 4. Component Specifications

[Rather than separating layout, logic, and auditing, specify each structural component (e.g., markdown section, JSON key block) in a single, colocated block to prevent indirection.]

### Component A: [e.g., Section Name / JSON Key]

* **A.1 Format & Layout (Structure)**:
  - [Define markdown layout template, headers, syntax, or JSON schema keys]
* **A.2 Logical Meaning & Rules (Substance)**:
  - [Specify factual/logical constraints; e.g. "every entry must represent a real architectural trade-off", "descriptions must be falsifiable"]
* **A.3 Resolution & Projection**:
  - [Specify the abstraction level and readability/density rules; e.g., "must be written at a design abstraction layer", "must balance technical detail with brevity"]
* **A.4 Section Boundaries (Scope)**:
  - [Define any component-specific scope boundaries; e.g. "only items active in this iteration are in-scope"]
* **A.5 Audit Dimensions & Intent**:
  - **Active Dimensions**: [e.g., Notation Conformance, Data Validity, Perspective Depth, Scope]
  - **Interpretive Fallbacks (if any)**:
    - *Dimension*: [e.g., Information Encoding]
    - *Evaluative Intent*: [Declare the intent the auditor must verify for this component]
    - *Auditor Mapping*: [Define what elements the auditor has discretion to map]

### Component B: [e.g., Section Name / JSON Key]
...
