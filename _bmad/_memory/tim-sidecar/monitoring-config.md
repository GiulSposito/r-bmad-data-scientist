# Monitoring Configuration

**Owner:** Tim (The Deployer)
**Purpose:** Track all monitoring setups, alert configurations, and SLO definitions

---

## Active Monitors

| Service | Metric | Threshold | Alert Channel | Status |
|---------|--------|-----------|---------------|--------|
| _No monitors configured yet_ | - | - | - | - |

---

## SLOs (Service Level Objectives)

### Template SLO

```markdown
## SLO: [service-name]

**Target:** [99.9% uptime]
**Measurement Window:** [30 days rolling]

**Metrics:**
- **Availability:** API returns 200 status
  - Target: 99.9%
  - Alert: < 99.5%

- **Latency (p95):** Prediction response time
  - Target: < 200ms
  - Alert: > 300ms

- **Error Rate:** 5xx responses
  - Target: < 0.1%
  - Alert: > 0.5%

**Alert Channels:**
- Email: [team@example.com]
- Slack: [#ml-alerts]
- PagerDuty: [on-call rotation]
```

---

## Dashboard Links

| Dashboard | URL | Purpose |
|-----------|-----|---------|
| _No dashboards yet_ | - | - |

---

## Alert Rules

### Template Alert

```markdown
## Alert: [alert-name]

**Condition:** [metric > threshold for duration]
**Severity:** [Critical/Warning/Info]
**Channel:** [email/slack/pagerduty]

**Runbook:**
1. Check [dashboard-link]
2. Verify [health-endpoint]
3. Review recent deployments
4. Escalate if not resolved in [15 minutes]

**False Positive Patterns:**
- [Known issue that triggers this alert]
```

---

## Monitoring Stack

**Tools in use:**
- [ ] Prometheus
- [ ] Grafana
- [ ] Vetiver monitoring
- [ ] Custom R dashboards
- [ ] Application logs

---

## Notes

- Review SLOs quarterly with stakeholders
- Tune alert thresholds to reduce noise
- Document all false positives for future reference
