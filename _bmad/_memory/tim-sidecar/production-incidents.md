# Production Incidents Log

**Owner:** Tim (The Deployer)
**Purpose:** Document all production incidents, rollbacks, and lessons learned

---

## Incident Response Protocol

1. **Detect** — Alert fires or manual detection
2. **Assess** — Check dashboards, logs, recent deployments
3. **Mitigate** — Rollback or hotfix
4. **Communicate** — Update stakeholders
5. **Document** — Log incident here
6. **Learn** — Update monitoring/procedures

---

## Active Incidents

| Incident ID | Started | Severity | Status | Owner |
|-------------|---------|----------|--------|-------|
| _No active incidents_ | - | - | - | - |

---

## Incident History

### Template Incident

```markdown
## Incident: [INC-YYYY-MM-DD-001]

**Date:** [YYYY-MM-DD HH:MM - HH:MM UTC]
**Severity:** [P0-Critical / P1-High / P2-Medium / P3-Low]
**Status:** [Resolved / Investigating / Monitoring]

**Summary:**
[Brief description of what happened]

**Impact:**
- **Users Affected:** [number or percentage]
- **Duration:** [XX minutes]
- **Service Degradation:** [Complete outage / Partial / Slow responses]

**Timeline:**
- HH:MM - Alert fired: [alert name]
- HH:MM - Investigation started
- HH:MM - Root cause identified: [cause]
- HH:MM - Mitigation deployed: [rollback/hotfix]
- HH:MM - Service restored
- HH:MM - Incident closed

**Root Cause:**
[Technical explanation of what went wrong]

**Resolution:**
[What was done to fix it]

**Prevention:**
- [ ] Action item 1: [improve monitoring]
- [ ] Action item 2: [update deployment process]
- [ ] Action item 3: [add validation check]

**Lessons Learned:**
- [What we learned from this incident]
- [How we improved our processes]
```

---

## Rollback Log

| Date | Model Version | Reason | Time to Rollback |
|------|---------------|--------|------------------|
| _No rollbacks yet_ | - | - | - |

---

## Known Issues

_Document recurring patterns or known limitations_

---

## Notes

- Review incidents quarterly for patterns
- Share lessons learned with Alan and Marie
- Update runbooks after each major incident
- Celebrate successful mitigations — incident response is a skill
