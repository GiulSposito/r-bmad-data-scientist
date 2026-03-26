# R Data Science

10-Phase Framework for R Data Science Excellence

From raw data to production deployment, guided by best practices

---

## Overview

A comprehensive framework that orchestrates the complete Data Science lifecycle in R (Tidyverse + Tidymodels + Quarto + Vetiver), solving "blank canvas syndrome" by providing executable workflows that guide technical decisions and generate production-ready code.

**For data scientists using R**, the module rds provides an executable guided framework that transforms ad-hoc projects into production-ready pipelines, unlike manual workflows because it integrates decades of best practices (Tidyverse, Tidymodels) into specialized agents that teach while executing.

---

## Installation

```bash
bmad install rds
```

---

## Quick Start

After installation, invoke the module's agents to get started:

1. **Ada** (Project Architect) — Setup, Import, Data Cleaning — Phases 1-3
   - `/bmad:rds:agents:ada` or trigger from bmad-master menu

2. **Grace** (Data Scientist) — EDA, Feature Engineering — Phases 4-5
   - `/bmad:rds:agents:grace` or trigger from bmad-master menu

3. **Alan** (ML Engineer) — Modeling, Tuning, Evaluation — Phases 6-8
   - `/bmad:rds:agents:alan` or trigger from bmad-master menu

4. **Marie** (The Reporter) — Reports, Dashboards, Presentations — Phase 9
   - `/bmad:rds:agents:marie` or trigger from bmad-master menu

5. **Tim** (The Deployer) — Production Deployment, Monitoring — Phase 10
   - `/bmad:rds:agents:tim` or trigger from bmad-master menu

**For detailed documentation, see [docs/](docs/).**

---

## Components

### Agents

1. **Ada** (Project Architect) — "Structure enables creativity"
   - Icon: 🏗️
   - Phases: 1-3 (Setup, Import, Cleaning)
   - Menu: [SP], [II], [CD], [FL], [DQ], [WS], [DA]

2. **Grace** (Data Scientist) — "Let the data speak"
   - Icon: 🔬
   - Phases: 4-5 (EDA, Feature Engineering)
   - Menu: [ED], [FE], [QE], [DT], [WS], [DA]

3. **Alan** (ML Engineer) — "Trust metrics, not intuition"
   - Icon: 🤖
   - Phases: 6-8 (Modeling, Tuning, Evaluation)
   - Menu: [BM], [TM], [EM], [MP], [HO], [MI], [MS], [WS], [DA]

4. **Marie** (The Reporter) — "Science without communication is incomplete"
   - Icon: 📊
   - Phase: 9 (Communication & Reporting)
   - Menu: [TR], [ER], [BD], [PG], [DS], [WS], [PM], [DA]

5. **Tim** (The Deployer) — "A model in production worth 10 in notebooks"
   - Icon: 🚀
   - Phase: 10 (Deployment & Monitoring)
   - Menu: [DM], [MM], [PP], [PG], [VC], [DH], [WS], [PM], [DA]

### Workflows

**Complete Lifecycle:**
1. **full-lifecycle** — Complete 10-phase DS lifecycle (2-4 weeks)
   - Orchestrated by Ada → Grace → Alan → Marie → Tim

**Phase-Specific Workflows:**

**Ada (Phases 1-3):**
2. **data-quality-check** — Deep data quality analysis (4-8 hours)

**Grace (Phases 4-5):**
3. **quick-eda** — Streamlined exploration (4-8 hours)

**Alan (Phases 6-8):**
4. **modeling-pipeline** — Feature engineering → evaluation (1-2 weeks)
5. **hyperparameter-optimization** — Advanced tuning (1-3 days)
6. **model-interpretation** — Deep interpretability (1-2 days)

**Marie (Phase 9 - Communication):**
7. **technical-report** — Comprehensive Quarto report (1-2 days)
8. **executive-report** — Executive summary (4-6 hours)
9. **build-dashboard** — Interactive Shiny dashboard (1-3 days)
10. **presentation-generation** — Quarto reveal.js slides (4-8 hours)

**Tim (Phase 10 - Deployment):**
11. **prototype-to-production** — Complete deployment workflow (1-2 weeks)
12. **deploy-model** — Vetiver API deployment (1-2 days)
13. **model-monitoring** — Monitoring and alerting setup (1-2 days)

---

## Configuration

The module uses standard BMAD configuration variables (set during installation or in `_bmad/core/config.yaml`):

- `{user_name}` — Your name for personalized communication
- `{communication_language}` — Primary language (default: Portuguese)
- `{output_folder}` — Where generated artifacts are saved
- `{project-root}` — Repository root

---

## Module Structure

```
rds/
├── config.yaml
├── README.md
├── TODO.md
├── docs/
│   ├── getting-started.md
│   ├── agents.md
│   ├── workflows.md
│   └── examples.md
├── agents/
│   ├── ada.spec.md
│   ├── grace.spec.md
│   ├── alan.spec.md
│   └── marie.spec.md
└── workflows/
    ├── full-lifecycle/
    ├── quick-eda/
    ├── modeling-pipeline/
    ├── prototype-to-production/
    ├── data-quality-check/
    ├── hyperparameter-optimization/
    └── model-interpretation/
```

---

## Documentation

For detailed user guides and documentation, see the **[docs/](docs/)** folder:
- [Getting Started](docs/getting-started.md)
- [Agents Reference](docs/agents.md)
- [Workflows Reference](docs/workflows.md)
- [Examples](docs/examples.md)

---

## Development Status

This module is **COMPLETE** and ready for use:

- [x] **Agents:** 5 agents (Ada, Grace, Alan, Marie, Tim)
- [x] **Workflows:** 13 workflows covering complete DS lifecycle
- [x] **Documentation:** Comprehensive agent specs and workflow guides
- [x] **BMAD Version:** Compatible with 6.2.2+

See CHANGELOG.md for version history.

---

## Author

Created via BMAD Module workflow (2026-03-17)

---

## License

Part of the BMAD framework.
