# Audit Implementation

Audit the current implementation of the AdoSprintTimer PowerShell 7 module against the GitHub Spec artifacts.

## Source of truth

You MUST compare the implementation against:

- specs/001-ado-sprint-timer/requirements.md
- specs/001-ado-sprint-timer/spec.md
- specs/001-ado-sprint-timer/plan.md
- specs/001-ado-sprint-timer/tasks.md
- principles.md

## Goal

Evaluate how closely the current codebase matches the defined specification, identify gaps, detect drift, and recommend precise fixes.

---

## Audit Scope

### 1. Requirements Coverage

- Verify each requirement is implemented
- Identify missing or partially implemented requirements
- Flag any behavior not defined in requirements

### 2. Spec Compliance

- Validate architecture matches spec.md
- Confirm module structure (Public, Private, Tests)
- Validate command contracts and expected outputs
- Check local storage design and schema adherence
- Verify API usage patterns

### 3. Plan Alignment

- Confirm implementation followed plan.md phases
- Identify skipped or out-of-order phases that caused issues

### 4. Task Completion

- Evaluate each task in tasks.md:
  - Completed
  - Partially completed
  - Not implemented
- Identify incorrect implementations

### 5. Principles Enforcement

- Check adherence to principles.md:
  - strict mode
  - CmdletBinding usage
  - object-based output
  - separation of concerns
  - no monolithic scripts
  - safe Azure DevOps updates

---

## Code Quality Review

### PowerShell Standards

- Proper use of CmdletBinding
- Parameter validation and typing
- Verbose logging usage
- No Write-Host for functional output
- Functions are small and focused

### Architecture

- Public vs private separation enforced
- Module loader (psm1) correctly structured
- No duplicated logic
- Reusable helper functions implemented

### Error Handling

- Robust handling of:
  - missing config
  - corrupt JSON
  - missing fields from Azure DevOps
  - API failures

---

## Azure DevOps Integration Audit

- Centralized REST helper used
- Correct API version usage
- PATCH format correct
- Missing fields handled safely
- RemainingWork never goes below zero
- Sync modes implemented correctly
- Idempotency strategy present or missing

---

## Local Storage Audit

- ~/.ado-time directory correctly used
- config.json lifecycle valid
- active-timer.json lifecycle valid
- worklog-yyyy-MM.json structure consistent
- Corrupt file handling implemented

---

## Testing Audit

- Pester tests exist
- Tests cover:
  - config lifecycle
  - timer lifecycle
  - work log behavior
  - summary calculations
  - sync behavior
- Azure DevOps API calls are mocked

---

## Documentation Audit

- README exists and is accurate
- Examples are runnable
- Setup instructions are clear
- Azure DevOps caveats documented

---

## Output Format

Return a structured audit report with:

### 1. Overall Score

- Percentage score (0–100)
- Brief summary of implementation quality

### 2. Coverage Summary

- Requirements coverage %
- Task completion %
- Test coverage %

### 3. Critical Issues

- List of issues that break functionality or spec compliance

### 4. Medium Issues

- Structural or quality issues

### 5. Minor Issues

- Improvements and polish

### 6. Missing Features

- Clearly list unimplemented requirements or tasks

### 7. Drift Detection

- Any logic implemented that is not defined in spec

### 8. Recommended Fixes

- Provide specific, actionable fixes
- Reference exact files and functions where possible

### 9. Next Actions

- Ordered list of what should be fixed first

---

## Constraints

- Do not rewrite the entire codebase
- Focus on analysis and targeted fixes
- Be precise and technical
- Do not give generic advice
- Do not skip any audit section

---

## Important

- The spec defines correctness, not the current implementation
- If implementation conflicts with spec, the spec wins
- Be strict in evaluation
