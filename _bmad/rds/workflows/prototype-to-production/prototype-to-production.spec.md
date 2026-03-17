# Workflow Specification: prototype-to-production

**Module:** rds
**Status:** Placeholder — To be created via workflow-builder workflow
**Created:** 2026-03-17

---

## Workflow Overview

**Goal:** Take features/recipe through modeling, communication, and deployment (Phases 6-10)

**Description:** Assumes features are ready. Focuses on model development, documentation, and production deployment with monitoring.

**Workflow Type:** Core — Production-focused, 5-phase deployment pipeline

---

## Workflow Structure

### Entry Point

```yaml
---
name: prototype-to-production
description: Modeling + communication + deploy for production
web_bundle: true
installed_path: '{project-root}/_bmad/rds/workflows/prototype-to-production'
---
```

### Mode

- [x] Multi-step sequential (step-01 through step-05)
- [ ] Tri-modal

---

## Planned Steps

| Step | Name | Goal |
|------|------|------|
| step-01 | Build Model | Create and compare models |
| step-02 | Tune | Optimize hyperparameters |
| step-03 | Evaluate | Test set + interpretation |
| step-04 | Communicate | Reports + dashboards |
| step-05 | Deploy | Vetiver API + monitoring setup |

---

## Workflow Inputs

### Required Inputs

- Features ready (recipe or processed data)
- Target variable
- Problem type

### Optional Inputs

- Deployment target (Posit Connect, Docker, local)
- Monitoring preferences

---

## Workflow Outputs

### Output Format

- [x] Document-producing
- [x] Non-document

### Output Files

- `final_model.rds` — Production model
- `technical_report.qmd/.html` — Technical documentation
- `executive_summary.qmd/.html` — Business summary
- `dashboard.qmd/.html` — Interactive dashboard
- `model_api/` — Vetiver API files
- `monitoring_setup.md` — Monitoring configuration

---

## Agent Integration

### Primary Agent

**Marie** — Owns and orchestrates this workflow, with handoff from Alan

### Other Agents

- **Alan** — Phases 6-8 (modeling through evaluation)
- **Marie** — Phases 9-10 (communication and deployment)

---

## Implementation Notes

**Use the workflow-builder workflow to build this workflow.**

Key implementation considerations:
- Handoff between Alan (technical) and Marie (communication/deploy)
- Generate both technical and executive documentation
- Vetiver for model versioning and API
- Monitoring setup included (not just deployment)
- Duration estimate: 1-2 weeks
- Ideal for: Taking validated models to production

---

_Spec created on 2026-03-17 via BMAD Module workflow (Create Mode)_
