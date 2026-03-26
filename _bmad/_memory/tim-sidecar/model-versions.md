# Model Versions Registry

**Owner:** Tim (The Deployer)
**Purpose:** Track all model versions with performance baselines and deployment readiness

---

## Production Models

| Model ID | Version | Test RMSE | Test Accuracy | Deployed | Status |
|----------|---------|-----------|---------------|----------|--------|
| _No models deployed yet_ | - | - | - | - | - |

---

## Staged Models (Ready for Deployment)

| Model ID | Version | Test RMSE | Test Accuracy | Validated | Notes |
|----------|---------|-----------|---------------|-----------|-------|
| _No staged models_ | - | - | - | - | - |

---

## Model Metadata Template

```markdown
## Model: [model-id]

**Version:** [v1.0.0]
**Created:** [YYYY-MM-DD]
**Algorithm:** [xgboost/glmnet/ranger/etc]
**Training Data:** [dataset-v1.0]

**Performance (Test Set):**
- RMSE: [0.123]
- Accuracy: [0.89]
- Other metrics: [...]

**Artifacts:**
- Model file: [path/to/model.rds]
- Recipe file: [path/to/recipe.rds]
- Vetiver bundle: [path/to/vetiver-bundle]

**Dependencies:**
- R version: [4.3.0]
- tidymodels: [1.1.1]
- vetiver: [0.2.3]

**Deployment Readiness:**
- [ ] Model validated by Alan
- [ ] Prediction endpoint tested
- [ ] Health check implemented
- [ ] Monitoring configured
- [ ] Rollback plan documented

**Notes:** [Any relevant context]
```

---

## Versioning Convention

- **Major.Minor.Patch** (e.g., v1.2.3)
- **Major:** Algorithm change or breaking API change
- **Minor:** Retrained on new data, same architecture
- **Patch:** Bug fix or minor tuning adjustment

---

## Notes

- Model versions link to Alan's evaluation artifacts
- Keep performance baselines for comparison
- Archive models after 6 months of no usage
