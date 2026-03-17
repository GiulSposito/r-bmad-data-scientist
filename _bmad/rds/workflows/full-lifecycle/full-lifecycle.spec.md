# Workflow Specification: full-lifecycle

**Module:** rds
**Status:** Placeholder — To be created via workflow-builder workflow
**Created:** 2026-03-17

---

## Workflow Overview

**Goal:** Guide users through the complete 10-phase Data Science lifecycle from raw data to production deployment

**Description:** Comprehensive workflow that orchestrates all phases of a data science project following best practices (Tidyverse + Tidymodels). Each phase validates before proceeding to the next.

**Workflow Type:** Core — Sequential, 10-phase lifecycle

---

## Workflow Structure

### Entry Point

```yaml
---
name: full-lifecycle
description: Complete 10-phase DS lifecycle from setup to deployment
web_bundle: true
installed_path: '{project-root}/_bmad/rds/workflows/full-lifecycle'
---
```

### Mode

- [x] Multi-step sequential (step-01 through step-10)
- [ ] Tri-modal

---

## Planned Steps

| Step | Name | Goal |
|------|------|------|
| step-01 | Setup Project | Create structure, renv, Git |
| step-02 | Import & Inspect | Load data, glimpse, skim, identify issues |
| step-03 | Clean Data | Wrangling, missings, outliers |
| step-04 | EDA | Explore distributions, relationships, patterns |
| step-05 | Feature Engineering | Transform, encode, create features |
| step-06 | Modeling | Build baseline + multiple models |
| step-07 | Tuning | Hyperparameter optimization |
| step-08 | Evaluation | Test set, diagnostics, interpretation |
| step-09 | Communication | Generate reports/dashboards |
| step-10 | Deploy | Vetiver API, monitoring |

---

## Workflow Inputs

### Required Inputs

- Project name (optional, defaults to directory name)
- Data source (file path or connection)

### Optional Inputs

- Specific modeling preferences
- Deployment target (local, cloud, Connect)

---

## Workflow Outputs

### Output Format

- [x] Document-producing (multiple artifacts)
- [x] Non-document (code, models)

### Output Files

- `/project-name/` — Complete project structure
- `.Rproj` — R project file
- `renv.lock` — Dependency lock file
- `/data/raw/` — Raw data
- `/data/processed/` — Clean data
- `/scripts/` — R scripts for each phase
- `/outputs/` — EDA plots, model artifacts
- `/reports/` — Quarto reports/dashboards
- `/models/` — Trained models (vetiver pins)

---

## Agent Integration

### Primary Agent

**Ada** — Orchestrates the complete workflow, coordinates handoffs between phases

### Other Agents

- **Grace** — Phases 4-5 (EDA, Feature Engineering)
- **Alan** — Phases 6-8 (Modeling, Tuning, Evaluation)
- **Marie** — Phases 9-10 (Communication, Deployment)

---

## Implementation Notes

**Use the workflow-builder workflow to build this workflow.**

Key implementation considerations:
- Each phase should validate completion before proceeding
- Save artifacts at each phase for reproducibility
- Use checkpoints to allow resume if interrupted
- Integrate with r-datascience, r-tidymodels, quarto skills
- Duration estimate: 2-4 weeks for complete project

**Orchestration Pattern**: Ada coordinates, invokes other agents at appropriate phases

---

_Spec created on 2026-03-17 via BMAD Module workflow (Create Mode)_
