# Release Readiness

Prepare the AdoSprintTimer PowerShell 7 module for release by validating production readiness and ensuring the project is ready for distribution.

## Source of truth

You MUST validate against:

- specs/001-ado-sprint-timer/requirements.md
- specs/001-ado-sprint-timer/spec.md
- specs/001-ado-sprint-timer/plan.md
- specs/001-ado-sprint-timer/tasks.md
- principles.md

You MUST also consider:

- the current implementation
- results from 06-Audit-Implementation.md
- fixes applied from 07-Fix-From-Audit.md
- validation results from 08-Regression-Test.md

---

## Goal

Ensure the module is:

- stable
- fully compliant with the spec
- properly versioned
- documented
- installable
- ready for publishing (PowerShell Gallery or internal distribution)

---

## Release Readiness Scope

### 1. Build Integrity

- Confirm module loads without errors
- Validate module manifest (.psd1)
- Ensure required files are present
- Verify no missing dependencies
- Ensure no debug or incomplete code remains

---

### 2. Versioning

- Validate module version in .psd1
- Ensure version follows semantic versioning
- Confirm version increment from previous release
- Validate compatibility with PowerShell 7

---

### 3. Module Packaging

- Ensure module structure is correct:
  - psd1
  - psm1
  - Public/
  - Private/
  - Tests/
- Confirm Export-ModuleMember exports only public functions
- Validate module imports cleanly using Import-Module

---

### 4. Installation Validation

Simulate installation scenarios:

- Local import via path
- Import after copying to standard module path
- Confirm commands are discoverable via Get-Command
- Confirm no path dependency issues

---

### 5. Documentation Validation

- README.md is complete and accurate
- Includes:
  - installation instructions
  - configuration steps
  - usage examples
- Examples must be runnable and match actual behavior
- Ensure no outdated or misleading content

---

### 6. Security Review

- Ensure no secrets are hardcoded
- Validate PAT handling is secure and documented
- Ensure no sensitive data is logged
- Confirm safe handling of configuration files

---

### 7. Dependency Review

- Confirm no unnecessary dependencies
- Validate all required modules are documented
- Ensure compatibility with PowerShell 7 environments

---

### 8. Test Validation

- All Pester tests pass
- No skipped or incomplete tests
- Test suite covers critical functionality
- Tests can be run independently

---

### 9. Spec Compliance Check

- Confirm implementation still aligns with:
  - requirements.md
  - spec.md
- Ensure no drift introduced after fixes

---

### 10. Performance and Stability

- Validate no obvious performance bottlenecks
- Ensure no infinite loops or blocking calls
- Confirm reasonable execution time for core functions

---

### 11. Release Artifacts

Prepare the following:

- Clean module directory
- README.md
- Module manifest (.psd1)
- Optional:
  - LICENSE file
  - CHANGELOG.md

---

## Output Format

Return a structured release readiness report:

### 1. Release Status

- READY or NOT READY
- Brief explanation

### 2. Build Integrity Issues

- List any problems

### 3. Versioning Issues

- List inconsistencies

### 4. Packaging Issues

- Structural or module problems

### 5. Installation Issues

- Import or execution failures

### 6. Documentation Gaps

- Missing or incorrect documentation

### 7. Security Concerns

- Any risks identified

### 8. Test Issues

- Failing or missing tests

### 9. Spec Drift

- Any mismatch with spec

### 10. Required Fixes Before Release

- Prioritized list of fixes

### 11. Optional Improvements

- Non-blocking enhancements

---

## Constraints

- Do not rewrite the codebase
- Do not re-run full audit
- Focus on release readiness validation
- Be precise and technical
- Do not skip any category

---

## Important

- The module must be production ready
- If any critical issue exists, mark as NOT READY
- The spec defines correctness
- This step determines if the module can be shipped
