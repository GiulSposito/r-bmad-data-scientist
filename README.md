# r-bmad-data-scientist

Repositório do módulo **RDS (R Data Science)** para BMAD — um framework completo que implementa o ciclo de vida de projetos de Data Science em R, seguindo as melhores práticas do ecossistema moderno (Tidyverse + Tidymodels + Quarto + Vetiver).

## 🎯 Objetivo

Módulo BMAD que orquestra o workflow de 10 fases de Data Science em R:

1. Setup & Planejamento
2. Importação & Inspeção
3. Limpeza & Wrangling
4. Análise Exploratória (EDA)
5. Feature Engineering
6. Modelagem
7. Tuning & Validação
8. Avaliação Final
9. Comunicação
10. Deploy & Monitoramento

**Framework completo com 4 agentes e 7 workflows implementados (total de 343KB em workflows).**

## 📦 Estrutura

```
/
├── _bmad/                          # Framework BMAD
│   ├── core/                       # Módulo core + bmad-master (não versionado)
│   ├── bmb/                        # Builder para criar módulos (não versionado)
│   └── rds/                        # ✅ Módulo RDS (versionado)
│       ├── module.yaml             # Configuração do módulo (distribution format)
│       ├── package.json            # NPM package metadata
│       ├── README.md               # Documentação do módulo
│       ├── TODO.md                 # Roadmap de implementação
│       ├── agents/                 # 4 agent specs
│       │   ├── ada.spec.md         # Project Architect (Phases 1-3)
│       │   ├── grace.spec.md       # Data Scientist (Phases 4-5)
│       │   ├── alan.spec.md        # ML Engineer (Phases 6-8)
│       │   └── marie.spec.md       # Communicator (Phases 9-10)
│       ├── workflows/              # 7 workflow specs
│       │   ├── full-lifecycle/
│       │   ├── quick-eda/
│       │   ├── modeling-pipeline/
│       │   ├── prototype-to-production/
│       │   ├── data-quality-check/
│       │   ├── hyperparameter-optimization/
│       │   └── model-interpretation/
│       └── docs/                   # User documentation
│           ├── getting-started.md
│           ├── agents.md
│           ├── workflows.md
│           └── examples.md
│
├── _bmad-output/                   # Build artifacts (versionado)
│   └── bmb-creations/
│       └── modules/
│           ├── module-brief-rds.md
│           ├── module-build-rds.md
│           └── validation-report-rds-20260317.md
│
├── .claude/
│   └── skills/                     # 20+ R Data Science Skills (não versionados)
│
├── docs/
│   └── planning/                   # Documentos de planejamento e preparação
│       ├── MODULE_BRIEF_PREPARATION.md
│       ├── rds-brief-prep.md
│       ├── data-science-lifecycle-framework.md
│       ├── REPOSITORY_STRATEGY.md
│       └── SETUP_COMPLETE.md
│
├── CLAUDE.md                       # Instruções para Claude Code
└── README.md                       # Este arquivo
```

## 🚀 Como Usar

### Pré-requisitos

1. **BMAD Framework** instalado (core + bmb modules)
2. **Claude Code** com skills de R Data Science
3. **R** com tidyverse e tidymodels

### Status do Módulo RDS

O módulo foi criado através do workflow BMB completo:

✅ **Brief Mode** — Especificação completa do módulo
✅ **Create Mode** — Estrutura com 4 agents specs e 7 workflow specs
✅ **Validate Mode** — Validação de compliance (PASS)

### Próximos Passos

Status atual da implementação:

1. **Agentes** ✅ COMPLETO
   - ✅ **Ada (Project Architect)** - Phases 1-3
   - ✅ **Grace (Data Scientist)** - Phases 4-5
   - ✅ **Alan (ML Engineer)** - Phases 6-8
   - ✅ **Marie (Communicator)** - Phases 9-10

2. **Workflows** ✅ COMPLETO
   - ✅ `full-lifecycle` (10 steps, 148KB)
   - ✅ `quick-eda` (4 steps)
   - ✅ `modeling-pipeline` (4 steps, 112KB)
   - ✅ `prototype-to-production` (5 steps)
   - ✅ `data-quality-check` (4 steps)
   - ✅ `hyperparameter-optimization` (4 steps, 83KB)
   - ✅ `model-interpretation` (4 steps)

3. **Distribuição e Instalação** ✅ TESTADO

   **Preparação para Distribuição:**
   - ✅ `config.yaml` renomeado para `module.yaml` (padrão de distribuição)
   - ✅ `package.json` criado com metadados NPM
   - ✅ Estrutura validada para instalação local

   **Teste de Instalação Local:**
   ```bash
   # Em um novo projeto
   npx bmad-method install
   # Selecionar: custom module
   # Path: /caminho/para/_bmad/rds
   ```

   Instalação testada com sucesso em `~/Projects/test-rds-install`

4. **Usar o Módulo**
   ```
   /bmad:rds:agents:ada      # Project setup, import, cleaning
   /bmad:rds:agents:grace    # EDA, feature engineering
   /bmad:rds:agents:alan     # Modeling, tuning, evaluation
   /bmad:rds:agents:marie    # Communication, deployment
   ```

### Documentação do Módulo

Consulte a documentação completa em:
- **[_bmad/rds/README.md](_bmad/rds/README.md)** — Visão geral do módulo
- **[_bmad/rds/TODO.md](_bmad/rds/TODO.md)** — Roadmap de implementação
- **[_bmad/rds/docs/](_bmad/rds/docs/)** — Guias de usuário:
  - `getting-started.md` — Como começar
  - `agents.md` — Referência dos agentes
  - `workflows.md` — Referência dos workflows
  - `examples.md` — Exemplos práticos e troubleshooting

## 📋 Status

- ✅ Framework BMAD instalado (v6.0.0-alpha.23)
- ✅ Skills R Data Science instalados (20+ skills)
- ✅ Módulo RDS criado via BMB workflow
- ✅ **4 Agentes completos**: Ada, Grace, Alan, Marie
- ✅ **7 Workflows completos**: full-lifecycle (148KB), quick-eda, modeling-pipeline (112KB), prototype-to-production, data-quality-check, hyperparameter-optimization (83KB), model-interpretation
- ✅ Documentação completa (1,253 linhas)
- ✅ Validação: PASS (compliance verificado)
- ✅ **Distribuição preparada**: module.yaml + package.json
- ✅ **Instalação local testada**: Funcionando em projeto de teste

**Última atualização:** 2026-03-17

## 🔧 Estratégia de Versionamento

**Versionado**:
- Documentação (CLAUDE.md, README, preparação)
- **Módulo RDS completo** (`_bmad/rds/`)
- **Build artifacts** (`_bmad-output/bmb-creations/`)
- Agent e workflow specs
- User documentation

**Não Versionado** (via .gitignore):
- Framework BMAD base (_bmad/core, _bmad/bmb)
- Skills externos (.claude/skills/)
- Dados de projetos (data/)
- Outputs de runtime
- Modelos treinados (models/)
- Configurações locais

## 📚 Recursos

### Documentação do Repositório
- [CLAUDE.md](CLAUDE.md) — Guia para Claude Code
- [docs/planning/](docs/planning/) — Documentos de planejamento e preparação

### Documentação do Módulo RDS
- [_bmad/rds/README.md](_bmad/rds/README.md) — Visão geral
- [_bmad/rds/TODO.md](_bmad/rds/TODO.md) — Roadmap
- [_bmad/rds/docs/](_bmad/rds/docs/) — Guias completos

### Build Artifacts
- [module-brief-rds.md](_bmad-output/bmb-creations/modules/module-brief-rds.md) — Brief completo (422 linhas)
- [module-build-rds.md](_bmad-output/bmb-creations/modules/module-build-rds.md) — Build tracking
- [validation-report-rds-20260317.md](_bmad-output/bmb-creations/modules/validation-report-rds-20260317.md) — Validation report

### Recursos Externos
- [BMAD Documentation](https://github.com/bmadcode/bmad-method) — Framework BMAD oficial
- [Tidyverse](https://www.tidyverse.org/) — Data wrangling
- [Tidymodels](https://www.tidymodels.org/) — Machine learning
- [Quarto](https://quarto.org/) — Reports & dashboards
- [Vetiver](https://vetiver.rstudio.com/) — Model deployment

## 🎯 Arquitetura do Módulo

**4 Agentes Especializados:**
- **Ada** (🏗️) — Project Architect — Phases 1-3
- **Grace** (🔬) — Data Scientist — Phases 4-5
- **Alan** (🤖) — ML Engineer — Phases 6-8
- **Marie** (📊) — Communicator — Phases 9-10

**7 Workflows:**
- **Core:** full-lifecycle, quick-eda, modeling-pipeline, prototype-to-production
- **Specialized:** data-quality-check, hyperparameter-optimization, model-interpretation

Ver documentação completa em [_bmad/rds/docs/](_bmad/rds/docs/)