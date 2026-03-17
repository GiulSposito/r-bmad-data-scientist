# Module Brief: rds

**Date:** 2026-03-17
**Author:** Giu
**Module Code:** rds
**Module Type:** Standalone
**Status:** Ready for Development

---

## Executive Summary

Transformar o ciclo de vida de Data Science em R de processo ad-hoc para framework executável, guiado e production-ready.

**Module Category:** Data Science Lifecycle Management
**Target Users:** Professional Data Scientists, ML Engineers (R/Tidymodels), Data Analysts upskilling to ML, Data Science Teams
**Complexity Level:** Advanced (4 agents, 7 workflows, full 10-phase lifecycle)

---

## Module Identity

### Module Code & Name

- **Code:** `rds`
- **Name:** `R Data Science`
- **Header:** 10-Phase Framework for R Data Science Excellence
- **Subheader:** From raw data to production deployment, guided by best practices

### Core Concept

A comprehensive framework that orchestrates the complete Data Science lifecycle in R (Tidyverse + Tidymodels + Quarto + Vetiver), solving "blank canvas syndrome" by providing executable workflows that guide technical decisions and generate production-ready code.

### Personality Theme

**Computing Pioneers** — Agents named after pioneers of computing and science (Ada Lovelace, Grace Hopper, Alan Turing, Marie Curie). Professional yet inspirational, educational tone that teaches while executing, based on authoritative sources (Max Kuhn, Hadley Wickham, Julia Silge).

---

## Module Type

**Type:** Standalone

**Explanation:** This is an independent module focused on a new domain (R Data Science Lifecycle). It does not extend an existing module and provides self-contained functionality with its own agents, workflows, and configuration. The module can be installed alongside any other BMAD modules and operates independently.

---

## Unique Value Proposition

**What makes this module special:**

For data scientists using R, the module rds provides an executable guided framework that transforms ad-hoc projects into production-ready pipelines, unlike manual workflows because it integrates decades of best practices (Tidyverse, Tidymodels) into specialized agents that teach while executing.

**Why users would choose this module:**

1. **Decisions, Not Just Execution** — Doesn't just say "do feature engineering", but guides WHEN to use each technique based on data characteristics
2. **Workflow Guides Reasoning** — Suggests steps and activities, helping structure thinking
3. **Production-Ready From Start** — Git setup, renv, .gitignore, proper structure automatically
4. **Deep Integration** — 20+ R skills BMAD automatically available and activated contextually
5. **Authority-Based** — Built on wisdom from Max Kuhn, Hadley Wickham, Julia Silge
6. **Pedagogical** — Explains the "why" behind each decision, enabling learning

**Value comparison:**

| Feature | Manual Workflow | rds |
|---------|----------------|-----|
| Setup time | 2-4 hours | 15 minutes |
| Guided decisions | No | Yes (tables, decision trees) |
| Production-ready | Refactoring needed | From the beginning |
| Reproducible | Depends on scientist | Always (renv, Git, Quarto) |
| Standardization | Each person different | Consistent workflow |
| Learning | Trial & error | Guided + explanations |

---

## User Scenarios

### Target Users

**Primary Users:**

1. **Professional Data Scientists** — Work with R, want speed + quality. Framework that guides complex decisions without getting in the way. Saves 40-60% of setup/boilerplate time.

2. **ML Engineers** — Know R/Tidymodels (intermediate-advanced), learning Python (basic). Need robust framework for complex R projects. Accelerates development while maintaining quality.

3. **Data Analysts Upskilling to ML** — Know basic R (dplyr, ggplot2), want to learn ML. Need structured framework that teaches concepts. Clear path from analyst → data scientist.

4. **Data Science Teams** — Multiple scientists needing standardization. Consistent workflows, easier code reviews. Uniform quality, faster onboarding.

**Personas:**

- **Ana** (Senior DS, 5+ years) — Wants speed without sacrificing quality. Pain: repetitive setup
- **João** (ML Engineer, R/Tidymodels expert) — Wants framework for productivity. Pain: repeating technical decisions
- **Maria** (Analyst, 2 years) — Wants to learn ML. Pain: "where to start?"

### Primary Use Case

Data scientists need to execute the full data science lifecycle (raw data → deployed model) following best practices, but face the "blank canvas syndrome" — repeating the same setup, making ad-hoc decisions, producing non-reproducible code, and struggling to standardize across teams.

### User Journey

**Scenario 1: Quick Prototype (4-8 hours)**

Ana (Senior DS) receives churn data on Monday, needs prototype by Friday.

1. Invokes Ada → `[SP]` Setup Project (15 min: structure, renv, Git)
2. Ada → `[II]` Import & Inspect (identifies 15% missings automatically)
3. Ada → `[CD]` Clean Data (applies cleaning with guided decisions)
4. Grace → `[QE]` Quick EDA (generates visual insights automatically)
5. Grace discovers: "Customers with >3 support calls have 5x more churn!"
6. Alan → `[MP]` Modeling Pipeline (tests 3 models, tunes best: XGBoost 87% accuracy)
7. Marie → `[BD]` Build Dashboard (presentation-ready dashboard with KPIs)

**Result:** 6.5 hours later, production-ready prototype with 87% accuracy, documented, reproducible.

**Scenario 2: Full Production Pipeline (2-3 weeks)**

João (ML Engineer) needs strategic demand forecasting in production.

- Week 1: Ada guides deep setup, Grace analyzes seasonality (30-page insights), creates 47 features
- Week 2: Alan tests 4 models with time series CV, Bayesian optimization (50 iterations)
- Week 3: Alan evaluates with walk-forward validation, Marie creates technical report (30 pages) + executive summary (2 pages), deploys via Vetiver API with Docker + monitoring

**Result:** Production-deployed model, documented, monitored, approved by technical and business teams.

**Scenario 3: EDA Exploration (3-6 hours)**

Maria (Analyst) explores sales data from 5 stores (100k transactions).

1. Invokes Grace, who coordinates with Ada for quick setup (5 min)
2. Grace → `[ED]` Run EDA (complete exploratory analysis)
3. Grace discovers: Store 3 has 2x weekend sales, Electronics 3x higher ticket, December peak confirmed
4. Marie generates beautiful HTML report: `eda-sales-exploration.html`

**Result:** 3 hours, actionable insights, documented. Maria learns structured EDA workflow.

**The "Aha!" moment:** "So THIS is how structured workflows work!"

---

## Agent Architecture

### Agent Count Strategy

**Multi-Agent Module (4 Specialized Agents)**

**Justification:**
- Broad domain (10 phases of DS lifecycle)
- Distinct expertise areas (setup vs EDA vs modeling vs deployment)
- Users expect the "right expert" for each phase
- Natural handoffs between phases

### Agent Roster

| Agent | Name | Role | Expertise |
|-------|------|------|-----------|
| Ada | The Project Architect | Foundation Specialist (Phases 1-3) | Setup, data import, cleaning, reproducibility |
| Grace | The Data Scientist | Exploration & Feature Specialist (Phases 4-5) | EDA, visualization, feature engineering |
| Alan | The ML Engineer | Modeling & Optimization Specialist (Phases 6-8) | Model building, tuning, evaluation, metrics |
| Marie | The Communicator | Communication & Deployment Specialist (Phases 9-10) | Reports, dashboards, deployment, monitoring |

### Agent Interaction Model

**Sequential Handoffs with Clear Boundaries:**

- Ada → Grace: "Clean data ready for EDA"
- Grace → Alan: "Features created, recipe ready"
- Alan → Marie: "Model evaluated, performance documented"
- Marie → Deploy: "Report/dashboard/API ready"

**Shared Commands (all agents):**
- `[WS]` Workflow Status — Show status of running workflows
- `[DA]` Dismiss Agent — Exit agent

**No Overlap:** Each command has a single owner agent.

**Sidecar Memory:** All 4 agents have sidecar memory to remember project context, decisions made, and artifacts created across sessions.

### Agent Communication Style

**Ada** 🏗️ (Ada Lovelace):
- Organized, methodical, structured
- "Everything has its place"
- Clear step-by-step, uses checklists
- Validates before proceeding
- Catchphrase: "Structure enables creativity"

**Grace** 🔬 (Grace Hopper):
- Curious, visual, explorative
- "Let the data tell the story"
- Visual-first (plots before tables)
- Interprets findings, suggests hypotheses
- Catchphrase: "Let the data speak"

**Alan** 🤖 (Alan Turing):
- Pragmatic, performance-focused, metric-driven
- "Numbers don't lie"
- Data-driven, shows metrics always
- Warns about data leakage, overfitting
- Catchphrase: "Trust metrics, not intuition"

**Marie** 📊 (Marie Curie):
- Clear, business-oriented, storyteller
- "Insights without action are worthless"
- Executive summary first
- Visual storytelling, actionable recommendations
- Catchphrase: "Science without communication is incomplete"

---

## Workflow Ecosystem

### Core Workflows (Essential)

**1. full-lifecycle/**
- **Purpose:** Complete 10-phase workflow from project zero to deployment
- **Duration:** 2-4 weeks (complete project)
- **Steps:** 10 (step-01-setup.md through step-10-deploy.md)
- **Owner:** Ada (orchestrates)
- **When:** New project, production-ready needed
- **Flow:** Raw data → 10 guided phases → Deployed model + docs

**2. quick-eda/**
- **Purpose:** Streamlined Setup + Import + Clean + EDA (Phases 1-4)
- **Duration:** 4-8 hours
- **Steps:** 4 (streamlined)
- **Owner:** Grace
- **When:** Quick data exploration, prototyping
- **Flow:** New dataset → Fast exploration → EDA report + insights

**3. modeling-pipeline/**
- **Purpose:** Feature Engineering + Modeling + Tuning + Evaluation (Phases 5-8)
- **Duration:** 1-2 weeks
- **Steps:** 4
- **Owner:** Alan
- **When:** Data already clean, focus on model optimization
- **Flow:** Clean data → Model optimization → Tuned model + metrics

**4. prototype-to-production/**
- **Purpose:** Modeling + Communication + Deploy (Phases 6-10)
- **Duration:** 1-2 weeks
- **Steps:** 5
- **Owner:** Marie (with handoff from Alan)
- **When:** Features ready, need to take to production
- **Flow:** Features ready → Full deploy pipeline → API + monitoring + docs

### Feature Workflows (Specialized)

**5. data-quality-check/**
- **Purpose:** Deep dive into data quality (Phase 3 expanded)
- **Duration:** 4-8 hours
- **Owner:** Ada
- **When:** Suspicious data, many missings, outliers
- **Flow:** Suspicious data → Deep validation → Quality report + fixes

**6. hyperparameter-optimization/**
- **Purpose:** Deep dive into tuning (Phase 7 expanded)
- **Duration:** 1-3 days
- **Owner:** Alan
- **When:** Critical performance, need maximum squeeze
- **Flow:** Base model → Advanced tuning (Bayesian, racing) → Optimized model

**7. model-interpretation/**
- **Purpose:** Deep dive into interpretability (Phase 8 expanded)
- **Duration:** 1-2 days
- **Owner:** Alan
- **When:** Model needs to be explainable (regulation, stakeholders)
- **Flow:** Trained model → Interpretation analysis → SHAP/VIP/PDP reports

### Utility Workflows (Support)

None defined — core and specialized workflows cover needs.

---

## Tools & Integrations

### MCP Tools

**None** — Module does not require custom MCP tools.

### External Services

**R Package Ecosystem** (referenced in workflows, not installed by module):

- **Core:** tidyverse, tidymodels
- **Feature Engineering:** recipes, embed, themis
- **Modeling:** parsnip, ranger, xgboost, glmnet
- **Evaluation:** tune, yardstick, workflows, vip, probably
- **Visualization:** ggplot2, patchwork, ggrepel
- **Communication:** quarto, gt, DT
- **Deploy:** vetiver, pins
- **Infrastructure:** renv, usethis

**Note:** Workflows reference/suggest these packages for use in R projects. They are not installed by the BMAD module itself.

### Integrations with Other Modules

**BMAD Core:** Uses BMAD Core configuration system and follows agent/workflow architecture patterns.

**R Skills BMAD (20+ skills):** Deep integration with automatic activation:
- Workflows mention keywords that trigger skills contextually
- Examples: "tidymodels" → `r-tidymodels` skill, "ggplot2" → `ggplot2` skill
- No custom MCP needed — R skills provide all necessary knowledge

**No dependencies on other specific modules** — operates as standalone.

---

## Creative Features

### Personality & Theming

**Theme:** Computing Pioneers

Agents named after pioneers of computing/science, creating educational and inspirational atmosphere:

**Agent Catchphrases:**
- Ada 🏗️: "Structure enables creativity"
- Grace 🔬: "Let the data speak"
- Alan 🤖: "Trust metrics, not intuition"
- Marie 📊: "Science without communication is incomplete"

**Style:** Professional yet accessible, methodical, evidence-based, pedagogical.

**Agent Quirks:**
- **Ada:** Uses building metaphors ("laying foundation", "scaffolding"), validates obsessively
- **Grace:** Shows excitement with ASCII plots, loves discovering unexpected correlations
- **Alan:** Warns aggressively about data leakage, always shows metrics in tables
- **Marie:** Always asks "How would you explain this to your CEO?", focuses on visual storytelling

### Easter Eggs & Delighters

**Achievement System** 🏆

Unlocked upon completing milestones:
- 🏆 "First Steps" — Completed first setup
- 🏆 "Data Detective" — Found 5+ insights in EDA
- 🏆 "Feature Wizard" — Created 20+ features
- 🏆 "Model Master" — Model with >90% accuracy
- 🏆 "Production Pro" — First successful deployment
- 🏆 "Lifecycle Legend" — Completed full-lifecycle workflow

**Quote Database** 💬

Displays random inspirational quotes from data science authorities:
- John Tukey: "The best thing about being a statistician is that you get to play in everyone's backyard."
- Hadley Wickham: "Make your code readable. Spend time on names."
- Andrew Ng: "Feature engineering is the key. Models are commodities."
- Max Kuhn: "Applied statistics is about reducing uncertainty."

**ASCII Art** 🎨

Displayed when model achieves >90% accuracy:
```
    ⭐ OUTSTANDING MODEL ⭐

     📈 Accuracy: 92.5%

    ╔══════════════════╗
    ║   GREAT WORK!    ║
    ╚══════════════════╝
```

**Hidden Commands** 🕵️
- `[XX]` Show Achievement Progress
- `[QQ]` Random Quote
- `[EE]` Easter Egg Hunt (shows list of easter eggs)

**Workflow Celebrations** 🎉

On completing full-lifecycle:
```
🎉 CONGRATULATIONS! 🎉

You just completed the entire Data Science Lifecycle!

From raw data to production deployment, you followed
best practices every step of the way.

📊 Summary:
   - Setup: ✅
   - Data Quality: ✅
   - EDA Insights: ✅
   - Features Created: ✅
   - Model Performance: ✅
   - Report Generated: ✅
   - Production Deployed: ✅

🏆 Achievement Unlocked: "Lifecycle Legend"

"The journey of a thousand models begins with a single seed."
- Ancient Data Science Proverb
```

### Module Lore

**Origin Story: "The Four Guardians"**

> "In 2024, four legendary data scientists—frustrated by repeating the same workflows in every project—decided to encode their collective wisdom into an executable framework. They systematized the best practices from decades of R evolution: from S-PLUS to modern Tidyverse, from ad-hoc modeling to rigorous Tidymodels. The result? A framework where data science is not trial-and-error, but guided discovery."

**The Guardians:**
- **Ada Lovelace** 🏗️ — Guardian of Structure (Setup, Foundation)
- **Grace Hopper** 🔬 — Guardian of Discovery (EDA, Features)
- **Alan Turing** 🤖 — Guardian of Intelligence (Modeling, Optimization)
- **Marie Curie** 📊 — Guardian of Communication (Reports, Deploy)

---

## Next Steps

1. **Review this brief** — Ensure the vision is clear and complete
2. **Run module workflow (Create mode)** — Build the module structure: `_bmad/rds/`
3. **Create agents** — Use agent-builder workflow for Ada, Grace, Alan, Marie
4. **Create workflows** — Use workflow-builder workflow for each of the 7 workflows
5. **Implement templates & data files** — Create project templates, decision trees, checklists
6. **Test module** — Install and verify functionality with test scenarios
7. **Iterate and refine** — Adjust based on usage feedback

---

_Brief created on 2026-03-17 by Giu using the BMAD Module workflow (Brief Mode)_
