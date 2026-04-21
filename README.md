# AdoSprintTimer

AdoSprintTimer is a PowerShell 7 project for tracking time against Azure DevOps sprint work items with a local first timer and optional sync back to Azure DevOps Boards.

The intent is to make personal sprint time tracking simple, scriptable, and safe:

1. Discover the current sprint from Azure DevOps.
2. List work items assigned to the current user.
3. Start and stop a local timer against a specific work item.
4. Store the time log locally as the source of truth.
5. Roll up daily and monthly totals.
6. Optionally sync logged time back to Azure DevOps fields and work item history.

## Project Goal

This project is meant to produce a reusable PowerShell module named `AdoSprintTimer`.

The planned module is designed around these core principles:

1. Local log data is authoritative.
2. Azure DevOps is a sync target, not the timer engine.
3. PowerShell 7 is the primary runtime.
4. Public commands, private helpers, tests, and docs stay separated.
5. Sync behavior defaults to safe, non-destructive options.

## Planned Module Capabilities

The target module is expected to support:

1. Connection setup for Azure DevOps organization, project, team, user identity, and PAT.
2. Current sprint discovery through Azure DevOps REST APIs.
3. Retrieval of sprint work items assigned to the configured user.
4. Local timer start and stop operations for a selected work item.
5. Local JSON storage under `~/.ado-time/`.
6. Daily and monthly summaries of logged time.
7. Optional sync modes for history comments, completed work, and remaining work.
8. Pester based validation for storage lifecycle, timer lifecycle, summaries, and sync behavior.

## Current Repository State

This repository currently contains the project definition and workflow prompts used to generate and implement the module through a GitHub Spec style workflow.

At the moment, the repository contains:

1. The root project documentation.
2. A prompt workflow under [Prompts/README.md](Prompts/README.md).
3. Prompt files for requirements, specification, planning, task generation, implementation, audit, fixes, regression testing, release readiness, publishing, post-release monitoring, and system improvement.
4. Shared engineering constraints in [Prompts/principles.md](Prompts/principles.md).
5. A local-only planning folder [future-upgrades](future-upgrades) that is excluded from git push via [.gitignore](.gitignore).

## Repository Layout

Current top level contents:

1. [README.md](README.md)
   Project overview and repository guidance.
2. [Prompts](Prompts)
   Prompt workflow used to generate and validate the module implementation.
3. [LICENSE](LICENSE)
   Repository license.
4. [future-upgrades](future-upgrades)
   Local planning notes folder excluded from source control.

Prompt workflow contents:

1. [Prompts/00-Setup-GitHub-Spec-Foundation.md](Prompts/00-Setup-GitHub-Spec-Foundation.md)
   Sets up the repository for the GitHub Spec workflow.
2. [Prompts/01-Generate-Requirements.md](Prompts/01-Generate-Requirements.md)
   Generates project requirements.
3. [Prompts/02-Generate-Formal-Spec.md](Prompts/02-Generate-Formal-Spec.md)
   Produces the formal design spec.
4. [Prompts/03-Generate-Plan.md](Prompts/03-Generate-Plan.md)
   Creates the implementation plan.
5. [Prompts/04-Generate-Tasks.md](Prompts/04-Generate-Tasks.md)
   Breaks the plan into executable tasks.
6. [Prompts/05-Implement-Tasks.md](Prompts/05-Implement-Tasks.md)
   Implements the module from the generated artifacts.
7. [Prompts/06-Audit-Implementation.md](Prompts/06-Audit-Implementation.md)
   Audits the implementation against the spec artifacts.
8. [Prompts/07-Fix-From-Audit.md](Prompts/07-Fix-From-Audit.md)
   Applies targeted fixes from the audit.
9. [Prompts/08-Regression-Test.md](Prompts/08-Regression-Test.md)
   Validates the implementation after fixes.
10. [Prompts/09-Release-Readiness.md](Prompts/09-Release-Readiness.md)
   Validates production readiness before release.
11. [Prompts/10-Publish-Module.md](Prompts/10-Publish-Module.md)
   Guides packaging and publishing.
12. [Prompts/11-Post-Release-Monitoring.md](Prompts/11-Post-Release-Monitoring.md)
   Defines post-release operational monitoring.
13. [Prompts/12-Auto-Improve-System.md](Prompts/12-Auto-Improve-System.md)
   Improves the workflow based on outcomes over time.
14. [Prompts/Generate-Formal-Spec.md](Prompts/Generate-Formal-Spec.md)
   Compatibility prompt filename for legacy editor references.
15. [Prompts/principles.md](Prompts/principles.md)
    Defines the engineering and safety constraints for all generated work.

## Spec Workflow

The intended project workflow is:

1. Generate requirements.
2. Generate the formal spec.
3. Generate the implementation plan.
4. Generate executable tasks.
5. Implement from tasks.
6. Audit the result.
7. Fix issues found in the audit.
8. Run regression validation.
9. Validate release readiness.
10. Publish module artifacts.
11. Monitor behavior post-release.
12. Improve the prompt system based on observed outcomes.

The generated artifacts should live under:

- `specs/001-ado-sprint-timer/`

Once those files exist, they become the source of truth for implementation.

## Design Intent

The planned AdoSprintTimer module is intended to be:

1. Local first.
2. Easy to inspect and maintain.
3. Friendly to command line workflows.
4. Easy to extend later for a tray app, MAUI front end, SQLite backend, or branch based automation.

The design favors plain JSON storage first so the system stays simple and easy to debug before introducing heavier persistence layers.

## Engineering Constraints

This project is constrained by the rules in [Prompts/principles.md](Prompts/principles.md), including:

1. Use PowerShell 7.
2. Use `Set-StrictMode -Version Latest`.
3. Use `CmdletBinding` on all functions.
4. Return objects rather than formatted output.
5. Keep public and private function boundaries clear.
6. Handle Azure DevOps process dependent fields defensively.
7. Keep sync safe and support `WhatIf` and `Confirm` where appropriate.
8. Maintain test coverage for public behavior.

## Azure DevOps Scope

The project is intended to integrate with Azure DevOps through the REST API for:

1. Sprint discovery.
2. Team iteration work item retrieval.
3. Work item hydration.
4. Safe field updates.
5. History comment updates.

The expected API approach is:

1. Centralized REST helper logic.
2. API version `7.1`.
3. `GET` and `PATCH` support.
4. `application/json-patch+json` for updates.
5. Defensive handling for missing scheduling fields.

## Local Storage Model

The intended local storage area is:

- `~/.ado-time/`

Expected files:

1. `config.json`
   Connection and identity settings.
2. `active-timer.json`
   The currently running timer, if one exists.
3. `worklog-yyyy-MM.json`
   Monthly time entries.

This local data is intended to remain the source of truth even when Azure DevOps sync is enabled.

## Status

Project status right now:

1. Repository prompt workflow is present.
2. Root and prompt documentation are in place.
3. The full lifecycle prompt set is present through release and post-release operations.
4. The actual module implementation should follow the prompt and spec workflow rather than being improvised directly.
5. Compatibility prompt filenames are present for older path references.

## Getting Started

If you are working on this repository, start here:

1. Read [Prompts/README.md](Prompts/README.md).
2. Review [Prompts/principles.md](Prompts/principles.md).
3. Generate or update the artifacts under `specs/001-ado-sprint-timer/`.
4. Implement only from those generated artifacts.
5. Run audit and regression prompts after implementation changes.
6. Run release readiness and publish prompts only after regression passes.

## Long Term Direction

The long term direction for AdoSprintTimer includes:

1. A production quality PowerShell module.
2. Optional SQLite storage.
3. Better sync idempotency tracking.
4. Possible tray or desktop UI.
5. Branch name to work item mapping.
6. VS Code task integration.

## Summary

AdoSprintTimer is a local first Azure DevOps sprint time tracking project with a PowerShell module target and a spec driven workflow. This repository currently documents and drives that implementation process through the prompt system under [Prompts](Prompts).

Local planning note:

- [future-upgrades](future-upgrades) is intentionally local-only and ignored by git.
