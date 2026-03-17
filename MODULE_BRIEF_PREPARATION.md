# Preparação para Criação do Módulo ds-lifecycle via BMB

**Data**: 2026-03-17
**Objetivo**: Analisar o documento `data-science-lifecycle-framework.md` e preparar informações para o workflow BMB Module Brief

---

## 📊 Análise do Documento Atual

### ✅ O Que Está Bem Estruturado

1. **10 Fases Clara e Sequenciais**
   - Cada fase tem objetivo, ferramentas, ações principais, e best practices
   - Fluxo lógico de setup → deploy
   - Código executável em todas as fases

2. **Decisões Técnicas Documentadas**
   - Tabelas de decisão (ex: encoding por cardinalidade)
   - Framework de escolha (ex: modelo por tipo de problema)
   - Quando usar cada abordagem

3. **Stack Tecnológico Definido**
   - Tidyverse, Tidymodels, Quarto, Vetiver
   - Packages específicos por necessidade

4. **Princípios Fundamentais**
   - 10 princípios claros (Data Budgeting, Honest Estimation, etc.)
   - Filosofia bem articulada

5. **Checklist Prático**
   - Por fase, acionável
   - Facilita tracking de progresso

---

## 🎯 O Que o BMB Workflow Brief Precisa

Baseado na análise dos steps do BMB, o workflow vai perguntar sobre:

### 1. **Module Type** (Step 3)
- Standalone, Extension, ou Global?
- **Para ds-lifecycle**: Standalone (novo domínio independente)

### 2. **Vision** (Step 4)
- O que faz esse módulo extraordinário?
- Problema que resolve?

### 3. **Identity** (Step 5)
- Nome do módulo
- Code (kebab-case)
- Subheader/tagline
- Personalidade

### 4. **Users** (Step 6)
- Quem vai usar?
- Personas, necessidades, contexto

### 5. **Value** (Step 7)
- O que torna especial?
- Diferencial

### 6. **Agents** (Step 8) ⚠️ CRÍTICO
- Single vs multi-agent?
- Roles, responsabilidades
- Communication style
- Workflows que cada um orquestra

### 7. **Workflows** (Step 9) ⚠️ CRÍTICO
- Quais workflows o módulo oferece?
- Estrutura (steps/)
- Inputs/outputs

### 8. **Tools** (Step 10)
- MCP tools?
- Integrações externas?

### 9. **Scenarios** (Step 11)
- Casos de uso concretos
- Como usuários interagem?

### 10. **Creative** (Step 12)
- Easter eggs, lore, personalidade

---

## 🔴 Gaps Identificados no Documento Atual

### 1. **Arquitetura de Agentes NÃO Definida**

**Problema**: O documento descreve 10 fases, mas não define:
- Quantos agentes?
- Um agente por fase? (10 agentes?)
- Ou agentes com responsabilidades agregadas?
- Como agentes se relacionam?

**Impacto no BMB**: Step 8 (Agents) vai pedir essa definição!

**Sugestões de Arquitetura**:

#### Opção A: 10 Agentes Especializados (1 por fase)
```
1. project-setup      → Fase 1
2. data-inspector     → Fase 2
3. data-cleaner       → Fase 3
4. eda-analyst        → Fase 4
5. feature-engineer   → Fase 5
6. modeler            → Fase 6
7. tuner              → Fase 7
8. evaluator          → Fase 8
9. communicator       → Fase 9
10. deployer          → Fase 10
```

**Prós**: Clara separação de responsabilidades
**Contras**: Pode ser overhead para projetos pequenos

#### Opção B: 4 Agentes por Macro-Fase (Recomendado)
```
1. project-architect
   - Setup (Fase 1)
   - Import & Inspect (Fase 2)
   - Cleaning (Fase 3)
   → "Eu preparo o projeto e dados"

2. data-scientist
   - EDA (Fase 4)
   - Feature Engineering (Fase 5)
   → "Eu entendo os dados e crio features"

3. ml-engineer
   - Modeling (Fase 6)
   - Tuning (Fase 7)
   - Evaluation (Fase 8)
   → "Eu construo e otimizo modelos"

4. communicator-deployer
   - Communication (Fase 9)
   - Deploy (Fase 10)
   → "Eu apresento resultados e coloco em produção"
```

**Prós**: Balanceado, especializado mas não excessivo
**Contras**: Agentes têm múltiplas responsabilidades

#### Opção C: 1 Agente Master + Workflows
```
1. ds-lifecycle-master
   - Menu com comandos para cada fase
   - Orquestra workflows
   → "Eu guio você pelo ciclo completo"
```

**Prós**: Simples, fácil de usar
**Contras**: Menos especialização, agente pode ser "pesado"

---

### 2. **Arquitetura de Workflows NÃO Definida**

**Problema**: Documento tem 10 fases, mas não define:
- Quantos workflows?
- Um workflow por fase?
- Ou workflows agregados?
- Workflow "full-lifecycle" completo?

**Sugestões de Workflows**:

#### Workflows Principais (Recomendado)
```
1. full-lifecycle/
   - Workflow completo de 10 fases
   - steps/step-01-setup.md até step-10-deploy.md
   - Para projetos completos

2. quick-eda/
   - Fases 1-4 (setup → EDA)
   - Para exploração rápida

3. modeling-pipeline/
   - Fases 5-8 (feature eng → evaluation)
   - Para quando dados já estão limpos

4. prototype-to-production/
   - Fases 6-10 (modeling → deploy)
   - Para quando já tem features prontas

5. report-generation/
   - Apenas Fase 9 (comunicação)
   - Para criar reports de análises existentes
```

#### Workflows Especializados (Opcional)
```
6. data-quality-check/
   - Deep dive em Fase 2-3
   - Validação intensiva de dados

7. hyperparameter-optimization/
   - Deep dive em Fase 7
   - Tuning avançado

8. model-interpretation/
   - Deep dive em Fase 8
   - SHAP, LIME, etc.
```

---

### 3. **Menu Commands dos Agentes NÃO Definidos**

**Problema**: Documento não especifica:
- Que comandos cada agente oferece?
- Como usuário interage com agentes?

**Exemplo de Menu (Opção B - 4 Agentes)**:

```yaml
# project-architect.md
menu:
  - [SP] Setup Project → workflow: setup-project/
  - [II] Import & Inspect → workflow: import-inspect/
  - [CD] Clean Data → workflow: clean-data/
  - [FL] Full Lifecycle → workflow: full-lifecycle/
  - [DA] Dismiss Agent

# data-scientist.md
menu:
  - [ED] Run EDA → workflow: exploratory-analysis/
  - [FE] Feature Engineering → workflow: feature-engineering/
  - [QE] Quick EDA → workflow: quick-eda/
  - [DA] Dismiss Agent

# ml-engineer.md
menu:
  - [BM] Build Model → workflow: build-model/
  - [TM] Tune Model → workflow: tune-model/
  - [EM] Evaluate Model → workflow: evaluate-model/
  - [MP] Modeling Pipeline → workflow: modeling-pipeline/
  - [DA] Dismiss Agent

# communicator-deployer.md
menu:
  - [CR] Create Report → workflow: create-report/
  - [BD] Build Dashboard → workflow: build-dashboard/
  - [DM] Deploy Model → workflow: deploy-model/
  - [DA] Dismiss Agent
```

---

### 4. **Casos de Uso Concretos (Scenarios) Faltando**

**Problema**: Documento é técnico, mas não tem exemplos de uso narrativo

**Sugestão de Scenarios**:

```markdown
## Scenario 1: Prototipagem Rápida de Churn
Ana, cientista de dados, recebe dados de churn e precisa de um
protótipo em 2 dias.

1. Invoca project-architect → [SP] Setup Project
2. Invoca project-architect → [QE] Quick EDA
3. Invoca ml-engineer → [MP] Modeling Pipeline
4. Invoca communicator-deployer → [CR] Create Report

Tempo: 4 horas de trabalho focado, 2 dias incluindo tuning.

## Scenario 2: Pipeline Completo de Produção
João, ML Engineer, precisa criar pipeline production-ready de
previsão de demanda.

1. Invoca project-architect → [FL] Full Lifecycle
   - Sistema guia pelas 10 fases com checkpoints
   - Cada fase valida antes de prosseguir
2. No final, código pronto para CI/CD

Tempo: 2-3 semanas, código production-ready.

## Scenario 3: Exploração de Novos Dados
Maria recebeu dataset novo e quer entender antes de modelar.

1. Invoca project-architect → [II] Import & Inspect
2. Invoca data-scientist → [ED] Run EDA
3. Documento exploratório gerado via Quarto

Tempo: 4-6 horas.
```

---

### 5. **Templates e Data Files NÃO Especificados**

**Problema**: Documento descreve "o que fazer", mas não define:
- Templates reusáveis (ex: template de projeto)
- Checklists interativos
- Decision trees (ex: qual encoding usar)
- Reference files

**Sugestão de Estrutura**:

```
_bmad/ds-lifecycle/
├── templates/
│   ├── project-structure/          # Template de diretórios
│   │   ├── .gitignore
│   │   ├── .Rprofile
│   │   ├── renv.lock
│   │   └── directory-structure.txt
│   │
│   ├── quarto-reports/
│   │   ├── eda-report.qmd
│   │   ├── modeling-report.qmd
│   │   └── dashboard.qmd
│   │
│   ├── r-scripts/
│   │   ├── 01-setup.R
│   │   ├── 02-import.R
│   │   ├── ...
│   │   └── 10-deploy.R
│   │
│   └── notebooks/
│       └── exploratory-analysis.Rmd
│
├── data/
│   ├── decision-trees/
│   │   ├── encoding-strategy.md    # Quando usar dummy vs target encoding
│   │   ├── transformation-guide.md # Box-Cox vs Yeo-Johnson vs Log
│   │   ├── model-selection.md      # Que modelo para que problema
│   │   └── metric-selection.md     # Que métrica para que cenário
│   │
│   ├── checklists/
│   │   ├── setup-checklist.md
│   │   ├── eda-checklist.md
│   │   ├── modeling-checklist.md
│   │   └── deploy-checklist.md
│   │
│   └── references/
│       ├── tidymodels-quick-ref.md
│       ├── ggplot2-quick-ref.md
│       └── best-practices-summary.md
```

---

### 6. **Personalidade e Lore NÃO Definidos**

**Problema**: BMB Step 12 pergunta sobre "creative", "easter eggs", personalidade

**Sugestões**:

**Lore/Backstory**:
```
"O módulo ds-lifecycle nasceu da frustração de cientistas de dados
que refaziam os mesmos passos em cada projeto. Um grupo de 4 experts
decidiu sistematizar as melhores práticas do ecossistema R moderno
(Tidyverse + Tidymodels) em um framework executável."
```

**Personalidade dos Agentes** (Opção B):
- **project-architect**: Organizado, metódico, gosta de estrutura
- **data-scientist**: Curioso, exploratório, adora visualizações
- **ml-engineer**: Pragmático, focado em performance, gosta de métricas
- **communicator-deployer**: Claro, orientado a negócios, storyteller

**Easter Eggs** (ideias):
- Mensagens motivacionais em checkpoints
- Quotes de estatísticos famosos (Fisher, Tukey, Hadley Wickham)
- ASCII art de gráficos quando modelo atinge alta acurácia
- "Achievement unlocked" quando completa primeira fase

---

## 📝 Documento Preparatório Sugerido

Antes de rodar o BMB, sugiro criar um documento complementar:

### `ds-lifecycle-brief-prep.md`

```markdown
# ds-lifecycle Module - Brief Preparation

## Quick Reference for BMB Workflow

### Module Identity
- **Name**: Data Science Lifecycle
- **Code**: ds-lifecycle
- **Type**: Standalone Module
- **Tagline**: "10-Phase Framework for R Data Science Excellence"

### Vision
Systematize best practices from Tidyverse + Tidymodels ecosystem
into an executable, guided workflow that takes data scientists
from raw data to production deployment.

### Users
- Data Scientists using R
- ML Engineers transitioning to R
- Analysts wanting to learn production ML
- Teams wanting standardized workflows

### Value Proposition
- Elimina "blank canvas syndrome"
- Incorpora 20+ skills BMAD automaticamente
- Decisões guiadas (encoding, transformations, models)
- Production-ready code desde o início
- Reproduzível e documentado

### Agent Architecture (Opção B - Recomendada)

**4 Agentes Especializados:**

1. **Project Architect** (Ada)
   - Role: Setup, data import, cleaning
   - Workflows: setup-project, import-inspect, clean-data
   - Style: Organized, methodical, structured
   - Icon: 🏗️

2. **Data Scientist** (Grace)
   - Role: EDA, feature engineering
   - Workflows: exploratory-analysis, feature-engineering
   - Style: Curious, visual, explorative
   - Icon: 🔬

3. **ML Engineer** (Alan)
   - Role: Modeling, tuning, evaluation
   - Workflows: build-model, tune-model, evaluate-model
   - Style: Pragmatic, metric-focused, performance-oriented
   - Icon: 🤖

4. **Communicator** (Marie)
   - Role: Reports, dashboards, deployment
   - Workflows: create-report, build-dashboard, deploy-model
   - Style: Clear, business-oriented, storyteller
   - Icon: 📊

### Workflows

**Main Workflows:**
1. full-lifecycle (10 steps)
2. quick-eda (4 steps)
3. modeling-pipeline (4 steps)
4. prototype-to-production (5 steps)

**Specialized:**
5. data-quality-check
6. hyperparameter-optimization
7. model-interpretation

### Templates Needed
- Project structure template
- Quarto report templates (EDA, modeling, dashboard)
- R script templates (01-setup.R até 10-deploy.R)
- .gitignore, renv setup

### Data Files Needed
- Decision trees (encoding, transformation, model selection)
- Checklists (por fase)
- Quick references (tidymodels, ggplot2)

### Scenarios

1. **Quick Prototype**: 4h, setup → report
2. **Full Production**: 2-3 weeks, 10 fases completas
3. **EDA Only**: 4-6h, entender dados novos

### Creative Elements
- Names inspired by computing pioneers (Ada, Grace, Alan, Marie)
- Motivational messages at checkpoints
- Achievement system
- Quote database (Fisher, Hadley, etc.)
```

---

## ✅ Checklist de Preparação para BMB

Antes de invocar `/bmad:bmb:workflows:module`:

### Decisões Estratégicas (Você DEVE Decidir)

- [ ] **Module Type**: Standalone ✓ (já decidido)
- [ ] **Agent Architecture**: Quantos agentes? (sugestão: 4)
- [ ] **Workflow Structure**: Quantos workflows principais? (sugestão: 4-7)
- [ ] **Personalidade**: Nomes dos agentes? (sugestão: Ada, Grace, Alan, Marie)
- [ ] **Templates Priority**: Quais templates são críticos? (sugestão: project-structure, quarto reports)

### Informações Complementares

- [ ] **Scenarios**: 3-5 cenários de uso narrativos
- [ ] **Decision Trees**: Extrair do framework (encoding, models, metrics)
- [ ] **Checklists**: Um por fase (já tem no framework)
- [ ] **Menu Commands**: Definir por agente

### Durante o BMB Brief

- [ ] **Step 1**: Mode = Interactive (recomendado)
- [ ] **Step 3**: Type = Standalone
- [ ] **Step 8**: Usar Party Mode para simular interação entre agentes
- [ ] **Step 11**: Scenarios concretos preparados

---

## 🎯 Recomendação Final

### Abordagem Sugerida

1. **ANTES do BMB**:
   - Decidir arquitetura de agentes (sugestão: Opção B - 4 agentes)
   - Criar `ds-lifecycle-brief-prep.md` com decisões
   - Ler este documento para ter respostas prontas

2. **DURANTE o BMB**:
   - Mode = Interactive (explorar bem)
   - Step 8 (Agents): Usar Party Mode para testar interações
   - Step 11 (Scenarios): Ter 3 cenários preparados
   - Step 12 (Creative): Usar nomes Ada, Grace, Alan, Marie

3. **DEPOIS do BMB**:
   - Brief gerado em `_bmad-output/bmb-creations/`
   - Usar Create Mode para gerar estrutura
   - Implementar templates e decision trees
   - Testar workflows

---

## 📊 Resumo Executivo

**Status**: `data-science-lifecycle-framework.md` está 70% pronto para BMB

**O Que Está Ótimo**: Especificação técnica completa, código executável, princípios claros

**O Que Falta**: Arquitetura de agentes, estrutura de workflows, scenarios narrativos, templates

**Ação Recomendada**: Criar `ds-lifecycle-brief-prep.md` com decisões estratégicas antes de rodar BMB

**Tempo Estimado**:
- Prep (este doc + decisões): 1-2h
- BMB Brief (Interactive): 2-3h
- BMB Create: 30min (automatizado)
- Implementação templates/data: 1-2 dias

---

**Criado**: 2026-03-17
**Próximo Passo**: Revisar sugestões e criar `ds-lifecycle-brief-prep.md`
