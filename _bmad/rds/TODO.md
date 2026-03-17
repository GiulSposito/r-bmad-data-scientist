# TODO: R Data Science

Development roadmap for rds module.

---

## Agents to Build

- [x] Ada (Project Architect — Phases 1-3) ✅ COMPLETE
  - Built with `agent-builder` on 2026-03-17
  - Location: `agents/ada.md`

- [x] Grace (Data Scientist — Phases 4-5) ✅ COMPLETE
  - Built with `agent-builder` on 2026-03-17
  - Location: `agents/grace.md`

- [x] Alan (ML Engineer — Phases 6-8) ✅ COMPLETE
  - Built with `agent-builder` on 2026-03-17
  - Location: `agents/alan.md`

- [x] Marie (Communicator — Phases 9-10) ✅ COMPLETE
  - Built with `agent-builder` on 2026-03-17
  - Location: `agents/marie.md`

---

## Workflows to Build

- [x] full-lifecycle ✅ COMPLETE (10 steps, 148KB)
  - Built with parallel subagents on 2026-03-17
  - Location: `workflows/full-lifecycle/`

- [x] quick-eda ✅ COMPLETE (4 steps)
  - Built with parallel subagents on 2026-03-17
  - Location: `workflows/quick-eda/`

- [x] modeling-pipeline ✅ COMPLETE (4 steps, 112KB)
  - Built with parallel subagents on 2026-03-17
  - Location: `workflows/modeling-pipeline/`

- [x] prototype-to-production ✅ COMPLETE (5 steps)
  - Built with parallel subagents on 2026-03-17
  - Location: `workflows/prototype-to-production/`

- [x] data-quality-check ✅ COMPLETE (4 steps)
  - Built with parallel subagents on 2026-03-17
  - Location: `workflows/data-quality-check/`

- [x] hyperparameter-optimization ✅ COMPLETE (4 steps, 83KB)
  - Built with parallel subagents on 2026-03-17
  - Location: `workflows/hyperparameter-optimization/`

- [x] model-interpretation ✅ COMPLETE (4 steps)
  - Built with parallel subagents on 2026-03-17
  - Location: `workflows/model-interpretation/`

### Future Workflows (Phase 2)

- [ ] setup-project (Ada - individual workflow)
- [ ] import-inspect (Ada - individual workflow)
- [ ] clean-data (Ada - individual workflow)
- [ ] exploratory-analysis (Grace - individual workflow)
- [ ] feature-engineering (Grace - individual workflow)
- [ ] build-model (Alan - individual workflow)
- [ ] tune-model (Alan - individual workflow)
- [ ] evaluate-model (Alan - individual workflow)

Note: These Phase 2 workflows can be extracted from existing full-lifecycle and modeling-pipeline steps if needed.

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
