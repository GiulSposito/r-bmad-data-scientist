# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **BMAD (BMad Method) Data Science** repository that provides a comprehensive framework for R data scientists. It combines:

- **BMAD Core Module**: Master orchestrator, foundational workflows (brainstorming, party-mode), and task system
- **BMAD BMB Module**: Builder tools for creating agents, workflows, and complete modules
- **20+ R Data Science Skills**: Comprehensive Claude Code skills for tidyverse, tidymodels, deep learning, Bayesian stats, Shiny, Quarto, and more

**Language Configuration**: User name is "Giu", primary communication language is Portuguese, but documentation/output defaults to English. Check `_bmad/core/config.yaml` for current settings.

## Repository Structure

```
/
├── _bmad/                          # BMAD framework installation
│   ├── core/                       # Core module
│   │   ├── agents/                 # bmad-master.md
│   │   ├── workflows/              # brainstorming, party-mode, advanced-elicitation
│   │   ├── tasks/                  # index-docs.xml, shard-doc.xml, workflow.xml
│   │   └── config.yaml             # Core configuration
│   ├── bmb/                        # Builder module
│   │   ├── agents/                 # module-builder, agent-builder, workflow-builder
│   │   ├── workflows/              # module, agent, workflow (quad-modal)
│   │   └── config.yaml             # BMB configuration
│   ├── _config/                    # Installation metadata
│   │   ├── manifest.yaml           # Version 6.0.0-alpha.23, installed modules/IDEs
│   │   ├── ides/                   # claude-code.yaml
│   │   └── agents/*.customize.yaml # Agent customizations
│   └── _bmad-output/               # Output directory for generated artifacts
│
└── .claude/skills/                 # 20+ R data science skills
    ├── r-datascience/              # Tidyverse, data wrangling
    ├── r-tidymodels/               # ML with tidymodels
    ├── r-deeplearning/             # torch, keras3
    ├── r-bayes/                    # brms, Stan, Bayesian inference
    ├── r-shiny/                    # Shiny app development
    ├── quarto/                     # Quarto reports/dashboards
    ├── ggplot2/                    # Data visualization
    ├── r-timeseries/               # fable/tsibble/feasts
    ├── r-text-mining/              # tidytext, NLP
    ├── tidyverse-expert/           # dplyr, tidyr, purrr mastery
    ├── tidyverse-patterns/         # Modern tidyverse patterns
    ├── rlang-patterns/             # Metaprogramming, tidy eval
    ├── r-performance/              # Profiling, optimization
    ├── r-package-development/      # devtools, usethis, roxygen2
    ├── r-oop/                      # S3, S4, S7, vctrs
    ├── r-feature-engineering/      # Feature engineering strategies
    ├── r-style-guide/              # R coding standards
    ├── tdd-workflow/               # Test-driven development with testthat
    ├── learning-paradigms/         # ML paradigm selection
    └── skillMaker/                 # Create new skills
```

## BMAD System Architecture

### Agent System

Agents are persona-driven, menu-based assistants defined in markdown with embedded XML:

- **Activation**: Multi-step sequence that loads config, sets variables, shows menu, waits for input
- **Menu System**: Numbered items with fuzzy matching, supports `action`, `exec`, `workflow` handlers
- **Configuration**: All agents load from `_bmad/{module}/config.yaml` to get `{user_name}`, `{communication_language}`, `{output_folder}`
- **Variable Interpolation**: `{project-root}`, `{installed_path}` are resolved at runtime

**Core Agents**:
- `bmad-master`: Master orchestrator, lists tasks/workflows
- `module-builder`: Create complete BMAD modules
- `agent-builder`: Build custom agents (simple, expert, module types)
- `workflow-builder`: Design structured workflows

Skills trigger agents via: `/bmad:core:agents:bmad-master` or skill number from menu.

### Workflow System

Workflows are **step-based markdown files** that guide multi-phase processes:

- **Structure**: `workflow.md` orchestrates, `steps/` contains individual step files
- **Modes**: Workflows support multiple modes (Brief/Create/Edit/Validate for module workflow)
- **Loading**: Steps load via `exec="{path}/step-N.md"` in workflow.md
- **State**: Workflows maintain state through loaded context files from `data/` directories

**Key Workflows**:
- `core/workflows/brainstorming/`: Interactive ideation with multiple techniques
- `core/workflows/party-mode/`: Multi-agent discussions
- `bmb/workflows/module/`: Quad-modal module creation (Brief→Create→Edit→Validate)
- `bmb/workflows/agent/`: Tri-modal agent creation
- `bmb/workflows/workflow/`: Tri-modal workflow creation

### Task System

Simple XML-based task definitions in `_bmad/core/tasks/*.xml`:
- `index-docs.xml`: Generate index.md for document directories
- `shard-doc.xml`: Split large markdown files by sections
- Tasks are cataloged in `_bmad/_config/task-manifest.csv`

## Working with BMAD Components

### Invoking Skills

Skills are invoked using the Skill tool with the full path format:

```
/bmad:core:agents:bmad-master          # Master orchestrator
/bmad:bmb:agents:module-builder        # Module builder agent
/bmad:bmb:workflows:module             # Module creation workflow
/bmad:core:workflows:brainstorming     # Brainstorming workflow
/bmad:core:tasks:index-docs            # Index docs task
```

Or from the bmad-master menu by number or fuzzy text match.

### Configuration Files

**Never modify config files directly without understanding impact:**

- `_bmad/core/config.yaml`: Core settings (user_name, communication_language, output_folder)
- `_bmad/bmb/config.yaml`: BMB settings (inherits from core, adds bmb_creations_output_folder)
- `_bmad/_config/manifest.yaml`: Installation metadata (version, modules, IDEs)

**Reading config is MANDATORY** in agent activation step 2 before any output.

### Creating New Components

**Agents**: Use `/bmad:bmb:agents:agent-builder` workflow
- Choose type: Simple (basic menu), Expert (deep domain knowledge), or Module (menu + handlers)
- Define persona (role, identity, communication_style, principles)
- Build activation sequence and menu structure

**Workflows**: Use `/bmad:bmb:workflows:workflow` workflow
- Design step architecture (steps/ directory)
- Create workflow.md orchestrator
- Add data files (data/ directory) for context/templates

**Modules**: Use `/bmad:bmb:workflows:module` workflow
- Start with Brief mode to explore module vision
- Create mode builds complete structure from brief
- Includes agents/, workflows/, config.yaml, README.md

### Agent Architecture Types

1. **Simple Agent**: Menu-driven with inline actions or exec handlers
2. **Expert Agent**: Rich persona, specialized knowledge, comprehensive menu with multi-modal workflows
3. **Module Agent**: Part of a larger module, coordinates workflows and resources

All agents follow XML-based structure with `<agent>`, `<activation>`, `<persona>`, `<menu>` sections.

## R Data Science Skills

This repository includes 20+ comprehensive R skills loaded in Claude Code. They provide:

- **Code patterns**: Production-ready R code for common tasks
- **Best practices**: Tidyverse style, performance optimization, testing
- **Templates**: Starter code for Shiny apps, Quarto reports, torch models, etc.
- **Activation triggers**: Skills auto-load when relevant keywords/imports detected

Skills are for **guidance only** - no actual R code is executed in this repository. They inform Claude when writing R code for data science projects.

## Key Principles

1. **Runtime Loading**: Never preload resources. Load files only when workflows execute or commands require them (exception: config.yaml in step 2)
2. **Variable Interpolation**: Always resolve `{project-root}`, `{user_name}`, `{communication_language}`, etc. from loaded config
3. **Menu-First Design**: Agents present menus, wait for user input, never auto-execute
4. **Step-Based Workflows**: Workflows are orchestrated sequences that load steps on-demand
5. **Communication Language**: Respect `{communication_language}` from config (default: Portuguese) unless workflow specifies otherwise
6. **Modular Architecture**: Modules are self-contained (agents, workflows, tasks, config) yet integrate seamlessly

## File Path Conventions

- `{project-root}`: Repository root (`/Users/gsposito/Projects/r-bmad-data-scientist`)
- `{installed_path}`: Resolved to actual module installation path
- `_bmad-output/`: All generated artifacts go here
- `_bmad-output/bmb-creations/`: BMB workflow outputs (briefs, modules, agents)

## Version Information

- **BMAD Version**: 6.0.0-alpha.23
- **Installed Modules**: core, bmb
- **IDE Integration**: claude-code
- **Installation Date**: 2026-03-17

## Important Notes

- This is a **framework repository**, not an R package or data science project
- No R code is executed here - this repo provides skills/agents/workflows for use in actual R projects
- The `_bmad/` directory structure is managed by BMAD installer - modifications should go through proper workflows
- Agent activation sequences are critical - follow them exactly, especially config loading in step 2
- Workflows are multi-phase and stateful - don't skip steps or improvise
