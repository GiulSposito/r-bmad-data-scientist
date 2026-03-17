# Workflow Specification: data-quality-check

**Module:** rds
**Status:** Placeholder — To be created via workflow-builder workflow
**Created:** 2026-03-17

---

## Workflow Overview

**Goal:** Deep dive into data quality analysis (expanded Phase 3)

**Description:** Comprehensive data quality assessment for suspicious data, high missings, or critical projects. Goes beyond standard cleaning with systematic validation.

**Workflow Type:** Specialized — Quality assurance

---

## Workflow Structure

### Entry Point

```yaml
---
name: data-quality-check
description: Deep dive data quality validation and remediation
web_bundle: true
installed_path: '{project-root}/_bmad/rds/workflows/data-quality-check'
---
```

### Mode

- [x] Multi-step sequential (step-01 through step-04)
- [ ] Tri-modal

---

## Planned Steps

| Step | Name | Goal |
|------|------|------|
| step-01 | Missing Analysis | Pattern detection (MCAR, MAR, MNAR) |
| step-02 | Outlier Detection | Systematic outlier identification |
| step-03 | Consistency Checks | Cross-variable validation, domain rules |
| step-04 | Remediation | Fix issues, document decisions |

---

## Workflow Inputs

### Required Inputs

- Data (raw or partially cleaned)

### Optional Inputs

- Domain-specific validation rules
- Acceptable missing thresholds

---

## Workflow Outputs

### Output Format

- [x] Document-producing
- [ ] Non-document

### Output Files

- `data_quality_report.html` — Comprehensive quality assessment
- `missing_analysis.html` — Missing data patterns
- `outlier_report.html` — Outlier detection results
- `remediation_log.md` — Documentation of fixes applied

---

## Agent Integration

### Primary Agent

**Ada** — Owns this specialized workflow

### Other Agents

- None (Ada-only workflow)

---

## Implementation Notes

**Use the workflow-builder workflow to build this workflow.**

Key implementation considerations:
- Use naniar, visdat for missing analysis
- Multiple outlier detection methods (IQR, isolation forest, domain rules)
- Document every remediation decision
- Generate comprehensive quality report
- Duration estimate: 4-8 hours
- Ideal for: Suspicious data, critical projects, high stakes

---

_Spec created on 2026-03-17 via BMAD Module workflow (Create Mode)_
