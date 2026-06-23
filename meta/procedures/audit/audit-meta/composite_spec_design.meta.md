# Audit Meta-Specification: Composite Dimension Specification Design (composite_spec_design.meta.md)

This specification defines the rules, structural constraints, and semantic guidelines for creating and modifying composite and entangled audit dimension specifications. It ensures all composite dimensions are structurally uniform, balance composed forces cleanly, and document trade-off equilibriums without ambiguity.

---

## A. Output Document Blueprint

All composite dimension specifications must be written in Markdown and conform exactly to the following skeleton:

```markdown
# Audit Dimension Specification *(Composite & Entangled / Layered)*: [Dimension Name] ([filename].dimension.md)

This specification defines the rules for the **[Dimension Name]** dimension. It audits [setup_description], balancing [Force A] against [Force B], answering: *[conceptual_equilibrium_question]?*

### Composed Dimensions
* [[Composed Dimension 1]](../dimension-atomic/[dimension1].dimension.md)
* [[Composed Dimension 2]](../dimension-composite/[dimension2].dimension.md)

---

## Composite Composition & Entanglement

[Composition_description_detailing_the_competing_forces_and_the_optimal_equilibrium_envelope]

* **[Dimension Name] ([Short Operational Description])**:
  - **Constraint**: [declarative_equilibrium_constraint]
  - **Audit Focus**: [trade-off_evaluation_guidelines]
  - **Mutual Exclusive Distinction**: [boundary_distinctions]
```

---

## B. Document Specifications & Structural Constraints

Each element in the composite dimension specification must conform to the following formatting and constraint rules:

| Element / Section | Markdown Syntax | Required | Format / Constraint | Description |
| :--- | :--- | :---: | :--- | :--- |
| **Title Header** | `# Audit Dimension Specification *(Composite & Entangled / Layered)*: [Dimension Name] ([filename].dimension.md)` | Yes | H1 header | Standard header naming the specification and the exact filename of the document. |
| **Intro Paragraph** | `This specification defines the rules for the **[Dimension Name]** dimension. It audits... balancing [A] against [B], answering: *[Question]?*` | Yes | Two sentences, H3 separator | Defines the target composite evaluation, the competing forces, and the key equilibrium question. |
| **Composed Dimensions** | `### Composed Dimensions` followed by a list of markdown links | Yes | H3 header and bulleted list | Clickable relative links to all atomic or composite dimensions that are packaged under this composite spec. |
| **Section Divider** | `---` | Yes | Three dashes | Horizontal rule dividing metadata from composition rules. |
| **Composition Header** | `## Composite Composition & Entanglement` | Yes | H2 header | Standard section header. |
| **Composition Desc** | `[detailed composition paragraph]` | Yes | Normal text | Defines the active trade-off curve (e.g., Fidelity vs. Economy) and how the composite balances them. |
| **Dimension Name Bullet** | `* **[Dimension Name] ([Short Operational Description])**:` | Yes | Bold bullet point | The title bullet point for the dimension's constraints. |
| **Constraint** | `  - **Constraint**: [rules]` | Yes | Bold label, indented bullet | Specifies the optimal equilibrium standard the target asset must satisfy. |
| **Audit Focus** | `  - **Audit Focus**: [instructions]` | Yes | Bold label, indented bullet | Operational guidelines to verify the trade-off is balanced, mapping deficits on both sides of the curve. |
| **Mutual Exclusive Distinction** | `  - **Mutual Exclusive Distinction**: [distinction]` | Yes | Bold label, indented bullet | Defines what remains constant, and how this composite isolates its focus from external conceptual layers. |

---

## C. Specification Integrity Invariants

### 1. The Equilibrium Rule (Fidelity vs. Economy)
Composite dimensions are designed to evaluate the trade-off curve between two or more competing atomic dimensions. The specification must explicitly define the **optimal equilibrium** rather than introducing new independent rules.
* **No New Atomic Rules**: A composite spec must not introduce ground-level atomic constraints that are not captured by its composed dimensions.
* **Symmetrical Focus**: The `Audit Focus` must be written to detect imbalances on both sides of the trade-off curve, defining:
  - **Fidelity Deficits**: Where information is omitted or over-condensed to minimize volume (compromising completeness for brevity).
  - **Economy Deficits**: Where information is dumped without structure or compression (compromising accessibility for specificity).

### 2. Separation of Scale (Composed Links)
The `Composed Dimensions` list must link only to the immediate child dimensions that form the composite.
* **Path Cleanliness**: Links must use relative markdown paths.
* **No Hierarchy Skips**: Do not list sub-components of child composite dimensions; let each composite document its own direct compositions.
