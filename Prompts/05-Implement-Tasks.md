# Implement Tasks

Implement the AdoSprintTimer PowerShell 7 module using the GitHub Spec workflow.

You MUST use the following files as the source of truth:

- specs/001-ado-sprint-timer/requirements.md
- specs/001-ado-sprint-timer/spec.md
- specs/001-ado-sprint-timer/plan.md
- specs/001-ado-sprint-timer/tasks.md
- principles.md

Do NOT invent new architecture unless required to fix a clear defect in the spec.
Do NOT skip tasks.
Do NOT collapse the module into a single script.

## Implementation Rules

- Follow tasks.md exactly in order.
- Each task must be fully completed before moving to the next.
- Maintain separation of:
  - public functions
  - private helpers
  - tests
  - documentation

## PowerShell Requirements

- Use PowerShell 7
- Use Set-StrictMode -Version Latest
- Use CmdletBinding for all functions
- Use typed parameters and validation attributes
- Return objects, not formatted output
- Use Write-Verbose for major operations

## Architecture Constraints

- Local log is the source of truth
- Azure DevOps is a sync target only
- Store data in ~/.ado-time/
- Use JSON for storage unless spec defines otherwise
- Use REST API version 7.1

## Azure DevOps Rules

- Use a centralized Invoke-AdoRestMethod helper
- Use PATCH with application/json-patch+json
- Handle missing fields like RemainingWork or CompletedWork safely
- Never reduce RemainingWork below zero
- Support WhatIf and Confirm for sync operations

## Testing Requirements

- Implement Pester tests alongside functionality
- Mock Azure DevOps API calls
- Validate:
  - config lifecycle
  - timer lifecycle
  - work log storage
  - summary calculations
  - sync modes

## Output Requirements

You must:

1. Create all files defined in the spec
2. Implement all module functionality
3. Implement all tests
4. Update README.md with real usage examples
5. Summarize assumptions and any deviations from the spec

## Important

- The spec defines the system, not this prompt
- If there is a conflict, follow the spec
