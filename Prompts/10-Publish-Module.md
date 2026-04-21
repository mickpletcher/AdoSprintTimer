# Publish Module

Publish the AdoSprintTimer PowerShell 7 module as a release artifact and optionally to the PowerShell Gallery.

## Source of truth

You MUST validate against:

- specs/001-ado-sprint-timer/requirements.md
- specs/001-ado-sprint-timer/spec.md
- specs/001-ado-sprint-timer/plan.md
- specs/001-ado-sprint-timer/tasks.md
- principles.md

You MUST also consider:

- results from 09-Release-Readiness.md
- current implementation state

---

## Goal

Package, version, tag, and publish the module in a clean, repeatable, and secure way.

---

## Pre-Publish Validation

Before publishing, confirm:

- Release status from 09-Release-Readiness.md is READY
- All tests pass
- No critical issues remain
- README.md is accurate
- Module manifest (.psd1) is correct
- Version number is properly incremented

If any of these fail:

- STOP
- Report blocking issues

---

## Versioning

- Validate semantic versioning format (MAJOR.MINOR.PATCH)
- Ensure version has been incremented from previous release
- Update version in .psd1 if needed
- Ensure version aligns with changes (breaking vs non-breaking)

---

## Packaging

Prepare the module for release:

- Ensure clean directory structure:
  - AdoSprintTimer/
    - AdoSprintTimer.psd1
    - AdoSprintTimer.psm1
    - Public/
    - Private/
    - README.md

- Exclude:
  - .git
  - .github
  - tests (optional depending on distribution strategy)
  - temporary or debug files

- Validate module loads from packaged location

---

## Git Tagging

- Create a git tag using the module version:
  - vX.Y.Z

- Tag message should summarize:
  - key features
  - fixes
  - improvements

- Push tag to remote repository

---

## Release Notes

Generate release notes including:

- Summary of changes
- New features
- Bug fixes
- Breaking changes (if any)
- Upgrade notes

If CHANGELOG.md exists:

- Update it accordingly

---

## PowerShell Gallery Publishing (optional)

If publishing to PowerShell Gallery:

- Validate API key is available securely
- Do not hardcode API key
- Use Publish-Module

Example:

```powershell
Publish-Module -Path ./AdoSprintTimer -NuGetApiKey $env:PSGALLERY_API_KEY
```
