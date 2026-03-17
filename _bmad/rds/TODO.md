# TODO: R Data Science

Development roadmap for rds module.

---

## Agents to Build

- [ ] Ada (Project Architect — Phases 1-3)
  - Use: `bmad:bmb:agents:agent-builder` or `/agent`
  - Spec: `agents/ada.spec.md`

- [ ] Grace (Data Scientist — Phases 4-5)
  - Use: `bmad:bmb:agents:agent-builder` or `/agent`
  - Spec: `agents/grace.spec.md`

- [ ] Alan (ML Engineer — Phases 6-8)
  - Use: `bmad:bmb:agents:agent-builder` or `/agent`
  - Spec: `agents/alan.spec.md`

- [ ] Marie (Communicator — Phases 9-10)
  - Use: `bmad:bmb:agents:agent-builder` or `/agent`
  - Spec: `agents/marie.spec.md`

---

## Workflows to Build

- [ ] full-lifecycle
  - Use: `bmad:bmb:workflows:workflow` or `/workflow`
  - Spec: `workflows/full-lifecycle/full-lifecycle.spec.md`

- [ ] quick-eda
  - Use: `bmad:bmb:workflows:workflow` or `/workflow`
  - Spec: `workflows/quick-eda/quick-eda.spec.md`

- [ ] modeling-pipeline
  - Use: `bmad:bmb:workflows:workflow` or `/workflow`
  - Spec: `workflows/modeling-pipeline/modeling-pipeline.spec.md`

- [ ] prototype-to-production
  - Use: `bmad:bmb:workflows:workflow` or `/workflow`
  - Spec: `workflows/prototype-to-production/prototype-to-production.spec.md`

- [ ] data-quality-check
  - Use: `bmad:bmb:workflows:workflow` or `/workflow`
  - Spec: `workflows/data-quality-check/data-quality-check.spec.md`

- [ ] hyperparameter-optimization
  - Use: `bmad:bmb:workflows:workflow` or `/workflow`
  - Spec: `workflows/hyperparameter-optimization/hyperparameter-optimization.spec.md`

- [ ] model-interpretation
  - Use: `bmad:bmb:workflows:workflow` or `/workflow`
  - Spec: `workflows/model-interpretation/model-interpretation.spec.md`

---

## Installation Testing

- [ ] Test installation with `bmad install`
- [ ] Verify config.yaml integration with core config
- [ ] Test agent invocation from bmad-master menu
- [ ] Verify workflow loading and execution

---

## Documentation

- [x] Complete README.md with usage examples
- [x] Create TODO.md with development roadmap
- [ ] Enhance docs/ folder with detailed guides
- [ ] Add troubleshooting section
- [ ] Document configuration options
- [ ] Add real-world usage examples

---

## Templates & Data Files

- [ ] Create decision trees for feature engineering (Grace)
- [ ] Create model selection tables (Alan)
- [ ] Create encoding strategy guides (Grace)
- [ ] Create deployment checklists (Marie)
- [ ] Create evaluation rubrics (Alan)

---

## Next Steps

1. Build agents using agent-builder workflow (`/agent`)
   - Start with Ada (foundational agent)
   - Then Grace (data science expertise)
   - Then Alan (ML engineering)
   - Finally Marie (communication/deployment)

2. Build workflows using workflow-builder workflow (`/workflow`)
   - Start with quick-eda (simplest, 4 steps)
   - Then modeling-pipeline (core workflow)
   - Then full-lifecycle (most comprehensive)
   - Then specialized workflows

3. Test installation and functionality
   - Install module via bmad installer
   - Test each agent activation
   - Test each workflow execution
   - Verify cross-agent handoffs

4. Iterate based on testing
   - Refine agent menus based on usage
   - Enhance workflows with real-world feedback
   - Add more templates and data files
   - Document edge cases and troubleshooting

---

_Last updated: 2026-03-17_
