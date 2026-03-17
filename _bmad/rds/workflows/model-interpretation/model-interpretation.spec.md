# Workflow Specification: model-interpretation

**Module:** rds
**Status:** Placeholder — To be created via workflow-builder workflow
**Created:** 2026-03-17

---

## Workflow Overview

**Goal:** Deep dive model interpretability (expanded Phase 8)

**Description:** Comprehensive model interpretation for regulated industries or stakeholder requirements. Uses SHAP, LIME, VIP, PDPs, and other explainability methods.

**Workflow Type:** Specialized — Interpretability/explainability

---

## Workflow Structure

### Entry Point

```yaml
---
name: model-interpretation
description: Deep model interpretation with SHAP, VIP, PDPs
web_bundle: true
installed_path: '{project-root}/_bmad/rds/workflows/model-interpretation'
---
```

### Mode

- [x] Multi-step sequential (step-01 through step-04)
- [ ] Tri-modal

---

## Planned Steps

| Step | Name | Goal |
|------|------|------|
| step-01 | Global Interpretation | Overall model behavior (VIP, PDPs) |
| step-02 | Local Interpretation | Individual prediction explanations (SHAP, LIME) |
| step-03 | Feature Importance | Permutation importance, SHAP values |
| step-04 | Documentation | Generate interpretation report |

---

## Workflow Inputs

### Required Inputs

- Trained model
- Test/validation data
- Feature names

### Optional Inputs

- Specific predictions to explain
- Interpretation method preferences

---

## Workflow Outputs

### Output Format

- [x] Document-producing
- [ ] Non-document

### Output Files

- `interpretation_report.html` — Comprehensive interpretation
- `global_interpretation/` — VIP plots, PDPs, ICE plots
- `local_interpretation/` — SHAP values, LIME explanations
- `feature_importance.csv` — Permutation importance results

---

## Agent Integration

### Primary Agent

**Alan** — Owns this specialized workflow

### Other Agents

- **Marie** — May assist with communication of interpretation results

---

## Implementation Notes

**Use the workflow-builder workflow to build this workflow.**

Key implementation considerations:
- Use vip, DALEX, iml, SHAPforxgboost packages
- Generate both global and local explanations
- Visual emphasis (plots are more interpretable)
- Audience-appropriate language (technical vs business)
- Duration estimate: 1-2 days
- Ideal for: Regulated industries, stakeholder requirements, model trust

---

_Spec created on 2026-03-17 via BMAD Module workflow (Create Mode)_
