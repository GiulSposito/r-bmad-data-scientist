# Workflow Specification: quick-eda

**Module:** rds
**Status:** Placeholder — To be created via workflow-builder workflow
**Created:** 2026-03-17

---

## Workflow Overview

**Goal:** Rapidly explore new datasets with streamlined setup, import, cleaning, and EDA (Phases 1-4)

**Description:** Fast-track workflow for data exploration and prototyping. Skips some validation steps of full-lifecycle for speed, but maintains reproducibility.

**Workflow Type:** Core — Streamlined, 4-phase exploration

---

## Workflow Structure

### Entry Point

```yaml
---
name: quick-eda
description: Streamlined setup + import + clean + EDA for rapid exploration
web_bundle: true
installed_path: '{project-root}/_bmad/rds/workflows/quick-eda'
---
```

### Mode

- [x] Multi-step sequential (step-01 through step-04)
- [ ] Tri-modal

---

## Planned Steps

| Step | Name | Goal |
|------|------|------|
| step-01 | Quick Setup | Minimal project structure |
| step-02 | Import | Load data quickly |
| step-03 | Quick Clean | Fast cleaning (automated decisions) |
| step-04 | EDA | Generate comprehensive EDA report |

---

## Workflow Inputs

### Required Inputs

- Data source (file path)

### Optional Inputs

- Project name
- Output format (HTML, PDF)

---

## Workflow Outputs

### Output Format

- [x] Document-producing
- [ ] Non-document

### Output Files

- `eda-report.html` — Comprehensive EDA report with visualizations
- `/plots/` — Individual EDA plots

---

## Agent Integration

### Primary Agent

**Grace** — Owns and orchestrates this workflow, coordinates with Ada for setup

### Other Agents

- **Ada** — Quick setup assistance (Phase 1-2)

---

## Implementation Notes

**Use the workflow-builder workflow to build this workflow.**

Key implementation considerations:
- Trade validation depth for speed
- Automate more decisions (imputation strategies, transformation choices)
- Generate rich HTML report at end (Quarto)
- Duration estimate: 4-8 hours
- Ideal for: New datasets, prototyping, exploratory projects

---

_Spec created on 2026-03-17 via BMAD Module workflow (Create Mode)_
