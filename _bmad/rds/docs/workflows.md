# Workflows Reference

rds includes 7 workflows organized into Core and Specialized categories:

---

## Core Workflows

### full-lifecycle

**ID:** `bmad:rds:workflows:full-lifecycle`
**Duration:** 2-4 weeks
**Orchestrated by:** Ada

**Purpose:**
Execute the complete 10-phase Data Science lifecycle from raw data to deployed model. Comprehensive approach for mission-critical projects requiring deep analysis and stakeholder buy-in.

**When to Use:**
- Strategic projects with long timeline
- Need comprehensive documentation
- Multiple stakeholders involved
- High-stakes decisions
- Production deployment required

**Key Steps:**
1. Project setup (structure, Git, renv)
2. Data import & profiling
3. Data cleaning & validation
4. Exploratory analysis (comprehensive)
5. Feature engineering (systematic)
6. Model building & comparison
7. Hyperparameter tuning
8. Model evaluation (test set, interpretation)
9. Communication (reports, dashboards)
10. Deployment (Vetiver API, monitoring)

**Agent(s):** Ada (orchestrator) → Grace → Alan → Marie

**Outputs:**
- Complete project structure
- Cleaned data with documentation
- EDA reports (20-30 pages)
- Feature engineering documentation
- Trained models with tuning history
- Evaluation reports with interpretation
- Technical + executive reports
- Interactive dashboards
- Deployed API with monitoring

---

### modeling-pipeline

**ID:** `bmad:rds:workflows:modeling-pipeline`
**Duration:** 1-2 weeks
**Owned by:** Alan

**Purpose:**
Execute feature engineering through model evaluation (Phases 5-8) assuming data is already clean. Focuses on creating features, building models, tuning, and rigorous evaluation.

**When to Use:**
- Clean data ready for modeling
- Need systematic feature engineering
- Compare multiple model types
- Rigorous evaluation required
- Don't need full lifecycle

**Key Steps:**
1. Feature engineering (transform, encode, create features + recipe)
2. Baseline models (build and compare multiple types)
3. Tuning (hyperparameter optimization with grid/Bayesian)
4. Evaluation (test set evaluation, diagnostics, interpretation)

**Agent(s):** Alan (owner) with Grace assist on feature engineering

**Outputs:**
- `recipe.rds` — Preprocessing recipe object
- `trained_models/` — Model objects
- `model_comparison.html` — Model comparison report
- `final_model.rds` — Best tuned model
- `evaluation_report.html` — Test set results, diagnostics
- `interpretation/` — VIP plots, SHAP values, PDPs

---

### prototype-to-production

**ID:** `bmad:rds:workflows:prototype-to-production`
**Duration:** 1-2 weeks
**Owned by:** Marie (with Alan handoff)

**Purpose:**
Take features/recipe through modeling, communication, and deployment (Phases 6-10). Assumes features are ready, focuses on model development, documentation, and production deployment.

**When to Use:**
- Features/recipe already created
- Need production deployment
- Multiple stakeholder reports required
- Monitoring setup needed
- Taking prototype to production

**Key Steps:**
1. Build model (create and compare models)
2. Tune (optimize hyperparameters)
3. Evaluate (test set + interpretation)
4. Communicate (reports + dashboards)
5. Deploy (Vetiver API + monitoring setup)

**Agent(s):** Marie (owner) with Alan handoff (Phases 6-8 → Phases 9-10)

**Outputs:**
- `final_model.rds` — Production model
- `technical_report.qmd/.html` — Technical documentation
- `executive_summary.qmd/.html` — Business summary
- `dashboard.qmd/.html` — Interactive dashboard
- `model_api/` — Vetiver API files
- `monitoring_setup.md` — Monitoring configuration

---

### quick-eda

**ID:** `bmad:rds:workflows:quick-eda`
**Duration:** 4-8 hours
**Owned by:** Grace

**Purpose:**
Streamlined exploration for urgent questions or initial understanding. Fast turnaround with solid insights, skipping deep modeling.

**When to Use:**
- Need fast insights
- Exploring new data
- Answering urgent business questions
- Pre-project scoping
- Not ready for modeling

**Key Steps:**
1. Quick setup (coordinated with Ada)
2. Import & profile (automated)
3. Targeted exploration (visual focus)
4. Report generation (HTML dashboard)

**Agent(s):** Grace (owner) with Ada coordination for setup

**Outputs:**
- `quick-eda.html` — Comprehensive visual report
- `insights.md` — Key findings documented
- `data_profile.csv` — Summary statistics
- `plots/` — Individual visualizations

---

## Specialized Workflows

### data-quality-check

**ID:** `bmad:rds:workflows:data-quality-check`
**Duration:** 4-8 hours
**Owned by:** Ada

**Purpose:**
Deep dive into data quality analysis (expanded Phase 3). Comprehensive assessment for suspicious data, high missings, or critical projects. Goes beyond standard cleaning with systematic validation.

**When to Use:**
- Suspicious data patterns
- High missing rates (>15%)
- Critical projects
- Need systematic validation
- Domain-specific rules required

**Key Steps:**
1. Missing analysis (pattern detection: MCAR, MAR, MNAR)
2. Outlier detection (systematic identification)
3. Consistency checks (cross-variable validation, domain rules)
4. Remediation (fix issues, document decisions)

**Agent(s):** Ada (solo workflow)

**Outputs:**
- `data_quality_report.html` — Comprehensive quality assessment
- `missing_analysis.html` — Missing data patterns
- `outlier_report.html` — Outlier detection results
- `remediation_log.md` — Documentation of fixes applied

---

### hyperparameter-optimization

**ID:** `bmad:rds:workflows:hyperparameter-optimization`
**Duration:** 1-3 days
**Owned by:** Alan

**Purpose:**
Deep dive hyperparameter tuning (expanded Phase 7). Advanced tuning strategies for critical performance scenarios using Bayesian optimization, racing methods, and ensemble approaches.

**When to Use:**
- Critical performance requirements
- Competitions (Kaggle-style)
- High-stakes projects
- Need maximum model performance
- Have computational budget

**Key Steps:**
1. Search space (define comprehensive parameter space)
2. Bayesian optimization (efficient parameter search)
3. Racing (early stopping for efficiency)
4. Ensemble (combine multiple tuned models)

**Agent(s):** Alan (solo workflow)

**Outputs:**
- `tuning_results.html` — Complete tuning analysis
- `best_params.rds` — Optimal hyperparameters
- `tuning_history.csv` — All iterations evaluated
- `ensemble_model.rds` — Ensemble if created

---

### model-interpretation

**ID:** `bmad:rds:workflows:model-interpretation`
**Duration:** 1-2 days
**Owned by:** Alan

**Purpose:**
Deep dive model interpretability (expanded Phase 8). Comprehensive interpretation for regulated industries or stakeholder requirements using SHAP, LIME, VIP, PDPs, and other explainability methods.

**When to Use:**
- Regulated industries (healthcare, finance)
- Stakeholder requirements for explainability
- Need to build trust in model
- Complex black-box models
- Audit requirements

**Key Steps:**
1. Global interpretation (overall model behavior: VIP, PDPs)
2. Local interpretation (individual predictions: SHAP, LIME)
3. Feature importance (permutation importance, SHAP values)
4. Documentation (generate interpretation report)

**Agent(s):** Alan (solo workflow) with Marie assist on communication

**Outputs:**
- `interpretation_report.html` — Comprehensive interpretation
- `global_interpretation/` — VIP plots, PDPs, ICE plots
- `local_interpretation/` — SHAP values, LIME explanations
- `feature_importance.csv` — Permutation importance results

---

## Workflow Selection Guide

| Scenario | Recommended Workflow | Duration |
|----------|---------------------|----------|
| New project, start to finish | full-lifecycle | 2-4 weeks |
| Clean data → production | prototype-to-production | 1-2 weeks |
| Clean data → modeling only | modeling-pipeline | 1-2 weeks |
| Fast insights, no model | quick-eda | 4-8 hours |
| Suspicious data | data-quality-check | 4-8 hours |
| Need max performance | hyperparameter-optimization | 1-3 days |
| Need explainability | model-interpretation | 1-2 days |

---

## Workflow Combination Patterns

**Pattern 1: Quality-First Full Lifecycle**
1. data-quality-check (validate data thoroughly)
2. full-lifecycle (execute complete DS lifecycle)
3. model-interpretation (add explainability)

**Pattern 2: Quick Prototype → Production**
1. quick-eda (understand data fast)
2. modeling-pipeline (build models)
3. prototype-to-production (deploy)

**Pattern 3: Performance-Critical Project**
1. full-lifecycle (standard approach)
2. hyperparameter-optimization (squeeze performance)
3. model-interpretation (explain results)

**Pattern 4: Exploratory → Full Analysis**
1. quick-eda (initial exploration)
2. (decision point: continue?)
3. full-lifecycle (if yes, full analysis)
