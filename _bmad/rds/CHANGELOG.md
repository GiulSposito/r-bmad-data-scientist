# Changelog

All notable changes to the RDS (R Data Science) module will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.2.0] - 2026-03-26

### Added

- **New Agent: Tim (The Deployer)** - Phase 10 specialist for production deployment and monitoring
  - Vetiver API deployment workflow
  - Docker containerization
  - Production monitoring setup
  - Model versioning and registry
  - Sidecar memory with deployment history
- **6 New Workflows:**
  - `technical-report` - Comprehensive Quarto technical documentation
  - `executive-report` - Executive summaries for stakeholders
  - `build-dashboard` - Interactive Shiny dashboards
  - `presentation-generation` - Quarto reveal.js presentations
  - `deploy-model` - Vetiver API deployment with Docker
  - `model-monitoring` - Production monitoring and alerting setup

### Changed

- **Marie refactored from "Communicator" to "Reporter"**
  - Now focuses exclusively on Phase 9 (Communication & Reporting)
  - Deployment responsibilities moved to Tim
  - Updated menu structure to remove deployment commands
  - Sidecar memory reorganized (removed deployment-registry, added report-templates and stakeholder-preferences)
- **Package version bumped to 0.2.0** to reflect major changes
- **Module compatibility updated to BMAD 6.2.2+**
- **README updated** to reflect 5 agents and 13 workflows

### Removed

- Marie no longer handles Phase 10 (Deployment) - moved to Tim
- Deployment workflows removed from Marie's menu ([DM], [MM])

## [0.1.0] - 2026-03-17

### Added

- Initial module structure
- 4 agents: Ada, Grace, Alan, Marie
- 7 core workflows:
  - full-lifecycle
  - quick-eda
  - modeling-pipeline
  - prototype-to-production
  - data-quality-check
  - hyperparameter-optimization
  - model-interpretation
- Module configuration and documentation
- Integration with 20+ R data science skills

### Notes

- Built with BMAD 6.0.0 compatibility
- Initial implementation complete but Marie handling both Phases 9-10

---

## Version History Summary

| Version | Date | Key Changes |
|---------|------|-------------|
| 0.2.0 | 2026-03-26 | Added Tim (Deployer), 6 new workflows, refactored Marie |
| 0.1.0 | 2026-03-17 | Initial release with 4 agents and 7 workflows |
