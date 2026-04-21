# Regression Test

Run a full regression validation of the AdoSprintTimer PowerShell 7 module after fixes have been applied.

## Source of truth

You MUST validate against:

- specs/001-ado-sprint-timer/requirements.md
- specs/001-ado-sprint-timer/spec.md
- specs/001-ado-sprint-timer/plan.md
- specs/001-ado-sprint-timer/tasks.md
- principles.md

You MUST also consider:

- the latest implementation
- the fixes applied from 07-Fix-From-Audit.md

---

## Goal

Ensure that:

- all functionality works as expected
- no regressions were introduced
- implementation still aligns with the spec
- the system is stable and production ready

---

## Validation Scope

### 1. Functional Validation

Verify all core workflows:

- Connect-AdoSprintTimer works end-to-end
- Get-AdoCurrentSprint returns correct sprint
- Get-AdoMySprintItems returns assigned items correctly
- Start-AdoTimer creates an active timer
- Stop-AdoTimer logs correct time entries
- Get-AdoToday returns accurate daily summaries
- Get-AdoMonth returns correct aggregation
- Show-AdoStatus reflects real state
- Sync-AdoTime behaves correctly across all modes

---

### 2. Regression Detection

- Identify any previously working functionality that is now broken
- Detect changes in behavior not defined in the spec
- Flag any inconsistencies between expected vs actual results

---

### 3. Data Integrity Validation

Validate:

- config.json structure and persistence
- active-timer.json lifecycle correctness
- worklog-yyyy-MM.json integrity
- no duplicate or corrupted entries
- consistent schema across all entries

---

### 4. Azure DevOps Integration Validation

- REST calls execute successfully
- API endpoints and versions are correct
- PATCH requests are properly formatted
- Missing fields handled safely
- RemainingWork is never reduced below zero
- Sync modes produce expected results
- Idempotency behavior verified (no duplicate sync effects)

---

### 5. Edge Case Testing

Test and validate handling of:

- No current sprint
- No assigned work items
- Starting timer when one is already active
- Stopping timer when none exists
- Corrupt config.json
- Corrupt worklog file
- Missing Azure DevOps fields
- Sprint spanning multiple months
- Partial or failed API responses

---

### 6. PowerShell Compliance

Verify:

- Set-StrictMode is enforced
- CmdletBinding used consistently
- Parameter validation works
- Functions return objects
- No Write-Host used for functional output
- Verbose logging is present and meaningful

---

### 7. Architecture Validation

- Public and private functions remain separated
- Module structure is intact
- No duplicated logic introduced
- Helper functions reused correctly
- No monolithic script regression

---

### 8. Test Suite Validation

- All Pester tests run successfully
- No failing tests
- Test coverage still valid after fixes
- Azure DevOps calls are mocked correctly

---

### 9. Documentation Validation

- README reflects actual behavior
- Examples are accurate and runnable
- Setup instructions still valid
- No outdated information

---

## Output Format

Return a structured regression report:

### 1. Overall Status

- PASS or FAIL
- Brief explanation

### 2. Functional Validation Results

- List each major function with PASS or FAIL

### 3. Regression Issues

- List any regressions found
- Include file/function references

### 4. Data Integrity Issues

- Any storage or schema problems

### 5. Azure DevOps Issues

- Any API or sync related problems

### 6. Edge Case Failures

- List failed edge case scenarios

### 7. Test Failures

- List failing tests or missing coverage

### 8. Documentation Gaps

- List inconsistencies

### 9. Recommended Fixes

- Provide targeted, minimal fixes for each issue

---

## Constraints

- Do not rewrite the codebase
- Do not perform a full audit again
- Focus on validation and regression detection
- Be precise and technical
- Do not skip any validation category

---

## Important

- The spec defines expected behavior
- The implementation must match the spec
- Fixes must not introduce regressions
- This step validates production readiness
