# Post Release Monitoring

Monitor and maintain the AdoSprintTimer PowerShell 7 module after release.

## Source of truth

You MUST use:

- specs/001-ado-sprint-timer/requirements.md
- specs/001-ado-sprint-timer/spec.md
- principles.md

You MUST also consider:

- the latest published version
- GitHub issues and discussions
- user feedback
- any telemetry or usage insights if available

---

## Goal

Ensure the released module:

- remains stable in real-world usage
- has no critical defects
- evolves safely through patches and improvements
- stays aligned with the spec and principles

---

## Monitoring Scope

### 1. Issue Tracking

- Review open GitHub issues
- Categorize each issue:
  - Bug
  - Enhancement
  - Documentation
  - Question

- Identify:
  - high priority bugs
  - recurring problems
  - unclear behavior

---

### 2. Production Feedback Analysis

- Analyze user feedback and patterns
- Identify:
  - common pain points
  - confusing workflows
  - unexpected behaviors

- Flag anything that contradicts expected behavior from the spec

---

### 3. Stability Monitoring

- Detect:
  - runtime errors
  - failing commands
  - broken workflows

- Identify commands most likely to fail:
  - Connect-AdoSprintTimer
  - Start-AdoTimer
  - Stop-AdoTimer
  - Sync-AdoTime

---

### 4. Regression Detection (Post-Release)

- Identify regressions reported by users
- Confirm whether:
  - functionality worked in previous versions
  - behavior changed unexpectedly

---

### 5. Security Monitoring

- Ensure no sensitive data exposure:
  - PAT leaks
  - config file vulnerabilities

- Review:
  - logs
  - configuration handling
  - API usage patterns

---

### 6. Performance Monitoring

- Identify:
  - slow commands
  - excessive API calls
  - inefficient file handling

---

### 7. Spec Alignment

- Ensure the implementation still aligns with:
  - requirements.md
  - spec.md

- Identify drift introduced through fixes or patches

---

## Issue Prioritization

Categorize findings into:

### Critical

- Breaks core functionality
- Security vulnerability
- Data corruption risk

### High

- Major feature malfunction
- Incorrect Azure DevOps sync behavior

### Medium

- Usability issues
- Edge case failures

### Low

- Minor improvements
- Documentation updates

---

## Recommended Actions

For each identified issue:

- Define:
  - root cause
  - affected components
  - severity

- Recommend:
  - fix strategy
  - whether to patch or defer

---

## Patch Strategy

If fixes are required:

- Create a patch plan:
  - which files to modify
  - which tests to update
  - which behaviors to validate

- Recommend version bump:
  - PATCH (bug fix)
  - MINOR (new feature)
  - MAJOR (breaking change)

---

## Output Format

Return a structured monitoring report:

### 1. System Health

- HEALTHY / DEGRADED / CRITICAL
- Brief explanation

### 2. Active Issues Summary

- Total issues
- Breakdown by severity

### 3. Critical Issues

- List with file/function references

### 4. High Priority Issues

- List with impact

### 5. Medium and Low Issues

- Summarized

### 6. Security Findings

- Any risks identified

### 7. Performance Concerns

- Any bottlenecks or inefficiencies

### 8. Spec Drift

- Any deviations from requirements or spec

### 9. Recommended Patch Plan

- Ordered list of fixes
- Version bump recommendation

### 10. Next Actions

- Immediate actions
- Follow-up steps

---

## Constraints

- Do not modify code directly
- Do not re-run full implementation or audit
- Focus on monitoring and actionable insights
- Be precise and technical

---

## Important

- This is an operational phase, not a build phase
- Stability and reliability are the priority
- The spec defines expected behavior
- All changes must remain aligned with the spec
