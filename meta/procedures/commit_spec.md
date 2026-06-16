# Git Commit & Transactional Staging Specification (commit_spec.md)

This document defines the formal transactional staging standards, conventional commit specifications, and git history invariants required to guarantee traceability, cleanliness, and structural safety across the codebase history.

> [!CAUTION]
> **Scope Restriction**:
> This specification governs local commit creation only. All other Git operations (including remote syncing, branching, and merging) are strictly out of scope.

---

## Commit Compliance & Transactional Staging

Git history nodes must remain atomic, linear, and completely self-documenting, satisfying the verification rules defined in [commit_plan.md](/meta/procedures/commit_plan.md).

### Commit Message Formatting
> [!IMPORTANT]
> All commit messages strictly adhere to the Conventional Commits 1.0.0 specification. The structure consists of a type, a mandatory and non-optional scope, an imperative description, an optional body, and optional footers.

> [!WARNING]
> Summary lines are written exclusively in the imperative, present-tense mood, acting as a direct instruction to the codebase. Past-tense descriptions are invalid.

* **Commit Structure Blueprint**:
  - `type(scope): <imperative, present-tense description>` (Maximum 72 characters, where `scope` is mandatory)
  - `type(scope)!: <imperative, present-tense description>` (The `!` indicator denotes a breaking change, where `scope` is mandatory)
  - Blank line separator
  - `[detailed body explaining the WHY behind the changes, not just WHAT was changed]`
  - Blank line separator
  - `[footers]`

* **Valid Commit Types**:
  - `feature`: A new user-facing or technical capability.
  - `fix`: A resolution to a compile-time, runtime, logical, or E2E regression.
  - `refactor`: Structural, layout, or type safety improvements that make absolutely zero behavioral changes.
  - `test`: Addition, correction, or restructuring of test suites or test files.
  - `documentation`: Documentation modifications.
  - `chore`: Dependency updates, build script modifications, or general script cleanups.
  - `performance`: Logic optimizations aimed strictly at enhancing runtime execution speed or memory efficiency.
  - `release`: Bumping version numbers, generating changelogs, or preparing deployment targets.

---

## Transaction Purity & Staging Rules

### Staging and Diff Sanitization
* **No Stray Files**: Staged changes exclude temporary session files, debug logs, scratch scripts, and compiler artifacts. The [.gitignore](/.gitignore) boundary is strictly maintained.
* **Zero Debugging Artifacts**: Staged changes contain no temporary debugging code, logging statements, or placeholders.
* **Diff Purity**: Staged insertions and deletions represent a clean, semantic delta matching only the intended change scope.
