# Getting Started with R Data Science

Welcome to rds! This guide will help you get up and running.

---

## What This Module Does

The rds module provides an executable guided framework that transforms ad-hoc R data science projects into production-ready pipelines. It orchestrates the complete Data Science lifecycle (raw data → deployed model) following best practices from the Tidyverse, Tidymodels, Quarto, and Vetiver ecosystems.

**Key features:**
- 10-phase structured DS lifecycle
- 4 specialized agents (Ada, Grace, Alan, Marie)
- 7 workflows (from quick EDA to full production deployment)
- Integration with 20+ R data science skills
- Pedagogical approach that teaches while executing
- Production-ready from the start (Git, renv, proper structure)

---

## Installation

If you haven't installed the module yet:

```bash
bmad install rds
```

Follow the prompts to configure the module for your needs. The installer will integrate with your BMAD core configuration to set up:
- Your name and preferred communication language
- Output folder locations
- IDE integration (if using Claude Code)

---

## First Steps

1. **Start a New Project** — Invoke Ada, the Project Architect
   ```
   /bmad:rds:agents:ada
   ```
   Choose `[SP]` Setup Project to initialize your workspace with:
   - Proper directory structure
   - Git repository
   - renv for dependency management
   - `.gitignore` and `.Rbuildignore` configured

2. **Import Your Data** — Use Ada's `[II]` Import & Inspect
   - Reads various formats (CSV, Excel, databases)
   - Automatically profiles your data
   - Identifies potential quality issues

3. **Explore Your Data** — Invoke Grace for EDA
   ```
   /bmad:rds:agents:grace
   ```
   Choose `[ED]` Run EDA or `[QE]` Quick EDA for rapid insights

4. **Build Models** — Invoke Alan when ready to model
   ```
   /bmad:rds:agents:alan
   ```
   Use `[MP]` Modeling Pipeline for the full process or `[BM]` Build Model for quick experiments

5. **Communicate Results** — Invoke Marie for reports and deployment
   ```
   /bmad:rds:agents:marie
   ```
   Choose `[CR]` Create Report or `[DM]` Deploy Model

---

## Common Use Cases

### Quick Prototype (4-8 hours)
Perfect when you need fast insights with minimal setup:
1. Ada → Setup + Import + Clean
2. Grace → Quick EDA
3. Alan → Modeling Pipeline (automated comparison + tuning)
4. Marie → Dashboard

**Result:** Production-ready prototype with documentation

### Full Production Pipeline (2-4 weeks)
For mission-critical models requiring comprehensive analysis:
1. Use the `full-lifecycle` workflow
2. Ada guides phases 1-3 (setup, import, deep cleaning)
3. Grace handles phases 4-5 (comprehensive EDA, sophisticated feature engineering)
4. Alan owns phases 6-8 (model comparison, advanced tuning, rigorous evaluation)
5. Marie completes phases 9-10 (technical + executive reports, Vetiver deployment)

**Result:** Production-deployed model with monitoring, complete documentation, stakeholder buy-in

### Exploratory Analysis (3-6 hours)
When you need to understand data without building models:
1. Grace → Run EDA
2. Marie → Build Dashboard

**Result:** Actionable insights with beautiful HTML reports

### Model Interpretation (1-2 days)
For regulated industries or stakeholder requirements:
1. Use the `model-interpretation` workflow
2. Alan generates SHAP values, VIP plots, PDPs, ICE plots
3. Marie creates interpretation-focused reports

**Result:** Explainable AI with visual emphasis

---

## What's Next?

- Check out the [Agents Reference](agents.md) to meet your team
- Browse the [Workflows Reference](workflows.md) to see what you can do
- See [Examples](examples.md) for real-world usage

---

## Need Help?

If you run into issues:
1. Check the troubleshooting section in [examples.md](examples.md)
2. Review your module configuration in `_bmad/rds/config.yaml`
3. Consult the broader BMAD documentation
4. Verify all agents and workflows are properly installed (see TODO.md)
