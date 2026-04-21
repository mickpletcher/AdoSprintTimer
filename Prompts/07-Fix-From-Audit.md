# Fix From Audit

Apply fixes to the AdoSprintTimer PowerShell 7 module based on the most recent audit report.

## Source of truth

You MUST use:

- The audit output generated from 06-Audit-Implementation.md
- specs/001-ado-sprint-timer/requirements.md
- specs/001-ado-sprint-timer/spec.md
- specs/001-ado-sprint-timer/plan.md
- specs/001-ado-sprint-timer/tasks.md
- principles.md

## Goal

Resolve all issues identified in the audit while maintaining strict alignment with the spec and principles.

---

## Fix Strategy

### 1. Critical Issues (highest priority)

- Fix all issues that break functionality or violate the spec
- Ensure implementation matches requirements and spec exactly
- Do not proceed until critical issues are resolved

### 2. Medium Issues

- Fix structural problems
- Correct architectural inconsistencies
- Improve error handling and validation

### 3. Minor Issues

- Improve code quality and readability
- Refactor where needed without changing behavior
- Enhance logging, validation, and consistency

---

## Execution Rules

- Apply fixes incrementally
- Validate each fix before moving to the next
- Do not introduce regressions
- Do not rewrite unrelated code
- Do not remove working functionality unless it conflicts with the spec

---

## Spec Enforcement

- The spec is authoritative
- If audit findings conflict with the spec, follow the spec
- Do not invent new features not defined in requirements or tasks
- Do not change architecture unless required to fix a spec violation

---

## PowerShell Requirements

- Maintain PowerShell 7 compatibility
- Preserve Set-StrictMode -Version Latest
- Ensure all functions use CmdletBinding
- Preserve parameter validation and typing
- Return objects from public functions
- Do not introduce Write-Host for functional output

---

## Architecture Constraints

- Maintain separation of:
  - Public functions
  - Private helpers
  - Tests
  - Documentation
- Do not collapse into a single script
- Reuse existing helpers instead of duplicating logic

---

## Azure DevOps Constraints

- Ensure REST calls use centralized helper
- Validate API usage and headers
- Ensure safe handling of:
  - RemainingWork
  - CompletedWork
- Never reduce RemainingWork below zero
- Ensure sync modes behave correctly
- Improve or implement idempotency if missing

---

## Local Storage Constraints

- Preserve ~/.ado-time structure
- Ensure:
  - config.json
  - active-timer.json
  - worklog-yyyy-MM.json
- Fix any schema inconsistencies
- Add defensive handling for corrupt or missing files

---

## Testing Requirements

- Fix or add tests for all corrected functionality
- Ensure tests cover:
  - config lifecycle
  - timer lifecycle
  - work log behavior
  - summary calculations
  - sync behavior
- Mock Azure DevOps API calls
- Ensure tests pass after fixes

---

## Documentation Requirements

- Update README.md to reflect fixes
- Ensure examples are accurate and runnable
- Document any behavior changes

---

## Output Requirements

You must:

1. Apply all fixes based on the audit
2. Update or add tests as needed
3. Update README.md if behavior changes
4. Summarize:
   - fixes applied
   - files modified
   - any remaining issues
   - any assumptions made

---

## Constraints

- Do not re-audit the code
- Do not produce a new audit report
- Focus only on fixing issues identified previously
- Be precise and minimal in changes
- Preserve working functionality wherever possible

---

## Important

- This is a corrective phase, not a redesign phase
- The spec defines correctness
- The audit defines what must be fixed
- Your job is to bring the implementation into compliance
