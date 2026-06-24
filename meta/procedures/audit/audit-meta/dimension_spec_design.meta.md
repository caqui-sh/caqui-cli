# Audit Meta-Specification: Dimension Specification Design (dimension_spec_design.meta.md)

This specification defines the rules, structural constraints, and semantic guidelines for creating and modifying technical audit dimension specifications. It ensures all audit dimensions are structurally uniform, operationally clear, mathematically rigorous, and free from cognitive bias traps.

---

## A. Output Document Blueprint

All audit dimension specifications must be written in Markdown and conform exactly to the following skeleton:

```markdown
# Audit Dimension Specification *(Atomic & Terminal)*: [Dimension Name] - [Pillar Name] ([filename].dimension.md)

This specification defines the rules for the **[Dimension Name]** dimension. It audits [conceptual_setup_description], answering: *[conceptual_outcome_question] (minimizing [asymmetric_failure_mode] / maximizing [asymmetric_target_metric])?*

This dimension exists under the [**[Pillar Name]**](audit-pillar/[pillar_filename].pillar.md) pillar.

This dimension is [**[Nature Name]**](audit-nature/[nature_filename].nature.md) in nature.

---

## Dimension Constraints

* **[Dimension Name] ([Short Operational Description])**:
  - **Constraint**: [declarative_constraint_rule]
  - **Audit Focus**: [qualitative_evaluation_guidelines]
  - **Mutual Exclusive Distinction**: [boundary_distinctions]
```

---

## B. Document Specifications & Structural Constraints

Each element in the dimension specification must conform to the following formatting and constraint rules:

| Element / Section | Markdown Syntax | Required | Format / Constraint | Description |
| :--- | :--- | :---: | :--- | :--- |
| **Title Header** | `# Audit Dimension Specification *(Atomic & Terminal)*: [Dimension Name] - [Pillar Name] ([filename].dimension.md)` | Yes | H1 header | Standard header naming the specification, the associated pillar, and the exact filename of the document. |
| **Intro Paragraph** | `This specification defines the rules for the **[Dimension Name]** dimension. It audits [setup_desc], answering: *[question] ([parenthetical])?*` | Yes | Two sentences, H2 separator | Defines the target evaluation, key conceptual question, and standardized metrics. |
| **Pillar Link** | `This dimension exists under the [**[Pillar Name]**](audit-pillar/[pillar_filename].pillar.md) pillar.` | Yes | Relative Markdown link | Points directly to the parent pillar specification document in the `audit-pillar/` folder. |
| **Nature Link** | `This dimension is [**[Nature Name]**](audit-nature/[nature_filename].nature.md) in nature.` | Yes | Relative Markdown link | Points directly to the associated technical nature specification document in the `audit-nature/` folder. |
| **Section Divider** | `---` | Yes | Three dashes | Horizontal rule dividing document metadata from constraints. |
| **Constraints Header** | `## Dimension Constraints` | Yes | H2 header | Standard section header. |
| **Dimension Name Bullet** | `* **[Dimension Name] ([Short Operational Description])**:` | Yes | Bold bullet point | The title bullet point for the dimension's constraints. |
| **Constraint Definition** | `  - **Constraint**: [rules]` | Yes | Bold label, indented bullet | The positive, declarative standard the target asset must satisfy. |
| **Audit Focus** | `  - **Audit Focus**: [instructions]` | Yes | Bold label, indented bullet | Operational guidelines for the auditor (must follow the anti-anchoring rule). |
| **Mutual Exclusive Distinction** | `  - **Mutual Exclusive Distinction**: [distinction]` | Yes | Bold label, indented bullet | Defines the boundary, distinguishing the dimension from close peers/siblings. |

---

## C. Specification Integrity Invariants

### 1. Semantic Progression & Asymmetry (The Intro Paragraph)
The introduction paragraph must follow a strict three-tier semantic progression:
* **Setup Sentence (Semantic Diversity)**: Introduce the dimension by naming it and describing the parameters or attributes it audits using rich, diverse prose. Avoid repeating the exact words of the parenthetical here.
* **Conceptual Question (Semantic Diversity)**: Ask a descriptive question focusing on the *experience*, *symptom*, or *operational outcome* of the dimension (e.g., avoiding vague generalizations, or preventing logical leaps).
* **Standardized Parenthetical (Semantic Alignment)**: Conclude the question with an asymmetric, standardized metric pair in the format: `(minimizing [failure mode] / maximizing [target metric])`.
* **The Asymmetric Parenthetical Rule**: The parenthetical metrics must **never** be symmetric mirror images of each other (e.g., `(minimizing detail loss / maximizing detail preservation)` is invalid because they are simple scalar negations). The failure mode must describe a distinct negative state of information packaging (e.g., *representation approximation*, *perspective drift*), and the target metric must describe a distinct positive operational objective (e.g., *detail specificity*, *resolution alignment*).

### 2. The Anti-Anchoring Rule (Audit Focus)
The `Audit Focus` must act as a continuous qualitative evaluation target rather than a checklist.
* **No Finite Lists**: The `Audit Focus` must not list specific examples, checkable symptoms, file paths, or text sections. 
* **Continuous Phrasing**: Use continuous qualitative conditions (e.g., *"identifying coarse approximations or non-specific generalities"* or *"identifying abrupt leaps in reasoning or perspective resolution"*). This prevents **auditor anchoring** and **design fixation** where the auditor treats the specification as a shallow checklist.

### 3. Closed-Loop ME Distinctions (Mutual Exclusion & Subspace Partitions)
The `Mutual Exclusive Distinction` must draw clear boundaries between the target dimension and its close peers (dimensions within the same subspace/pillar) to prevent operational confusion.
* **Relevance-Only Rule**: Only reference dimensions that share the same subspace or pose a real risk of confusion. Do not list completely unrelated dimensions (e.g., do not list `Notation Conformance` in `Depth Continuity`, as they belong to different subspaces and share no common support).
* **Subspace Partitions (Binary, Triad, or Multivalent)**: If a subspace (pillar) is partitioned by multiple orthogonal dimensions (e.g., the binary `Inclusion`/`Exclusion` pair in Scope, or the triad `Perspective Depth`/`Depth Conformance`/`Depth Continuity` in Resolution), all dimensions in that partition must reference each other in a closed loop (a pair, triangle, or $N$-ary chain), explicitly mapping how they divide their shared operational space.

### 4. Asymmetric Coordinate Mapping (Meta-Semantic Diversity)
To prevent auditor anchoring, design fixation, or hand-waving subjectivity, dimension specifications are structured using **Asymmetric Coordinate Mapping**. This is an application of **Semantic Diversity** at the meta-specification level: rather than defining a dimension via a single linear description, the specification maps the dimension's boundaries by intersecting contrasting, non-symmetrical coordinate axes:

#### Axis A: The Intent Coordinate (Directional Asymmetry)
* **Mathematical/Conceptual Counterpart**: **Minimize vs. Maximize**
* **Operational Metaphor**: **Noise vs. Signal**
  - **Signal (Maximize)**: The constructive semantic intent, clear information transmission, and positive utility of the dimension.
  - **Noise (Minimize)**: The structural, cognitive, or semantic friction, clutter, and unwanted variance that obscure the signal.
* **Writing Rule**: The parenthetical metric pairing in the introduction must reflect this asymmetry: `(minimizing [Noise / Failure Mode] / maximizing [Signal / Target Objective])`. The failure mode must describe a distinct negative symptom or failure state (e.g., *perspective drift*, *representation approximation*), and the target objective must describe a distinct positive capability (e.g., *resolution alignment*, *detail specificity*). They must never be symmetric mirror images of each other (e.g., `minimizing detail loss / maximizing detail preservation` is invalid).

#### Axis B: The Scale Coordinate (Evaluation Dualism)
* **Mathematical/Conceptual Counterpart**: **Discrete vs. Spectrum**
* **Operational Metaphor**: **Floor vs. Ceiling**
  - **Floor (Discrete)**: The baseline, checkable invariants, discrete boundary conditions, or safety thresholds (errors of commission/omission). It defines the entry-level sanity check or pass/fail line.
  - **Ceiling (Spectrum)**: The continuous optimization gradient, asymptotic density, or qualitative depth of the document. It defines the aspiration for excellence that can be progressively approached.
* **Writing Rule**: Constraints and audit focus guidelines are encouraged to frame the dimension from both a floor perspective (pinpointable, countable errors) and a ceiling perspective (continuous flow, density, or quality scales). This gives the auditor both clear actionable infractions and holistic evaluations.
* **The Shadow Perspective**: For dimensions that lean heavily toward one realm, authors should actively identify and integrate their **shadow perspective** rather than forcing a 50/50 balance:
  - **The Spectrum Shadow (for Discrete-heavy dimensions)**: If a dimension is naturally discrete/binary (e.g., syntax or linkages), authors should define a spectrum shadow to evaluate overall style, rhythm, or coherence.
    * *Example (Notation Conformance)*: Discrete infractions (spelling/linter errors) are paired with a spectrum shadow of *typographic rhythm* or *stylistic consistency*.
    * *Example (Macro Topology)*: Discrete infractions (broken links/cycles) are paired with a spectrum shadow of *topological coherence* or *navigation flow*.
  - **The Discrete Shadow (for Spectrum-heavy dimensions)**: If a dimension is naturally continuous/qualitative (e.g., cognitive friction or conceptual correctness), authors should define a discrete shadow to give the auditor concrete, checkable infractions.
    * *Example (Reader Accessibility)*: The spectrum of cognitive load is paired with a discrete shadow of *jargon infractions* or *sentence-length violations*.
    * *Example (Semantic Fidelity)*: The spectrum of conceptual distortion is paired with a discrete shadow of *relationship inversions* or *hierarchy skips*.

This coordinate mapping ensures that dimensions are captured in their complete conceptual depth, but authors must not shoehorn either perspective into a dimension where it does not naturally fit.

### 5. Inquisitive & Informative Dual Framing (Semantic Projective Duality)
Every audit dimension specification must frame its target concept using both a **Statement** and a **Question** to capture the complete semantic space:
* **The Informative Statement (Banded Constant / Bounded)**:
  - *Manifestation*: Enforced in the introductory setup sentence and the `Constraint` definition.
  - *Mechanism*: Acts as an informative projection ($!p$) or extensional focus. It **minimizes** variability, state-space, and update frame, while **maximizing** invariance (acting as a constant), constraint rules, and update focus. This collapses alternatives to define a rigid boundary condition.
* **The Inquisitive Question (Unbounded Variable / Open)**:
  - *Manifestation*: Enforced in the `[conceptual_outcome_question]` of the introductory paragraph.
  - *Mechanism*: Acts as an inquisitive projection ($?p$) or intensional frame (interrogative type-shifting). It **minimizes** certainty, assertions, and real-world assumptions, while **maximizing** alternative paths, possibility state-spaces, and inquiry frames. This shifts the concept from a constant to a variable bounded by a domain, providing the auditor with the target problem context.



