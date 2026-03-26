# r-bmad-data-scientist

Repository for the **RDS (R Data Science)** module for BMAD — a comprehensive framework that implements the complete lifecycle of Data Science projects in R, following modern ecosystem best practices (Tidyverse + Tidymodels + Quarto + Vetiver).

## 🎯 Objective

BMAD module that orchestrates the 10-phase Data Science workflow in R:

1. Setup & Planning
2. Import & Inspection
3. Cleaning & Wrangling
4. Exploratory Data Analysis (EDA)
5. Feature Engineering
6. Modeling
7. Tuning & Validation
8. Final Evaluation
9. Communication
10. Deployment & Monitoring

**Complete framework with 5 agents and 13 workflows implemented.**

## 📦 Structure

```
/
├── _bmad/                          # BMAD Framework
│   ├── core/                       # Core module + bmad-master (not versioned)
│   ├── bmb/                        # Builder for creating modules (not versioned)
│   └── rds/                        # ✅ RDS Module (versioned)
│       ├── module.yaml             # Module configuration (distribution format)
│       ├── package.json            # NPM package metadata
│       ├── README.md               # Module documentation
│       ├── TODO.md                 # Implementation roadmap
│       ├── agents/                 # 5 agent specs
│       │   ├── ada.spec.md         # Project Architect (Phases 1-3)
│       │   ├── grace.spec.md       # Data Scientist (Phases 4-5)
│       │   ├── alan.spec.md        # ML Engineer (Phases 6-8)
│       │   ├── marie.spec.md       # The Reporter (Phase 9)
│       │   └── tim.spec.md         # The Deployer (Phase 10)
│       ├── workflows/              # 13 workflow specs
│       │   ├── full-lifecycle/
│       │   ├── quick-eda/
│       │   ├── modeling-pipeline/
│       │   ├── prototype-to-production/
│       │   ├── data-quality-check/
│       │   ├── hyperparameter-optimization/
│       │   ├── model-interpretation/
│       │   ├── technical-report/
│       │   ├── executive-report/
│       │   ├── build-dashboard/
│       │   ├── presentation-generation/
│       │   ├── deploy-model/
│       │   └── model-monitoring/
│       └── docs/                   # User documentation
│           ├── getting-started.md
│           ├── agents.md
│           ├── workflows.md
│           └── examples.md
│
├── _bmad-output/                   # Build artifacts (versioned)
│   └── bmb-creations/
│       └── modules/
│           ├── module-brief-rds.md
│           ├── module-build-rds.md
│           └── validation-report-rds-20260317.md
│
├── .claude/
│   └── skills/                     # 20+ R Data Science Skills (not versioned)
│
├── docs/
│   └── planning/                   # Planning and preparation documents
│       ├── MODULE_BRIEF_PREPARATION.md
│       ├── rds-brief-prep.md
│       ├── data-science-lifecycle-framework.md
│       ├── REPOSITORY_STRATEGY.md
│       └── SETUP_COMPLETE.md
│
├── CLAUDE.md                       # Instructions for Claude Code
└── README.md                       # This file
```

## 🚀 Installation & Setup

### Prerequisites

1. **Claude Code** installed and running
2. **BMAD Framework** installed (v6.2.2 or higher)
3. **R** environment with tidyverse and tidymodels
4. **Git** for cloning repositories

### Step-by-Step Installation

#### 1. Install R Claude Skills

The RDS module works best with specialized R skills for Claude Code. Install them first:

```bash
# Navigate to your Claude skills directory
cd ~/.claude/skills

# Clone the R Claude Skills repository
git clone https://github.com/GiulSposito/r-claude-skills.git

# The skills are now available in Claude Code
```

**What this gives you:**
- 20+ specialized R skills (tidyverse, tidymodels, deep learning, Bayesian stats, Shiny, Quarto, etc.)
- Automatic activation when working with R code
- Production-ready patterns and best practices

#### 2. Install BMAD Framework

If you haven't installed BMAD yet:

```bash
# In your project directory
npx bmad-method install

# Select modules:
# - core (required)
# - bmb (recommended for building custom modules)
```

This installs the base BMAD framework in your project's `_bmad/` directory.

#### 3. Install RDS Module

You have two options:

**Option A: Clone this repository (recommended for development)**

```bash
# Clone this repository
git clone https://github.com/GiulSposito/r-bmad-data-scientist.git
cd r-bmad-data-scientist

# The RDS module is already in _bmad/rds/
# Copy the skills to your Claude directory
cp -r .claude/skills/* ~/.claude/skills/

# You're ready to use the module!
```

**Option B: Install as custom module in a new project**

```bash
# In your project directory
npx bmad-method install

# Select: "custom module"
# Enter path: /path/to/r-bmad-data-scientist/_bmad/rds

# The module will be copied to your project's _bmad/rds/
```

#### 4. Verify Installation

Open Claude Code in your project directory and run:

```
/bmad:core:agents:bmad-master
```

You should see the RDS module listed with 5 agents available:
- Ada (Project Architect)
- Grace (Data Scientist)
- Alan (ML Engineer)
- Marie (The Reporter)
- Tim (The Deployer)

### Quick Start

After installation, invoke agents directly:

```
/bmad:rds:agents:ada      # Start a new data science project
/bmad:rds:agents:grace    # Perform EDA and feature engineering
/bmad:rds:agents:alan     # Build and tune models
/bmad:rds:agents:marie    # Create reports and presentations
/bmad:rds:agents:tim      # Deploy models to production
```

Or use complete workflows:

```
/bmad:rds:workflows:full-lifecycle           # Complete 10-phase workflow
/bmad:rds:workflows:quick-eda                # Fast exploratory analysis
/bmad:rds:workflows:modeling-pipeline        # Build and evaluate models
```

> **Note**: The RDS module requires the R Claude Skills for full functionality. Without them, the agents will still work but won't have access to specialized R patterns and best practices.

### Troubleshooting Installation

**Skills not appearing in Claude Code:**
- Verify skills are in `~/.claude/skills/`
- Restart Claude Code
- Check skill frontmatter for syntax errors

**Module not found after installation:**
- Verify `_bmad/rds/module.yaml` exists
- Check BMAD framework version (needs v6.2.2+)
- Run `/bmad:core:agents:bmad-master` to refresh module list

**Agent commands not working:**
- Ensure you're in project root directory
- Check that `_bmad/_config/manifest.yaml` lists the RDS module
- Verify agent files exist in `_bmad/rds/agents/`

## 📊 Implementation Status

### Module Creation

The module was created through the complete BMB workflow:

✅ **Brief Mode** — Complete module specification
✅ **Create Mode** — Structure with 4 agent specs and 7 workflow specs
✅ **Validate Mode** — Compliance validation (PASS)

### Current Status

1. **Agents** ✅ COMPLETE
   - ✅ **Ada (Project Architect)** - Phases 1-3: Setup, Import, Cleaning
   - ✅ **Grace (Data Scientist)** - Phases 4-5: EDA, Feature Engineering
   - ✅ **Alan (ML Engineer)** - Phases 6-8: Modeling, Tuning, Evaluation
   - ✅ **Marie (The Reporter)** - Phase 9: Reports, Dashboards, Presentations
   - ✅ **Tim (The Deployer)** - Phase 10: Deployment, Monitoring, Production

2. **Workflows** ✅ COMPLETE
   - ✅ `full-lifecycle` (10 steps) - Complete DS lifecycle
   - ✅ `quick-eda` (4 steps) - Fast exploration
   - ✅ `modeling-pipeline` (4 steps) - Model development
   - ✅ `prototype-to-production` (5 steps) - Full deployment pipeline
   - ✅ `data-quality-check` (4 steps) - Data validation
   - ✅ `hyperparameter-optimization` (4 steps) - Advanced tuning
   - ✅ `model-interpretation` (4 steps) - Model explainability
   - ✅ `technical-report` (4 steps) - Technical documentation
   - ✅ `executive-report` (single-step) - Executive summaries
   - ✅ `build-dashboard` (4 steps) - Shiny dashboards
   - ✅ `presentation-generation` (single-step) - Slide decks
   - ✅ `deploy-model` (4 steps) - Vetiver API deployment
   - ✅ `model-monitoring` (4 steps) - Production monitoring

3. **Distribution and Installation** ✅ TESTED

   - ✅ `config.yaml` renamed to `module.yaml` (distribution standard)
   - ✅ `package.json` created with NPM metadata
   - ✅ Structure validated for local installation
   - ✅ Successfully tested in `~/Projects/test-rds-install`

## 📖 Documentation

### Module Documentation

- **[_bmad/rds/README.md](_bmad/rds/README.md)** — Module overview and quick reference
- **[_bmad/rds/TODO.md](_bmad/rds/TODO.md)** — Implementation roadmap and future plans
- **[_bmad/rds/docs/](_bmad/rds/docs/)** — Comprehensive user guides:
  - `getting-started.md` — Getting started guide
  - `agents.md` — Complete agent reference
  - `workflows.md` — Workflow documentation
  - `examples.md` — Practical examples and troubleshooting

### Repository Documentation

- **[CLAUDE.md](CLAUDE.md)** — Instructions for Claude Code
- **[docs/planning/](docs/planning/)** — Planning and preparation documents

## 🌟 What Makes This Module Unique

### Comprehensive Coverage
- **Complete 10-phase workflow**: From project setup to deployment and monitoring
- **4 specialized agents**: Each handles specific phases with deep domain expertise
- **7 production workflows**: From quick EDA to full production pipelines

### Modern R Ecosystem
- **Tidyverse-first**: Leverages dplyr, tidyr, purrr, ggplot2 for data manipulation
- **Tidymodels framework**: Unified interface for modeling with recipes, parsnip, tune, workflows
- **Quarto integration**: Professional reports, dashboards, and presentations
- **Vetiver deployment**: Seamless model deployment and monitoring

### Best Practices Built-in
- **TDD approach**: Test-driven development with testthat
- **Style compliance**: Follows tidyverse style guide
- **Performance optimization**: Profiling and benchmarking patterns
- **Reproducibility**: Version control, environments, and documentation

### Integration with Claude Code
- **20+ specialized skills**: Automatic activation based on context
- **Interactive workflows**: Step-by-step guidance through complex processes
- **Smart code generation**: Production-ready R code following best practices
- **Learning support**: Explains concepts and provides alternatives

## 📋 Status

- ✅ BMAD Framework upgraded to **v6.2.2**
- ✅ R Data Science Skills installed (20+ skills)
- ✅ RDS Module created and refactored via BMB workflows
- ✅ **5 Complete Agents**: Ada, Grace, Alan, Marie (Reporter), Tim (Deployer)
- ✅ **13 Complete Workflows**: 51 step files, comprehensive coverage
- ✅ Complete documentation with CHANGELOG
- ✅ Validation: **PASS** (100% compliance verified)
- ✅ **Distribution ready**: module.yaml + package.json v0.2.0
- ✅ **Production ready**: Full deployment and monitoring support

**Last update:** 2026-03-26 (v0.2.0 - Added Tim, refactored Marie, +6 workflows)

## 🔧 Versioning Strategy

**Versioned**:
- Documentation (CLAUDE.md, README, planning)
- **Complete RDS Module** (`_bmad/rds/`)
- **Build artifacts** (`_bmad-output/bmb-creations/`)
- Agent and workflow specs
- User documentation

**Not Versioned** (via .gitignore):
- Base BMAD Framework (_bmad/core, _bmad/bmb)
- External skills (.claude/skills/)
- Project data (data/)
- Runtime outputs
- Trained models (models/)
- Local configurations

## 📚 Resources

### Repository Documentation
- [CLAUDE.md](CLAUDE.md) — Guide for Claude Code
- [docs/planning/](docs/planning/) — Planning and preparation documents

### RDS Module Documentation
- [_bmad/rds/README.md](_bmad/rds/README.md) — Overview
- [_bmad/rds/TODO.md](_bmad/rds/TODO.md) — Roadmap
- [_bmad/rds/docs/](_bmad/rds/docs/) — Complete guides

### Build Artifacts
- [module-brief-rds.md](_bmad-output/bmb-creations/modules/module-brief-rds.md) — Complete brief (422 lines)
- [module-build-rds.md](_bmad-output/bmb-creations/modules/module-build-rds.md) — Build tracking
- [validation-report-rds-20260317.md](_bmad-output/bmb-creations/modules/validation-report-rds-20260317.md) — Validation report

### External Resources
- [BMAD Documentation](https://github.com/bmadcode/bmad-method) — Official BMAD Framework
- [R Claude Skills](https://github.com/GiulSposito/r-claude-skills) — Specialized R skills for Claude Code
- [Tidyverse](https://www.tidyverse.org/) — Data wrangling
- [Tidymodels](https://www.tidymodels.org/) — Machine learning
- [Quarto](https://quarto.org/) — Reports & dashboards
- [Vetiver](https://vetiver.rstudio.com/) — Model deployment

## 🎯 Module Architecture

**5 Specialized Agents:**
- **Ada** (🏗️) — Project Architect — Phases 1-3: Setup, Import, Cleaning
- **Grace** (🔬) — Data Scientist — Phases 4-5: EDA, Feature Engineering
- **Alan** (🤖) — ML Engineer — Phases 6-8: Modeling, Tuning, Evaluation
- **Marie** (📊) — The Reporter — Phase 9: Reports, Dashboards, Presentations
- **Tim** (🚀) — The Deployer — Phase 10: Deployment, Monitoring, Production

**13 Workflows:**
- **Complete Lifecycle:** full-lifecycle (10 steps)
- **Quick Workflows:** quick-eda, executive-report, presentation-generation
- **Modeling:** modeling-pipeline, hyperparameter-optimization, model-interpretation
- **Communication:** technical-report, build-dashboard
- **Deployment:** deploy-model, model-monitoring, prototype-to-production
- **Quality:** data-quality-check

See complete documentation at [_bmad/rds/docs/](_bmad/rds/docs/)