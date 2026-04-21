# Engineering Principles

## Architecture

- Build reusable modules, not monolithic scripts
- Keep public and private functions separated
- Keep the local log as the source of truth
- Treat Azure DevOps as a sync target, not the timer source

## PowerShell Standards

- Use PowerShell 7
- Use Set-StrictMode -Version Latest
- Use CmdletBinding on all functions
- Return objects, not formatted output
- Use typed parameters and validation attributes
- Use Write-Verbose for major execution steps

## Safety

- Sync must default to the safest mode
- Never assume Azure DevOps fields exist across all processes
- Never reduce RemainingWork below zero
- Handle corrupt JSON and missing files gracefully
- Support WhatIf and Confirm on destructive or update operations

## Testing

- Every public function must have test coverage
- Mock Azure DevOps API calls in Pester
- Validate file lifecycle and sync behavior

## Documentation

- Every public function must include comment based help
- README examples must reflect real commands in the module
- Assumptions and Azure DevOps caveats must be documented
