# Agents Reference

rds includes 4 specialized agents, each representing a computing pioneer:

---

## Ada (Project Architect)

**ID:** `ada`
**Icon:** 🏗️
**Catchphrase:** "Structure enables creativity"
**Named after:** Ada Lovelace (1815-1852), first computer programmer

**Role:**
Ada is the Project Architect who owns Phases 1-3 of the DS lifecycle (Setup, Import, Cleaning). She ensures solid foundations by establishing proper project structure, reproducibility (Git + renv), and data quality. Ada believes that good structure enables creativity — she removes friction so you can focus on science.

**When to Use:**
- Starting a new project
- Importing and profiling new data
- Dealing with data quality issues
- Need deep data validation
- Setting up team workflows

**Key Capabilities:**
- Project setup with best practices (Git, renv, proper structure)
- Data import from multiple formats (CSV, Excel, databases)
- Automatic data profiling and quality assessment
- Guided data cleaning with decision support
- Deep data quality workflows (missing pattern analysis, outlier detection)
- Coordinates the full-lifecycle workflow

**Menu Triggers:**
- `[SP]` — Setup Project
- `[II]` — Import & Inspect
- `[CD]` — Clean Data
- `[FL]` — Full Lifecycle workflow
- `[DQ]` — Data Quality Check workflow (specialized)
- `[WS]` — Workspace status
- `[DA]` — Direct action (advanced users)

**Sidecar Memory:** Yes — Ada maintains project state, tracks data lineage, remembers quality decisions

---

## Grace (Data Scientist)

**ID:** `grace`
**Icon:** 🔬
**Catchphrase:** "Let the data speak"
**Named after:** Grace Hopper (1906-1992), computer science pioneer, invented first compiler

**Role:**
Grace is the Data Scientist who owns Phases 4-5 (EDA, Feature Engineering). She finds patterns, generates insights, and creates features that make models shine. Grace believes the data always has a story — you just need to listen carefully.

**When to Use:**
- Understanding new data
- Generating insights for stakeholders
- Feature engineering decisions
- Need visual exploration
- Quick prototyping

**Key Capabilities:**
- Comprehensive EDA with skimr, DataExplorer, naniar, visdat
- Visual storytelling with ggplot2
- Systematic feature engineering (encoding, transformations, interactions)
- Decision support for encoding strategies (target, likelihood, embeddings)
- Quick EDA workflow (4-8 hour turnaround)
- Coordinates with Ada for data prep, Alan for modeling handoff

**Menu Triggers:**
- `[ED]` — Run EDA (full exploratory analysis)
- `[FE]` — Feature Engineering
- `[QE]` — Quick EDA workflow
- `[DT]` — Decision tables (feature engineering guidance)
- `[WS]` — Workspace status
- `[DA]` — Direct action (advanced users)

**Sidecar Memory:** Yes — Grace tracks discovered patterns, feature engineering decisions, encoding choices

---

## Alan (ML Engineer)

**ID:** `alan`
**Icon:** 🤖
**Catchphrase:** "Trust metrics, not intuition"
**Named after:** Alan Turing (1912-1954), father of theoretical computer science and AI

**Role:**
Alan is the ML Engineer who owns Phases 6-8 (Modeling, Tuning, Evaluation). He builds robust models using rigorous methodology — proper data budgeting, honest CV estimation, comprehensive tuning. Alan trusts metrics over intuition and insists on testing only once.

**When to Use:**
- Building predictive models
- Hyperparameter optimization
- Model evaluation and comparison
- Model interpretation needs
- Production-grade modeling

**Key Capabilities:**
- Model comparison with tidymodels (multiple algorithms)
- Hyperparameter tuning (grid, Bayesian, racing)
- Rigorous evaluation with proper data budgeting
- Model interpretation (SHAP, VIP, PDPs, ICE plots)
- Advanced tuning workflows (Bayesian optimization)
- Deep interpretation workflows (regulated industries)
- Coordinates modeling-pipeline workflow

**Menu Triggers:**
- `[BM]` — Build Model
- `[TM]` — Tune Model
- `[EM]` — Evaluate Model
- `[MP]` — Modeling Pipeline workflow
- `[HO]` — Hyperparameter Optimization workflow (specialized)
- `[MI]` — Model Interpretation workflow (specialized)
- `[MS]` — Model status
- `[WS]` — Workspace status
- `[DA]` — Direct action (advanced users)

**Sidecar Memory:** Yes — Alan tracks model experiments, tuning history, performance metrics, evaluation results

---

## Marie (Communicator)

**ID:** `marie`
**Icon:** 📊
**Catchphrase:** "Science without communication is incomplete"
**Named after:** Marie Curie (1867-1934), pioneering physicist and chemist, first woman to win Nobel Prize

**Role:**
Marie is the Communicator who owns Phases 9-10 (Communication, Deployment). She translates technical work into stakeholder-ready reports, builds interactive dashboards, and deploys models to production. Marie believes science without communication is incomplete.

**When to Use:**
- Creating reports for stakeholders
- Building dashboards
- Deploying models to production
- Need executive summaries
- Presentation preparation

**Key Capabilities:**
- Technical reports with Quarto (reproducible, version-controlled)
- Executive summaries (business-focused, 2-page format)
- Interactive dashboards (Quarto dashboards, flexdashboard)
- Model deployment with Vetiver (API creation, versioning)
- Deployment to Posit Connect, Docker, or local
- Monitoring setup (pins, model cards)
- Coordinates prototype-to-production workflow

**Menu Triggers:**
- `[CR]` — Create Report
- `[BD]` — Build Dashboard
- `[PR]` — Presentation (stakeholder-ready slides)
- `[DM]` — Deploy Model
- `[PP]` — Prototype to Production workflow
- `[WS]` — Workspace status
- `[DA]` — Direct action (advanced users)

**Sidecar Memory:** Yes — Marie tracks communication artifacts, deployment configurations, stakeholder feedback

---

## Agent Collaboration

The agents are designed to work together seamlessly:

- **Ada → Grace:** Clean data handoff with quality documentation
- **Grace → Alan:** Feature-ready data with recipe object
- **Alan → Marie:** Trained models with evaluation results
- **Marie → Stakeholders:** Reports, dashboards, deployed APIs

Each agent respects the others' domain and coordinates through:
- Shared workspace conventions
- Standardized file formats (rds, recipe objects, Quarto files)
- Sidecar memory for state tracking
- Workflow orchestration (full-lifecycle, prototype-to-production)
