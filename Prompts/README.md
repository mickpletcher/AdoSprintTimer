# Prompts Directory

This directory contains the prompt set used to drive the AdoSprintTimer GitHub Spec workflow.

These prompts are intended to be used in sequence unless a later corrective step is needed.
The prompts define how requirements, specs, plans, tasks, implementation, audit, fixes, and regression validation should be produced and applied.

The generated artifacts are expected to live under:

- `specs/001-ado-sprint-timer/`

The implementation should follow those generated spec artifacts, not the prompt text directly, once the artifacts exist.

## Prompt Order

### `00-Setup-GitHub-Spec-Foundation.md`

Initial repository structure setup prompt.
Use this to establish or repair the GitHub Spec workflow foundation in the repository.

What it does:

1. Refactors prompt placement and prompt naming.
2. Adds the `specs/001-ado-sprint-timer/` output structure.
3. Adds workflow documentation.
4. Tightens implementation guardrails.
5. Validates prompt and spec references across the repo.

Use this when:

- the repo structure is not aligned to the intended spec workflow
- prompts or spec outputs need to be normalized
- workflow guardrails need to be re-established

### `01-Generate-Requirements.md`

Requirements generation prompt.
Use this to create `specs/001-ado-sprint-timer/requirements.md` from the product idea.

What it focuses on:

1. Functional requirements.
2. Nonfunctional requirements.
3. Error handling requirements.
4. Storage requirements.
5. Sync safety requirements.
6. Testing requirements.

Expected output:

- implementation-neutral, testable requirements

### `02-Generate-Formal-Spec.md`

Formal specification prompt.
Use this to transform `requirements.md` into `spec.md`.

What it defines:

1. Architecture.
2. Module structure.
3. Public functions.
4. Private helpers.
5. Local file schemas.
6. API interaction design.
7. Sync modes.
8. Idempotency approach.
9. Error handling model.
10. Pester testing strategy.

Expected output:

- concrete design and behavior without implementation code

### `03-Generate-Plan.md`

Implementation planning prompt.
Use this to generate `plan.md` from `spec.md`.

What it focuses on:

1. Phased implementation order.
2. Dependencies.
3. Risks.
4. Validation steps.
5. Testability.
6. Extensibility.

Expected output:

- a staged implementation plan optimized for local-first behavior and safe Azure DevOps sync

### `04-Generate-Tasks.md`

Task breakdown prompt.
Use this to generate `tasks.md` from `plan.md`.

What it requires:

1. Concrete executable tasks.
2. Exact file targets.
3. Specific changes to make.
4. Expected results.
5. Validation notes.
6. Phase grouping.

Expected output:

- an ordered task list that can be implemented directly

### `05-Implement-Tasks.md`

Primary implementation prompt.
Use this to build the module from the generated spec artifacts.

This prompt enforces:

1. `requirements.md`, `spec.md`, `plan.md`, and `tasks.md` as the source of truth.
2. Respect for `principles.md`.
3. PowerShell 7 standards.
4. Strict separation of public functions, private helpers, tests, and documentation.
5. Safe Azure DevOps sync behavior.
6. Tests implemented alongside code.

Use this when:

- the spec artifacts are ready and implementation should begin

### `06-Audit-Implementation.md`

Implementation audit prompt.
Use this after implementation to compare the current codebase against the generated spec artifacts.

What it evaluates:

1. Requirements coverage.
2. Spec compliance.
3. Plan alignment.
4. Task completion.
5. Principles enforcement.
6. Code quality.
7. Azure DevOps integration.
8. Local storage behavior.
9. Tests and documentation.

Expected output:

- a structured gap analysis with severity, missing features, drift detection, and recommended fixes

### `07-Fix-From-Audit.md`

Corrective implementation prompt.
Use this after an audit identifies issues.

What it does:

1. Applies fixes from the most recent audit.
2. Preserves spec alignment.
3. Updates code, tests, and README as needed.
4. Focuses on correction, not redesign.

Use this when:

- the audit found critical, medium, or minor issues that must be brought back into compliance

### `08-Regression-Test.md`

Regression validation prompt.
Use this after fixes have been applied.

What it validates:

1. End-to-end functional behavior.
2. Regression detection.
3. Data integrity.
4. Azure DevOps integration behavior.
5. Edge case handling.
6. PowerShell compliance.
7. Architecture integrity.
8. Test suite health.
9. Documentation accuracy.

Expected output:

- a PASS or FAIL style regression report with targeted fixes if issues remain

### `09-Release-Readiness.md`

Release readiness prompt.
Use this after implementation, fixes, and regression testing are complete.

What it validates:

1. Build integrity.
2. Versioning.
3. Module packaging.
4. Installation scenarios.
5. Documentation quality.
6. Security handling.
7. Dependency health.
8. Test readiness.
9. Spec alignment.
10. Performance and stability.

Expected output:

- a structured READY or NOT READY report for release decisions

### `10-Publish-Module.md`

Publishing prompt.
Use this when the module has passed release readiness and should be packaged and published.

What it covers:

1. Pre-publish validation.
2. Version checks.
3. Packaging rules.
4. Git tagging.
5. Release notes.
6. Optional PowerShell Gallery publishing.

Expected output:

- a repeatable publishing plan and release artifact guidance

### `11-Post-Release-Monitoring.md`

Post-release monitoring prompt.
Use this after the module is shipped and real-world usage begins.

What it focuses on:

1. Issue tracking.
2. Production feedback analysis.
3. Stability monitoring.
4. Regression detection.
5. Security monitoring.
6. Performance monitoring.
7. Ongoing spec alignment.

Expected output:

- a health and patch planning report based on production signals

### `12-Auto-Improve-System.md`

System improvement prompt.
Use this to improve the workflow itself after one or more implementation cycles.

What it analyzes:

1. Recurring failure patterns.
2. Prompt effectiveness.
3. Spec quality.
4. Task generation quality.
5. Testing effectiveness.
6. Architecture drift causes.

Expected output:

- system-level recommendations to reduce future defects and improve determinism

### `principles.md`

Engineering constraints file.
This is not a generation step by itself.

It defines the rules that all generated outputs and implementation work should respect, including:

1. Reusable module architecture.
2. Public and private separation.
3. Local-first design.
4. PowerShell 7 coding standards.
5. Safe sync behavior.
6. Required testing discipline.
7. Documentation expectations.

Treat this file as a standing constraint across the full workflow.

## Recommended Workflow

Use the prompt set in this order for normal feature delivery:

1. `00-Setup-GitHub-Spec-Foundation.md` if the workflow structure needs to be established or corrected.
2. `01-Generate-Requirements.md`
3. `02-Generate-Formal-Spec.md`
4. `03-Generate-Plan.md`
5. `04-Generate-Tasks.md`
6. `05-Implement-Tasks.md`
7. `06-Audit-Implementation.md`
8. `07-Fix-From-Audit.md`
9. `08-Regression-Test.md`
10. `09-Release-Readiness.md`
11. `10-Publish-Module.md`
12. `11-Post-Release-Monitoring.md`
13. `12-Auto-Improve-System.md`

If the repository structure is already correct, start at step 2.

## Source Of Truth Rules

1. Prompts generate artifacts.
2. Generated artifacts under `specs/001-ado-sprint-timer/` define the system.
3. `principles.md` constrains all generated and implemented work.
4. Once requirements, spec, plan, and tasks exist, implementation should follow those files rather than improvising from the prompts.

## Compatibility Filenames

This directory may include compatibility prompt filenames for editor state or legacy links.

Current compatibility file:

- `Generate-Formal-Spec.md`

Compatibility files are not part of the ordered prompt chain.
For normal workflow execution, use the numbered prompt files.

## Reference Subdirectory

The `reference/` subdirectory is not part of the active prompt chain.

Use it only for supporting context or historical reference.
If a prompt exists both in this directory and under `reference/`, the file in this directory is the active version.
