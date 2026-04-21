# Auto Improve System

Continuously improve the AdoSprintTimer development system by analyzing past implementation cycles, audit results, regression reports, and post-release monitoring data.

## Source of truth

You MUST use:

- specs/001-ado-sprint-timer/requirements.md
- specs/001-ado-sprint-timer/spec.md
- specs/001-ado-sprint-timer/plan.md
- specs/001-ado-sprint-timer/tasks.md
- principles.md

You MUST also analyze outputs from:

- 05-Implement-Tasks.md
- 06-Audit-Implementation.md
- 07-Fix-From-Audit.md
- 08-Regression-Test.md
- 09-Release-Readiness.md
- 10-Publish-Module.md
- 11-Post-Release-Monitoring.md

---

## Goal

Improve the system itself by:

- identifying recurring failures
- detecting weak spots in prompts
- strengthening spec definitions
- refining task generation
- improving implementation reliability
- reducing future defects and drift

---

## Analysis Scope

### 1. Failure Pattern Detection

Identify patterns across cycles:

- repeated audit failures
- recurring regression issues
- repeated post-release bugs
- common implementation mistakes

Group findings into categories:

- architecture issues
- task ambiguity
- missing requirements
- weak validation
- test gaps

---

### 2. Prompt Effectiveness Review

Evaluate prompts:

- 01 through 11 prompt files

Identify:

- unclear instructions
- missing constraints
- redundancy
- steps that produce inconsistent output

Flag prompts that:

- lead to drift
- allow shortcuts
- produce inconsistent implementations

---

### 3. Spec Quality Review

Evaluate:

- requirements.md
- spec.md

Identify:

- missing edge cases
- ambiguous definitions
- incomplete workflows
- weak constraints

---

### 4. Task Generation Review

Evaluate tasks.md:

- Are tasks granular enough?
- Are tasks enforceable?
- Are tasks being skipped or misinterpreted?
- Are dependencies between tasks clear?

---

### 5. Testing Effectiveness

Evaluate:

- test coverage gaps
- missed edge cases
- weak assertions
- missing negative tests

---

### 6. Architecture Drift Analysis

Identify:

- where implementation diverged from spec
- why drift occurred
- whether drift was caused by:
  - poor spec clarity
  - weak prompts
  - missing constraints

---

## Improvement Actions

### 1. Prompt Improvements

For each prompt (00–11):

- recommend specific changes
- add missing constraints
- remove ambiguity
- improve determinism

---

### 2. Spec Improvements

Recommend updates to:

- requirements.md
- spec.md

Include:

- clearer definitions
- additional constraints
- edge case coverage

---

### 3. Task Improvements

Recommend updates to:

- tasks.md

Include:

- better task breakdown
- improved ordering
- explicit validation steps

---

### 4. Testing Improvements

Recommend:

- new tests to add
- edge cases to cover
- stronger validation patterns

---

### 5. System Enhancements

Suggest improvements such as:

- additional pipeline steps
- better validation checkpoints
- automation opportunities
- performance optimizations

---

## Output Format

Return a structured system improvement report:

### 1. Overall System Health

- Rating: STRONG / MODERATE / WEAK
- Summary explanation

### 2. Recurring Failure Patterns

- Categorized list

### 3. Prompt Weaknesses

- List of prompts with issues
- Specific problems identified

### 4. Spec Gaps

- Missing or unclear areas

### 5. Task Issues

- Weak or ambiguous tasks

### 6. Testing Gaps

- Missing coverage areas

### 7. Architecture Drift Causes

- Root cause analysis

### 8. Recommended Improvements

#### Prompt Updates

- Specific changes by prompt file

#### Spec Updates

- Required improvements

#### Task Updates

- Task restructuring suggestions

#### Testing Updates

- New or improved tests

---

### 9. Priority Actions

- Ordered list of highest impact improvements

---

## Constraints

- Do not modify code directly
- Do not perform implementation
- Focus on system-level improvements
- Be precise and technical
- Avoid generic advice

---

## Important

- The goal is to improve the system, not the current build
- Every recommendation must reduce future failure risk
- Prioritize determinism, clarity, and repeatability
