# Verification Procedural Plan (verification_plan.md)

This document defines the step-by-step execution procedures, terminal commands, and validation protocols required to implement and enforce the standards defined in the declarative [verification_spec.md](/meta/procedures/verification_spec.md).

---

## Phase 1: Static Analysis & Compiler Invariants (L1 Gates)

Verify compile-time type-safety, styling, and linter constraints across the codebase.

### Step 1.1: Rust Compilation & Lint Audit
Validate that all Rust crates build successfully and satisfy strict safety lints.
* **Execution Commands**:
  ```bash
  cargo fmt --all -- --check
  cargo check --workspace
  cargo clippy --workspace --all-targets --all-features -- -D warnings
  ```
* **Procedural Check**: Ensure all commands exit with code 0 and emit zero compiler errors, format warnings, or Clippy lint violations.

### Step 1.2: Deno/TypeScript Lint & Type Check
Validate that E2E test suites and automation scripts are correctly formatted and free of TypeScript compilation errors.
* **Execution Commands**:
  ```bash
  cd meta/tests
  deno lint
  deno check source/**/*.ts
  ```
* **Procedural Check**: Ensure commands exit with code 0 and emit zero warning or diagnostic errors.

---

## Phase 2: End-to-End Testing (L2 Gates)

Verify the dynamic runtime behavior of the compiled system as a cohesive whole.

### Step 2.1: Execute the Verification Pipeline
Run the mandatory test suite orchestration script.
* **Execution Command**:
  ```bash
  cd meta/tests
  deno task test
  ```
* **Procedural Check**: Verify that the command builds the binaries, executes the E2E tests in parallel, and completes with a 100% success rate.

### Step 2.2: Process Cleanup & Socket Audit
Verify complete lifecycle cleanup of background processes and port limits to satisfy [verification_spec.md](/meta/procedures/verification_spec.md) Section 2.
* **Execution Commands**:
  - Audit for orphaned database/server processes:
    ```bash
    ps aux | grep caqui | grep -v grep
    ```
  - Audit for bound or listening network sockets:
    ```bash
    lsof -i :8000
    ```
* **Cleanup Routine**: If dangling resources are found, terminate them:
  ```bash
  killall caqui || true
  ```
* **Procedural Check**: Confirm that no background processes survive and no network sockets remain bound upon test completion.

