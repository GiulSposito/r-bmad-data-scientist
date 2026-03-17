# Workflow Specification: modeling-pipeline

**Module:** rds
**Status:** Placeholder — To be created via workflow-builder workflow
**Created:** 2026-03-17

---

## Workflow Overview

**Goal:** Execute feature engineering through model evaluation (Phases 5-8) for clean data

**Description:** Assumes data is already clean. Focuses on feature creation, model building, tuning, and rigorous evaluation. Emphasizes cross-validation and proper data budgeting.

**Workflow Type:** Core — Modeling-focused, 4-phase pipeline

---

## Workflow Structure

### Entry Point

```yaml
---
name: modeling-pipeline
description: Feature engineering + modeling + tuning + evaluation
web_bundle: true
installed_path: '{project-root}/_bmad/rds/workflows/modeling-pipeline'
---
```

### Mode

- [x] Multi-step sequential (step-01 through step-04)
- [ ] Tri-modal

---

## Planned Steps

| Step | Name | Goal |
|------|------|------|
| step-01 | Feature Engineering | Transform, encode, create features + recipe |
| step-02 | Baseline Models | Build and compare multiple model types |
| step-03 | Tuning | Hyperparameter optimization (grid/Bayesian) |
| step-04 | Evaluation | Test set evaluation, diagnostics, interpretation |

---

## Workflow Inputs

### Required Inputs

- Clean data (data frame or path)
- Target variable name
- Problem type (classification, regression)

### Optional Inputs

- Model preferences (specific algorithms)
- Tuning strategy (grid, Bayesian, racing)
- Evaluation metrics

---

## Workflow Outputs

### Output Format

- [x] Document-producing
- [x] Non-document

### Output Files

- `recipe.rds` — Preprocessing recipe object
- `trained_models/` — Model objects
- `model_comparison.html` — Model comparison report
- `final_model.rds` — Best tuned model
- `evaluation_report.html` — Test set results, diagnostics
- `interpretation/` — VIP plots, SHAP values, PDPs

---

## Agent Integration

### Primary Agent

**Alan** — Owns and orchestrates this workflow

### Other Agents

- **Grace** — May assist with feature engineering decisions

---

## Implementation Notes

**Use the workflow-builder workflow to build this workflow.**

Key implementation considerations:
- Strict data budgeting (test set touched ONCE)
- All preprocessing in CV folds (honest estimation)
- Compare multiple model types (baseline always included)
- Document all tuning decisions
- Duration estimate: 1-2 weeks
- Ideal for: Clean data ready for modeling

---

_Spec created on 2026-03-17 via BMAD Module workflow (Create Mode)_
