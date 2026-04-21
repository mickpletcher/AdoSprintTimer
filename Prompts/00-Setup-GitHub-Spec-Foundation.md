# Setup GitHub Spec Foundation

Review the current AdoSprintTimer repository and refactor the repo structure to support a proper GitHub Spec workflow.

Goals:

1. Move prompt files into the correct location.
2. Add a real specs output structure.
3. Add workflow guidance so future implementation is driven by generated specs, not just prompts.
4. Tighten implementation guardrails so Copilot follows the generated artifacts.

Make the following changes exactly.

## 1. Prompt location

Move the existing prompt files from the current prompts folder into:

.github/prompts/

Preserve the numbered execution order.

Target prompt files:

- 00-Generate-Requirements.md
- 01-Generate-Formal-Spec.md
- 02-Generate-Plan.md
- 03-Generate-Tasks.md
- 04-Implement-Tasks.md
- Build-AdoSprintTimer-PowerShell-Module.md

If the current filenames differ slightly, normalize them to the names above and update any references.

## 2. Add specs output structure

Create this folder structure:

specs/
  001-ado-sprint-timer/

Inside that folder, create placeholder markdown files with clear section headings for:

- requirements.md
- spec.md
- plan.md
- tasks.md

These are generated artifacts, not prompts.
Each file should contain a short header explaining its purpose in the workflow.

## 3. Add spec workflow documentation

Update the root README.md to add a new section named:

## Spec Workflow

Document this flow clearly:

1. Generate requirements
2. Generate formal spec
3. Generate implementation plan
4. Generate executable tasks
5. Implement from tasks

Add a note that implementation must be based on files in:

specs/001-ado-sprint-timer/

and not directly from prompt files.

Also add a short section explaining the purpose of principles.md and how it constrains generated output.

## 4. Strengthen implementation prompt

Update:

.github/prompts/04-Implement-Tasks.md

Add explicit guardrails so the implementation prompt tells Copilot to:

- read and follow requirements.md, spec.md, plan.md, and tasks.md
- treat those files as the source of truth
- not invent architecture outside the spec unless required to fix an obvious defect
- not collapse the module into one monolithic script
- preserve separation of public functions, private helpers, tests, and documentation
- implement tests along with code
- respect principles.md

## 5. Add a front door prompt

Create a new prompt file:

.github/prompts/00-Generate-Requirements-From-Idea.md

Purpose:
This prompt should take a short natural language idea for the repo or feature and generate a structured requirements.md file under:

specs/001-ado-sprint-timer/requirements.md

The prompt should instruct Copilot to:

- convert a rough idea into testable requirements
- define functional and nonfunctional requirements
- include storage, API, sync safety, error handling, and testing requirements
- keep the requirements implementation neutral

## 6. Validate references

Search the repo for any old references to the previous prompts folder location and update them.
Ensure README examples and internal references point to:

.github/prompts/

and

specs/001-ado-sprint-timer/

## 7. Keep this repo clean

Do not add unnecessary ceremony.
Do not add extra spec folders.
Do not add placeholder implementation code unrelated to the repo structure cleanup.
Focus only on restructuring the repo for a correct GitHub Spec pipeline.

## Deliverables

Make the file and README updates directly.
At the end, provide a concise summary of:

- files moved
- files created
- files updated
- any assumptions made
