# Deployment Registry

**Owner:** Tim (The Deployer)
**Purpose:** Track all model deployments, production versions, and rollback history

---

## Current Production

| Model | Version | Deployed | Endpoint | Status |
|-------|---------|----------|----------|--------|
| _No deployments yet_ | - | - | - | - |

---

## Deployment History

### Template Entry

```markdown
## Deployment: [YYYY-MM-DD HH:MM]

**Model:** [model-name]
**Version:** [v1.0.0]
**Environment:** [production/staging]
**Endpoint:** [https://api.example.com/predict]
**Deployment Strategy:** [blue-green/canary/rolling]

**Pre-flight Checks:**
- ✅ Model artifacts validated
- ✅ Health endpoint tested
- ✅ Monitoring configured
- ✅ Rollback plan ready

**Outcome:** [Success/Rolled back]
**Notes:** [Any relevant details]
```

---

## Rollback Events

_Log all rollback events with reasons and lessons learned_

---

## Notes

- Keep entries concise — full details in production-incidents.md
- Update current production table after every deployment
- Archive old entries after 90 days
