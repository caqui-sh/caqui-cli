# Git Commit Procedural Plan (commit_plan.md)

This document defines the step-by-step execution procedures, terminal commands, and validation protocols required to implement the standards of [commit_spec.md](/meta/procedures/commit_spec.md) for every commit transaction.

> [!CAUTION]
> **Scope Restriction**:
> This plan governs procedural execution for local commit creation only. All other Git operations (including remote syncing, branching, and merging) are out of scope.

---

## Step-by-Step Commit Staging & Verification Procedure

### Phase 1: Pre-Staging Workspace Audit
Perform a structural scan of the workspace to isolate target changes and identify any unintended artifacts before git commands are executed.

* **Procedure 1.1: Identify Modified and Untracked Files**
  - Execute `git status` to retrieve a list of all modified, untracked, and deleted files.
  - Review the list to confirm all changes are strictly relevant to the specific logical target scope.

* **Procedure 1.2: Check for Stray and Temporary Files**
  - Identify any temporary artifacts, runtime log files, build products, system configuration caches, editor session/swap files, or auto-generated lists.
  - Ensure all such files are either added to `.gitignore` or strictly avoided during staging. **DO NOT** use broad wildcard commands like `git add .` or `git add -A` to prevent staging untracked workspace noise.

* **Procedure 1.3: Clean Debugging and Placeholder Statements**
  - Run a workspace-wide grep or search for temporary debugging code, logging statements, and placeholders.
  - Delete or revert these statements entirely to ensure they do not contaminate the final commit.

---

### Phase 2: Transactional Staging & Diff Sanitization
Incrementally prepare the git index, ensuring only pure, semantic changes are staged.

* **Procedure 2.1: Targeted Staging**
  - Stage files individually using `git add <file_path>` to ensure no unrelated files are packaged into the commit.
  - For files containing multiple separate changes, use interactive staging (`git add -p <file_path>`) to selectively stage only the relevant logical chunks.

* **Procedure 2.2: Ocular Diff Verification**
  - Execute `git diff --cached` to output the exact changes staged in the git index.
  - Perform a line-by-line ocular audit of every staged insertion (`+`) and deletion (`-`) to verify:
    - Zero temporary debugging comments or logger statements remain.
    - Formatting and indentations are clean and conform to codebase style.
    - No unintended code modifications are present.

---

### Phase 3: Message Formatting & Validation
Draft and validate a commit message that matches the semantic requirements and Conventional Commit specifications of [commit_spec.md](/meta/procedures/commit_spec.md).

* **Procedure 3.1: Select Type & Scope from Specification**
  - Select the precise commit type from the approved list defined in [commit_spec.md](/meta/procedures/commit_spec.md).
  - Identify and specify the mandatory scope. A scope is strictly required and mandatory for all commits.

* **Procedure 3.2: Formulate Imperative Summary Line**
  - Draft the description in the present-tense, imperative mood as instructed in [commit_spec.md](/meta/procedures/commit_spec.md).
  - Verify that the character length of the summary line satisfies the approved length limit constraints in [commit_spec.md](/meta/procedures/commit_spec.md).
  - Append the `!` breaking change indicator after the type/scope if the commit contains breaking changes.

* **Procedure 3.3: Draft Body and BREAKING CHANGE Footers**
  - If the changes are complex, add a blank line after the summary and write a concise body explaining the architectural "why".
  - If the commit contains breaking changes, append the approved `BREAKING CHANGE: <explanation>` footer format.

---

### Phase 4: Commit Execution & Verification
Create the commit transaction and audit the resulting git history node.

* **Procedure 4.1: Execute the Commit**
  - Run the commit command: `git commit -m "<message>"` (or run `git commit` to use the configured text editor for multi-line messages).

* **Procedure 4.2: Audit the Created Commit**
  - Run `git show --stat HEAD` to verify that:
    - The commit message matches the conventional format perfectly.
    - Exactly the intended files were committed.
  - Run `git show HEAD` to review the final commit diff one last time for total correctness.
