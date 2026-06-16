# Codebase Verification Specification (verification_spec.md)

This document establishes the declarative verification standards, structural invariants, static analysis requirements, and test topologies mandated to guarantee absolute safety, correctness, and architectural integrity across the codebase.

---

## 1. Static Analysis & Compiler Invariants

Static analysis is the first line of defense. The codebase must compile under strict flags with zero tolerance for developer warnings.

### 1.1 Rust / Cargo Verification Gates
> [!IMPORTANT]
> Rust code compilation is not merely about producing a binary; it is about satisfying the compiler's strict lifetime and borrow-checker invariants.

* **Zero Warnings Directive**: The compiler must emit exactly **zero warnings**. Any warning, including unused variables, dead code, or deprecated features, is considered a gate violation.
* **Clippy Lint Invariants**: The codebase enforces safety and correctness invariants through strict lint restrictions, denying unsafe blocks and panicking/unwrapping constructs at the crate level:
  - **Unsafe Code Prohibition**: Enforced via `#![deny(unsafe_code)]` (or `-D unsafe-code`). Safe Rust is mandated across all modules.
  - **No Panic Paths**: Enforced via `#![deny(clippy::panic, clippy::todo, clippy::unimplemented)]`. Production-ready paths must not contain explicit panicking/abort pathways.
  - **Explicit Error Propagation**: Enforced via `#![deny(clippy::unwrap_used, clippy::expect_used)]`. All options and results must employ explicit error propagation (`?`) or pattern matching.

### 1.2 Deno / TypeScript Verification Gates
* **TypeScript Compilation Gate**: All E2E test files and supporting automation scripts must compile and type-check successfully with zero type errors.
* **Strict Linting Gate**: Code style and practices inside the TypeScript test suites must pass strict lint checks with zero warning or error diagnostics.

---

## 2. E2E Test Topology & Standards

The codebase's dynamic behavior must be fully verified using the E2E test suites located in `meta/tests/`.

* **Mandatory Pipeline Entrypoint**: All dynamic system verification must be executed exclusively via the orchestration command `deno task test` (which runs `run_tests.sh`). This orchestrator enforces compiling the binary and ensures compliance with the following execution standards:
  - **Execution Environment Isolation**: Tests must spawn isolated server/client loops over localhost (`127.0.0.1`), ensuring they do not leak state or bind to external network interfaces.
  - **Parallel Execution Correctness**: The system's architecture must support high-concurrency test runs. All E2E tests must execute and pass in parallel without race conditions or shared database locks.
* **Resource Lifecycle Cleanup**: All spawned server binaries, network ports, and temporary system/file resource locks **MUST** be cleaned up completely upon completion of execution. No dangling processes or orphaned sockets are permitted to survive.

