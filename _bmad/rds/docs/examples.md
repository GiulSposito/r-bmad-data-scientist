# Examples & Use Cases

This section provides practical examples for using R Data Science module.

---

## Example Workflows

### Example 1: Customer Churn Prediction (Quick Prototype)

**Scenario:** Ana (Senior DS) receives customer churn data on Monday, needs prototype by Friday.

**Workflow:** Quick prototype approach (6-8 hours total)

**Steps:**

1. **Setup Project (15 min)** — Ada `[SP]`
   ```
   /bmad:rds:agents:ada
   [SP] Setup Project
   - Creates: churn-analysis/
   - Initializes: Git, renv, proper structure
   ```

2. **Import & Inspect (20 min)** — Ada `[II]`
   ```
   [II] Import & Inspect
   - Loads: customers.csv (10,000 rows, 25 features)
   - Detects: 15% missing values in income, 3 outliers in tenure
   ```

3. **Clean Data (30 min)** — Ada `[CD]`
   ```
   [CD] Clean Data
   - Imputes: income (median by region)
   - Handles: outliers (investigation → keep valid data)
   - Documents: all decisions in cleaning_log.md
   ```

4. **Quick EDA (2 hours)** — Grace `[QE]`
   ```
   /bmad:rds:agents:grace
   [QE] Quick EDA workflow
   - Discovery: Customers with >3 support calls have 5x higher churn
   - Discovery: Contract length strong predictor (monthly vs annual)
   - Generates: quick-eda.html with 15 visualizations
   ```

5. **Modeling Pipeline (3 hours)** — Alan `[MP]`
   ```
   /bmad:rds:agents:alan
   [MP] Modeling Pipeline
   - Tests: Logistic, Random Forest, XGBoost
   - Best: XGBoost (87% accuracy, 0.82 AUC)
   - Tunes: 20 iterations, optimal params found
   ```

6. **Dashboard (45 min)** — Marie `[BD]`
   ```
   /bmad:rds:agents:marie
   [BD] Build Dashboard
   - Creates: interactive dashboard
   - Shows: KPIs, feature importance, predictions
   - Format: churn-dashboard.html
   ```

**Result:**
- 6.5 hours total
- Production-ready prototype
- 87% accuracy model
- Documented, reproducible
- Stakeholder-ready dashboard

---

### Example 2: Demand Forecasting (Full Production)

**Scenario:** João (ML Engineer) needs strategic demand forecasting in production.

**Workflow:** Full lifecycle (2-3 weeks)

**Week 1: Foundation (Ada + Grace)**

```
/bmad:rds:agents:ada
[FL] Full Lifecycle workflow

Phase 1-3 (Ada):
- Deep setup with team conventions
- Import: 3 years sales data (500k transactions)
- Quality check: detects seasonality artifacts, fixes encoding issues

Phase 4 (Grace):
- EDA: 30-page report
- Discovers: Strong weekly/monthly seasonality, holiday effects, store clustering
```

**Week 2: Modeling (Alan)**

```
Phase 5 (Grace):
- Features: 47 created (lags, rolling means, holiday flags, store embeddings)
- Recipe: comprehensive preprocessing pipeline

Phase 6-7 (Alan):
- Models: Prophet, XGBoost, LSTM (torch)
- Time series CV: walk-forward validation
- Tuning: Bayesian optimization (50 iterations)
- Best: Ensemble (Prophet + XGBoost) — RMSE 145, MAE 98
```

**Week 3: Communication + Deployment (Marie)**

```
Phase 8 (Alan):
- Evaluation: rigorous backtesting
- Interpretation: SHAP for XGBoost, Prophet decomposition

Phase 9-10 (Marie):
- Technical report: 30 pages with methodology
- Executive summary: 2 pages, business-focused
- Dashboard: interactive forecast explorer
- Deployment: Vetiver API on Posit Connect
- Monitoring: pins for tracking, model card created
```

**Result:**
- Production-deployed forecast model
- Comprehensive documentation
- Monitoring infrastructure
- Approved by technical and business teams
- Retraining pipeline established

---

### Example 3: Sales Exploration (EDA Only)

**Scenario:** Maria (Analyst) explores sales data from 5 stores.

**Workflow:** Quick EDA (3 hours)

**Steps:**

1. **Invoke Grace** (coordinator)
   ```
   /bmad:rds:agents:grace
   [ED] Run EDA
   ```

2. **Grace coordinates with Ada** (5 min setup)
   - Quick project structure
   - Import: sales-transactions.csv (100k rows)

3. **Grace runs comprehensive EDA** (2.5 hours)
   - Automatic profiling with skimr
   - Visual exploration with DataExplorer
   - Custom plots with ggplot2

4. **Discoveries:**
   - Store 3: 2x weekend sales vs weekdays
   - Electronics: 3x higher avg ticket than other categories
   - December: confirmed peak season (2.5x average)
   - Outliers: 12 transactions >$10k (investigated → corporate orders)

5. **Marie generates report** (coordinated handoff)
   ```
   Beautiful HTML report: eda-sales-exploration.html
   - Executive summary
   - Key insights highlighted
   - 20 visualizations
   - Recommendations section
   ```

**Result:**
- 3 hours total
- Actionable insights
- Beautiful documentation
- Maria learns structured EDA approach

**The "Aha!" moment:** "So THIS is how structured workflows work! I can replicate this for other data."

---

## Common Scenarios

### Scenario: High Missing Data

**Problem:** Dataset with 40% missing values in key features

**Solution:**
```
/bmad:rds:agents:ada
[DQ] Data Quality Check workflow

Step 1: Missing Analysis
- Identifies: MAR pattern (related to customer age)
- Visualizes: missing patterns with naniar

Step 2: Outlier Detection
- Multiple methods: IQR, isolation forest, domain rules

Step 3: Consistency Checks
- Cross-validates: age vs tenure, income vs purchase patterns

Step 4: Remediation
- Documents: every decision
- Strategy: Multiple imputation for MAR, sensitivity analysis
```

**Result:** Systematic remediation with full documentation

---

### Scenario: Black-Box Model Needs Explainability

**Problem:** XGBoost model for loan approval needs regulatory compliance

**Solution:**
```
/bmad:rds:agents:alan
[MI] Model Interpretation workflow

Step 1: Global Interpretation
- VIP: debt-to-income ratio most important
- PDPs: shows non-linear relationship with credit score

Step 2: Local Interpretation
- SHAP: explains individual predictions
- LIME: validates SHAP findings

Step 3: Feature Importance
- Permutation importance confirms VIP
- Documents: all features ranked

Step 4: Documentation
- Generates: interpretation_report.html
- Audience: technical + compliance teams
```

**Result:** Fully explainable model meeting regulatory requirements

---

### Scenario: Model Performance Critical

**Problem:** Kaggle competition or high-stakes prediction requiring maximum performance

**Solution:**
```
/bmad:rds:agents:alan
[HO] Hyperparameter Optimization workflow

Step 1: Search Space
- Comprehensive: 8 hyperparameters, wide ranges

Step 2: Bayesian Optimization
- Efficient search: 200 iterations
- Tracks: full tuning trajectory

Step 3: Racing
- Early stopping: eliminates poor configurations fast

Step 4: Ensemble
- Combines: top 5 configurations
- Stacking: meta-learner improves performance
```

**Result:** Squeezed every bit of performance, ensemble model 2% better than single model

---

## Tips & Tricks

### Tip 1: Always Start with Quick EDA
Even if you think you know the data, Grace's Quick EDA often reveals surprises. Investment of 4 hours can save days of debugging later.

### Tip 2: Use Sidecar Memory
Agents remember project state. After Ada cleans data, Grace and Alan know what's been done. No need to repeat context.

### Tip 3: Coordinate Agent Handoffs
```
Ada cleans data → creates clean_data.rds
Grace reads clean_data.rds → creates recipe.rds + features_ready.rds
Alan reads recipe.rds → creates final_model.rds
Marie reads final_model.rds → deploys
```

### Tip 4: Document As You Go
Don't wait until the end. Each phase creates documentation:
- Ada: cleaning_log.md
- Grace: eda_report.html, feature_decisions.md
- Alan: model_comparison.html, evaluation_report.html
- Marie: technical_report.qmd, executive_summary.qmd

### Tip 5: Use Workflows for Consistency
Individual agent commands = flexibility
Workflows = consistent, repeatable process

Choose based on:
- New project? → full-lifecycle workflow
- Known pattern? → Individual agent commands
- Teaching someone? → Workflows (shows the right way)

### Tip 6: Leverage R Skills
The module integrates 20+ R skills. When you work with ggplot2, Grace automatically has access to advanced visualization patterns. When Alan tunes models, tidymodels expertise is activated.

### Tip 7: Test Set Discipline
Alan enforces proper data budgeting — test set is touched ONCE. If you peek early, he'll notice and guide you back to the right path.

### Tip 8: Reproducibility by Default
Every project gets:
- Git repository (version control)
- renv (dependency management)
- Quarto (reproducible reports)
- Proper .gitignore (no data or credentials committed)

You don't have to think about it — Ada handles it in project setup.

---

## Troubleshooting

### Issue: "Agent doesn't have context about my data"

**Solution:** Agents use sidecar memory to maintain state, but memory is session-based. If you start a new session:
1. Check `workspace_state.md` (Ada creates this)
2. Use `[WS]` Workspace Status command to refresh agent memory
3. Point agents to key files (clean_data.rds, recipe.rds)

---

### Issue: "Workflow feels too rigid"

**Solution:** Workflows are designed for consistency, but you can:
1. Use individual agent commands instead of workflows
2. Use `[DA]` Direct Action for advanced custom operations
3. Skip workflow steps if prerequisites are met
4. Combine workflows (e.g., quick-eda → modeling-pipeline)

---

### Issue: "Model performance not meeting expectations"

**Solution:**
1. Alan → `[MP]` Modeling Pipeline (try multiple model types)
2. Grace → `[FE]` Feature Engineering (revisit features)
3. Alan → `[HO]` Hyperparameter Optimization (deep tuning)
4. Check data quality (Ada → `[DQ]`)
5. Consider ensemble approaches

---

### Issue: "Need to explain model to non-technical stakeholders"

**Solution:**
1. Alan → `[MI]` Model Interpretation (generate visuals)
2. Marie → `[BD]` Build Dashboard (interactive exploration)
3. Marie → `[PR]` Presentation (stakeholder-ready slides)
4. Use executive summary format (Marie creates automatically)

---

### Issue: "Installation problems or agent not loading"

**Solution:**
1. Check: `_bmad/rds/config.yaml` exists
2. Verify: Module listed in `_bmad/_config/manifest.yaml`
3. Test: `/bmad:rds:agents:ada` invocation
4. Check: Agent specs exist in `_bmad/rds/agents/*.spec.md`
5. See: TODO.md for implementation status

---

## Getting More Help

- Review the main BMAD documentation for system architecture
- Check module configuration in `_bmad/rds/config.yaml`
- Verify all agents and workflows are properly installed (see TODO.md)
- Consult [Agents Reference](agents.md) for detailed agent capabilities
- See [Workflows Reference](workflows.md) for workflow selection guidance
- Use `[WS]` Workspace Status with any agent to check current project state
