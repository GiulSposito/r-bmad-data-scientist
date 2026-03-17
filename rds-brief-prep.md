# R Data Science Module - Brief Preparation

**Preparação para**: `/bmad:bmb:workflows:module` (Brief Mode)
**Data**: 2026-03-17
**Arquitetura Escolhida**: 4 Agentes Especializados (Opção B)
**Status**: Pronto para BMB

---

## 🎯 Quick Reference - Respostas para o BMB Workflow

Este documento contém todas as decisões estratégicas prontas para os 13 steps do BMB Brief Mode.

---

## 📋 STEP 1-2: Initial Idea & Spark

### Ideia Inicial

**Módulo para orquestrar o ciclo de vida completo de projetos de Data Science em R**, seguindo as melhores práticas do ecossistema moderno (Tidyverse + Tidymodels + Quarto + Vetiver).

### Problema que Resolve

**"Blank Canvas Syndrome"** - Data scientists enfrentam:
- Refazem os mesmos passos em cada projeto
- Decisões ad-hoc sem framework (qual encoding? qual modelo?)
- Código não reproduzível
- Dificuldade em seguir best practices
- Falta de padronização em equipes

### O Que Me Excita

Sistematizar décadas de melhores práticas (Tidyverse, Tidymodels, feature engineering do Max Kuhn) em um framework **executável** que:
- Guia decisões técnicas
- Gera código production-ready
- Integra 20+ R skills automaticamente
- Ensina enquanto executa

---

## 📦 STEP 3: Module Type

### Decisão: **Standalone Module**

**Justificativa**:
- Domínio independente (Data Science lifecycle em R)
- Não estende módulo existente
- Não é global (não afeta todo BMAD)

**Module Code**: `rds`

**Location**: `_bmad/rds/`

---

## 🌟 STEP 4: Vision

### Visão do Módulo

**"Transformar o ciclo de vida de Data Science em R de processo ad-hoc para framework executável, guiado e production-ready."**

### O Que Torna Extraordinário

1. **Decisões Guiadas**: Não apenas "faça feature engineering" — mostra QUANDO usar cada técnica
2. **Production-Ready Code**: Código gerado segue best practices desde o início
3. **Integração Profunda**: 20+ R skills BMAD automaticamente disponíveis
4. **Reproduzível**: renv, Git, Quarto desde setup
5. **Ensina Enquanto Faz**: Explica "por quê" de cada decisão

### Como Seria o Mundo Com Este Módulo

- Data scientists **começam projetos em minutos**, não horas
- Equipes **seguem padrões consistentes**
- Código **vai direto para produção** sem refatoração
- Juniors **aprendem best practices** naturalmente
- Seniors **economizam tempo** em tarefas repetitivas

---

## 🏷️ STEP 5: Identity

### Module Identity

**Name**: R Data Science
**Code**: `rds`
**Header**: "10-Phase Framework for R Data Science Excellence"
**Subheader**: "From raw data to production deployment, guided by best practices"

### Personality

**Framework**: Metódico, rigoroso, educacional
**Tone**: Professional mas acessível, ensina enquanto executa
**Style**: Estruturado, baseado em evidências (cita Kuhn, Wickham, Silge)

**Inspirações**:
- Max Kuhn & Kjell Johnson - "Feature Engineering and Selection"
- Hadley Wickham - Tidyverse philosophy
- Max Kuhn & Julia Silge - "Tidy Modeling with R"

---

## 👥 STEP 6: Users

### Primary Users

**1. Professional Data Scientists**
- Contexto: Trabalham com R, querem velocidade + qualidade
- Necessidade: Framework que não atrapalhe, mas guie decisões complexas
- Ganho: Economiza 40-60% do tempo em setup/boilerplate

**2. ML Engineers Transitioning to R**
- Contexto: Conhecem Python/sklearn, aprendendo R/tidymodels
- Necessidade: Guia claro de "como fazer X em R"
- Ganho: Acelera curva de aprendizado em 3-6 meses

**3. Data Analysts Upskilling to ML**
- Contexto: Conhecem R básico (dplyr, ggplot2), querem ML
- Necessidade: Framework estruturado que ensina conceitos
- Ganho: Path claro de analyst → data scientist

**4. Data Science Teams**
- Contexto: Múltiplos cientistas, precisam padronização
- Necessidade: Workflows consistentes, code reviews mais fáceis
- Ganho: Qualidade uniforme, onboarding mais rápido

### User Personas

**Persona 1: "Ana, a Senior Data Scientist"**
- 5+ anos de experiência
- Faz 10+ projetos/ano
- Quer: Velocidade sem sacrificar qualidade
- Pain point: Repetição cansativa de setup

**Persona 2: "João, the ML Engineer"**
- Background Python/TensorFlow
- Precisa usar R em novo projeto
- Quer: Equivalências Python ↔ R claras
- Pain point: "Como fazer isso em R?"

**Persona 3: "Maria, the Upskilling Analyst"**
- 2 anos fazendo análises descritivas
- Quer aprender ML/modelagem preditiva
- Precisa: Estrutura pedagógica
- Pain point: "Por onde começar?"

---

## 💎 STEP 7: Value Proposition

### O Que Torna Especial

**1. Decisões, Não Apenas Execução**
```
❌ Outros frameworks: "Faça feature engineering"
✅ rds: "Sua variável tem 50+ categorias? Use entity embeddings.
                 Tem 10-50? Use target encoding.
                 Tem <10? Use dummy variables."
```

**2. Production-Ready Desde o Início**
- Git setup automático
- renv para dependências
- .gitignore apropriado
- Estrutura de diretórios padrão
- Quarto para documentação

**3. Integração com R Skills Ecosystem**
- 20+ skills R BMAD automaticamente disponíveis
- Chama skills certos no momento certo
- tidymodels, ggplot2, quarto, etc.

**4. Baseado em Autoridades**
- Max Kuhn (criador tidymodels, caret)
- Hadley Wickham (criador tidyverse)
- Julia Silge (co-autora "Tidy Modeling with R")
- Não é opinião, é consenso da comunidade

**5. Ensina Enquanto Executa**
- Explica "por quê" de cada escolha
- Links para documentação aprofundada
- Cita princípios (ex: "Data Budgeting First")

### Comparação

| Feature | Manual Workflow | rds |
|---------|----------------|--------------|
| Setup tempo | 2-4 horas | 15 minutos |
| Decisões guiadas | Não | Sim (tabelas, decision trees) |
| Production-ready | Refatoração necessária | Desde o início |
| Reproduzível | Depende do cientista | Sempre (renv, Git, Quarto) |
| Padronização | Cada um faz diferente | Workflow consistente |
| Aprendizado | Trial & error | Guiado + explicações |

---

## 🤖 STEP 8: Agents Architecture

### Decisão: 4 Agentes Especializados

**Filosofia**: Especialização por macro-fase do ciclo, balanceando expertise com simplicidade.

---

### Agent 1: **Ada** - The Project Architect 🏗️

**Named After**: Ada Lovelace (primeira programadora)

**Role**: Foundation Specialist
**Responsibility**: Setup, Data Import, Data Cleaning (Fases 1-3)

**Identity**:
- Organized, methodical, structured
- "Everything has its place"
- Cares deeply about reproducibility

**Communication Style**:
- Clear, step-by-step
- Uses checklists
- Validates each step before proceeding

**Workflows Orchestrated**:
- `setup-project/` - Fase 1 completa
- `import-inspect/` - Fase 2 completa
- `clean-data/` - Fase 3 completa
- `full-lifecycle/` - Orquestra workflow completo (steps 1-10)

**Menu Commands**:
```
[SP] Setup Project       → Cria estrutura, renv, git
[II] Import & Inspect    → Importa dados, glimpse, skim, vis_miss
[CD] Clean Data          → Wrangling com dplyr/tidyr
[FL] Full Lifecycle      → Workflow completo 10 fases
[WS] Workflow Status     → Status de workflows ativos
[DA] Dismiss Agent
```

**Key Capabilities**:
- Setup de projetos R (.Rproj, renv, git)
- Estrutura de diretórios padrão
- Importação de múltiplos formatos (CSV, Excel, SPSS, etc.)
- Inspeção inicial (skimr, naniar, visdat)
- Data cleaning com tidyverse

**Sidecar Memory**: Sim
- Lembra estrutura do projeto atual
- Decisões de cleaning tomadas
- Problemas de dados identificados

---

### Agent 2: **Grace** - The Data Scientist 🔬

**Named After**: Grace Hopper (pioneira da computação)

**Role**: Exploration & Feature Specialist
**Responsibility**: EDA, Feature Engineering (Fases 4-5)

**Identity**:
- Curious, visual, explorative
- "Let the data tell the story"
- Loves patterns and correlations

**Communication Style**:
- Visual-first (gráficos antes de tabelas)
- Interprets findings
- Sugere hypotheses baseadas em padrões

**Workflows Orchestrated**:
- `exploratory-analysis/` - Fase 4 completa
- `feature-engineering/` - Fase 5 completa
- `quick-eda/` - EDA rápido (Fases 1-4 streamlined)

**Menu Commands**:
```
[ED] Run EDA             → Análise exploratória completa
[FE] Feature Engineering → Transformações, encoding, interações
[QE] Quick EDA           → EDA rápido (setup + import + EDA)
[DT] Decision Trees      → Mostra decision trees (encoding, transform)
[WS] Workflow Status
[DA] Dismiss Agent
```

**Key Capabilities**:
- EDA univariado (distribuições, outliers)
- EDA bivariado (correlações, relações)
- Visualizações com ggplot2 (colorblind-safe)
- Feature engineering com recipes
- Decision trees (qual encoding, qual transformação)

**Sidecar Memory**: Sim
- Insights de EDA
- Features criadas
- Decisões de transformação

---

### Agent 3: **Alan** - The ML Engineer 🤖

**Named After**: Alan Turing (pai da computação)

**Role**: Modeling & Optimization Specialist
**Responsibility**: Modeling, Tuning, Evaluation (Fases 6-8)

**Identity**:
- Pragmatic, performance-focused, metric-driven
- "Numbers don't lie"
- Obsessed with overfitting detection

**Communication Style**:
- Data-driven (mostra métricas sempre)
- Compara rigorosamente (CV, test set)
- Warns sobre data leakage, overfitting

**Workflows Orchestrated**:
- `build-model/` - Fase 6 completa
- `tune-model/` - Fase 7 completa
- `evaluate-model/` - Fase 8 completa
- `modeling-pipeline/` - Fases 5-8 (feature eng → evaluation)

**Menu Commands**:
```
[BM] Build Model         → Baseline + múltiplos modelos
[TM] Tune Model          → Grid search, Bayesian optimization
[EM] Evaluate Model      → Test set, diagnóstico, interpretação
[MP] Modeling Pipeline   → Feature eng + modeling + eval completo
[MS] Model Selection     → Guia de seleção de modelo
[WS] Workflow Status
[DA] Dismiss Agent
```

**Key Capabilities**:
- Model specification (parsnip)
- Workflow creation (recipe + model)
- Hyperparameter tuning (grid, Bayes, racing)
- Model evaluation (confusion matrix, ROC, PR curves)
- Interpretability (VIP, SHAP, PDPs)

**Sidecar Memory**: Sim
- Modelos testados
- Melhores hiperparâmetros
- Métricas de performance
- Test set guardado (usa UMA VEZ)

---

### Agent 4: **Marie** - The Communicator 📊

**Named After**: Marie Curie (cientista pioneira)

**Role**: Communication & Deployment Specialist
**Responsibility**: Reports, Dashboards, Deployment (Fases 9-10)

**Identity**:
- Clear, business-oriented, storyteller
- "Insights without action are worthless"
- Bridges technical ↔ business

**Communication Style**:
- Executive summary first
- Visual storytelling
- Actionable recommendations

**Workflows Orchestrated**:
- `create-report/` - Fase 9 (Quarto report)
- `build-dashboard/` - Fase 9 (Quarto dashboard)
- `deploy-model/` - Fase 10 completa
- `prototype-to-production/` - Fases 6-10 (model → deploy)

**Menu Commands**:
```
[CR] Create Report       → Quarto analytical report
[BD] Build Dashboard     → Quarto dashboard interativo
[PR] Presentation        → Quarto RevealJS slides
[DM] Deploy Model        → Vetiver API + pins
[PP] Prototype→Production → Modeling + comunicação + deploy
[WS] Workflow Status
[DA] Dismiss Agent
```

**Key Capabilities**:
- Quarto reports (HTML, PDF, Word)
- Quarto dashboards (value boxes, plots, tables)
- Quarto presentations (RevealJS)
- Model deployment (vetiver, plumber)
- Monitoring setup

**Sidecar Memory**: Sim
- Reports gerados
- Dashboards criados
- Modelos deployados
- URLs de APIs

---

### Agent Coordination

**Shared Commands** (todos os agentes):
- `[WS]` Workflow Status - Mostra status de workflows em execução
- `[DA]` Dismiss Agent - Sai do agente

**No Overlap**: Cada comando tem um único owner (agente)

**Handoffs**:
- Ada → Grace: "Dados limpos prontos para EDA"
- Grace → Alan: "Features criadas, recipe pronto"
- Alan → Marie: "Modelo avaliado, performance documentada"
- Marie → Deploy: "Report/dashboard/API prontos"

**Conversação Natural**:
```
User: "Preciso criar um modelo de churn"

Ada: "Vou começar pelo setup do projeto e importação dos dados.
      [SP] Setup Project?"

→ Após setup

Grace: "Ótimo! Agora vamos explorar os dados.
        [ED] Run EDA?"

→ Após EDA

Alan: "Insights interessantes! Pronto para modelar?
       [MP] Modeling Pipeline?"

→ Após modeling

Marie: "Modelo com 87% accuracy! Que tal um dashboard?
        [BD] Build Dashboard?"
```

---

## 🔄 STEP 9: Workflows

### Main Workflows (4)

#### 1. `full-lifecycle/`
**Purpose**: Workflow completo, 10 fases, projeto do zero até deploy
**Duration**: 2-4 semanas (projeto completo)
**Steps**: 10 (step-01-setup.md até step-10-deploy.md)
**Owner**: Ada (orquestra)
**When**: Projeto novo, production-ready necessário

```
full-lifecycle/
├── workflow.md
├── steps/
│   ├── step-01-setup.md
│   ├── step-02-import-inspect.md
│   ├── step-03-clean.md
│   ├── step-04-eda.md
│   ├── step-05-feature-engineering.md
│   ├── step-06-modeling.md
│   ├── step-07-tuning.md
│   ├── step-08-evaluation.md
│   ├── step-09-communication.md
│   └── step-10-deploy.md
└── data/
    └── phase-transitions.md
```

#### 2. `quick-eda/`
**Purpose**: Setup + Import + Clean + EDA (Fases 1-4)
**Duration**: 4-8 horas
**Steps**: 4 (streamlined)
**Owner**: Grace
**When**: Exploração rápida de dados novos, prototipagem

```
quick-eda/
├── workflow.md
├── steps/
│   ├── step-01-quick-setup.md
│   ├── step-02-import.md
│   ├── step-03-quick-clean.md
│   └── step-04-eda.md
└── templates/
    └── eda-report-template.qmd
```

#### 3. `modeling-pipeline/`
**Purpose**: Feature Engineering + Modeling + Tuning + Eval (Fases 5-8)
**Duration**: 1-2 semanas
**Steps**: 4
**Owner**: Alan
**When**: Dados já limpos, foco em otimização de modelo

```
modeling-pipeline/
├── workflow.md
├── steps/
│   ├── step-01-feature-engineering.md
│   ├── step-02-baseline-models.md
│   ├── step-03-tuning.md
│   └── step-04-evaluation.md
└── data/
    ├── model-selection-guide.md
    └── metric-selection-guide.md
```

#### 4. `prototype-to-production/`
**Purpose**: Modeling + Communication + Deploy (Fases 6-10)
**Duration**: 1-2 semanas
**Steps**: 5
**Owner**: Marie (com handoff de Alan)
**When**: Features prontas, precisa levar para produção

```
prototype-to-production/
├── workflow.md
├── steps/
│   ├── step-01-build-model.md
│   ├── step-02-tune.md
│   ├── step-03-evaluate.md
│   ├── step-04-communicate.md
│   └── step-05-deploy.md
└── templates/
    ├── deployment-checklist.md
    └── monitoring-setup.md
```

---

### Specialized Workflows (3)

#### 5. `data-quality-check/`
**Purpose**: Deep dive em qualidade de dados (Fase 3 expandida)
**Duration**: 4-8 horas
**Owner**: Ada
**When**: Dados suspeitos, muitos missings, outliers

```
data-quality-check/
├── workflow.md
├── steps/
│   ├── step-01-missing-analysis.md
│   ├── step-02-outlier-detection.md
│   ├── step-03-consistency-checks.md
│   └── step-04-remediation.md
└── data/
    └── data-quality-metrics.md
```

#### 6. `hyperparameter-optimization/`
**Purpose**: Deep dive em tuning (Fase 7 expandida)
**Duration**: 1-3 dias
**Owner**: Alan
**When**: Performance crítica, precisa squeeze máximo

```
hyperparameter-optimization/
├── workflow.md
├── steps/
│   ├── step-01-search-space.md
│   ├── step-02-bayesian-opt.md
│   ├── step-03-racing.md
│   └── step-04-ensemble.md
└── data/
    └── tuning-strategies.md
```

#### 7. `model-interpretation/`
**Purpose**: Deep dive em interpretabilidade (Fase 8 expandida)
**Duration**: 1-2 dias
**Owner**: Alan
**When**: Modelo precisa ser explicável (regulamentação, stakeholders)

```
model-interpretation/
├── workflow.md
├── steps/
│   ├── step-01-global-interpretation.md
│   ├── step-02-local-interpretation.md
│   ├── step-03-feature-importance.md
│   └── step-04-documentation.md
└── data/
    └── interpretability-methods.md
```

---

## 📁 STEP 10: Tools & Integrations

### MCP Tools

**Not Applicable**: Módulo não requer MCP tools customizados

### External Integrations

**R Packages** (declarados em workflows):
```yaml
dependencies:
  r_packages:
    - tidyverse
    - tidymodels
    - recipes
    - parsnip
    - tune
    - yardstick
    - workflows
    - ranger
    - xgboost
    - glmnet
    - vip
    - ggplot2
    - patchwork
    - quarto
    - gt
    - DT
    - vetiver
    - pins
    - renv
    - usethis
```

### Integration with R Skills

**Automatic Skills Activation**:
- Workflows mencionam keywords que ativam skills automaticamente
- Ex: "tidymodels" → r-tidymodels skill
- Ex: "ggplot2" → ggplot2 skill
- Ex: "quarto" → quarto skill

**No Custom MCP Needed**: R skills já instalados fornecem todo conhecimento

---

## 🎬 STEP 11: Scenarios

### Scenario 1: Quick Prototype (4-8 hours)

**User**: Ana, Senior Data Scientist
**Context**: Recebeu dados de churn de clientes na segunda-feira, precisa apresentar protótipo na sexta

**Journey**:

```
09:00 - Invoca Ada
        Ada: "Bom dia Ana! Novo projeto?"
        Ana: "Sim, análise de churn. Tenho CSV com 50k clientes."
        Ada: "[SP] Setup Project"
        → Cria estrutura, renv, git em 15min

09:20 - Ada: "Projeto pronto! [II] Import & Inspect?"
        → Importa dados, mostra glimpse, identifica 3 variáveis com missings

09:40 - Ada: "15% missings em 'income'. Estratégia?"
        Ana: "Imputação mediana"
        Ada: "[CD] Clean Data"
        → Aplica cleaning, valida resultado

10:00 - Grace entra: "Dados limpos! [QE] Quick EDA?"
        → Gera EDA automático: distribuições, correlações, insights
        → Output: eda-report.html

11:30 - Grace: "Clientes com >3 suportes têm 5x mais churn!"
        Alan entra: "Interessante! [MP] Modeling Pipeline?"
        → Cria features, testa 3 modelos, tune melhor

14:00 - Alan: "XGBoost: 87% accuracy, 0.91 AUC-ROC"
        Marie entra: "[BD] Build Dashboard?"
        → Dashboard com KPIs, confusion matrix, top features

15:30 - Marie: "Dashboard pronto! Quer apresentar?"
        Ana: "Perfeito! Vou revisar"
```

**Total**: 6.5 horas, protótipo production-ready

**Key Moments**:
- Ada identifica missings automaticamente
- Grace sugere insights de EDA
- Alan compara 3 modelos rigorosamente
- Marie cria dashboard apresentável

---

### Scenario 2: Full Production Pipeline (2-3 weeks)

**User**: João, ML Engineer (background Python)
**Context**: Projeto estratégico, modelo de previsão de demanda para produção

**Journey**:

```
Week 1 - Foundation
Day 1-2: Ada [FL] Full Lifecycle (steps 1-3)
         → Setup, import histórico 2 anos, cleaning profundo

Day 3-4: Grace [ED] Run EDA
         → Análise de sazonalidade, trends, outliers
         → Documento de 30 páginas de insights

Day 5: Grace [FE] Feature Engineering
       → Lags, rolling stats, holiday effects
       → 47 features criadas

Week 2 - Modeling
Day 1-3: Alan [BM] Build Model
         → Testa: linear, RF, XGBoost, prophet
         → Time series CV (rolling origin)

Day 4-5: Alan [TM] Tune Model
         → Bayesian optimization, 50 iterações
         → Best: XGBoost com features de lag

Week 3 - Production
Day 1: Alan [EM] Evaluate Model
       → Walk-forward validation
       → RMSE, MAE, MAPE aceitáveis
       → SHAP para interpretação

Day 2-3: Marie [CR] Create Report
         → Report técnico (30 páginas)
         → Executive summary (2 páginas)

Day 4: Marie [DM] Deploy Model
       → Vetiver API
       → Docker container
       → Monitoring setup

Day 5: João: Code review, CI/CD setup
```

**Total**: 3 semanas, production-ready, documentado, deployado

**Key Moments**:
- Ada setup completo (renv, Git, structure)
- Grace identifica sazonalidade complexa
- Alan aplica time series CV (critical para temporal data)
- Marie gera docs técnico + executivo + deploy

---

### Scenario 3: EDA-Only Exploration (4-6 hours)

**User**: Maria, Data Analyst (upskilling to ML)
**Context**: Dataset novo de vendas, precisa entender antes de propor análise

**Journey**:

```
10:00 - Invoca Grace
        Grace: "Olá Maria! Novo dataset?"
        Maria: "Sim, vendas de 5 lojas, 100k transações"
        Grace: "Vamos explorar! Já tem projeto?"
        Maria: "Não ainda"

10:05 - Grace chama Ada: "Ada, [SP] quick setup?"
        Ada: "Claro! Nome do projeto?"
        Maria: "sales-exploration"
        Ada: → Setup rápido (5min)

10:10 - Grace: "[II] Import & Inspect"
        → Importa, mostra estrutura
        Grace: "Vejo 7 variáveis. Quer [ED] Run EDA completo?"
        Maria: "Sim!"

10:15 - Grace executa EDA
        → Univariado: distribuições de valor, quantidade, loja
        → Bivariado: valor vs loja, temporal patterns
        → Correlações: identifica 3 correlações fortes

12:00 - Grace: "Achei padrões interessantes!"
        → Loja 3 tem 2x mais vendas aos finais de semana
        → Categoria 'eletrônicos' tem ticket médio 3x maior
        → Pico de vendas em dezembro (óbvio, mas confirmado)

12:30 - Grace: "[CR] Create Report para documentar?"
        Marie entra: "Vou gerar um report lindo!"
        → eda-sales-exploration.html criado

13:00 - Maria: "Perfeito! Agora sei que análise propor"
```

**Total**: 3 horas, insights acionáveis, documentado

**Key Moments**:
- Grace coordena com Ada para setup rápido
- EDA revela padrões não-óbvios
- Marie gera report apresentável
- Maria aprendeu workflow EDA estruturado

---

### Scenario Summary

| Scenario | Duration | Users | Workflows | Output |
|----------|----------|-------|-----------|--------|
| Quick Prototype | 4-8h | Seniors em deadline | quick-eda + modeling-pipeline | Protótipo + dashboard |
| Full Production | 2-3 weeks | ML Engineers | full-lifecycle | Código production + deploy |
| EDA Exploration | 3-6h | Analysts learning | quick-eda | Insights + report |

---

## ✨ STEP 12: Creative Elements

### Module Lore

**Origin Story**:
> "In 2024, four legendary data scientists—frustrated by repeating the same workflows in every project—decided to encode their collective wisdom into an executable framework. They systematized the best practices from decades of R evolution: from S-PLUS to modern Tidyverse, from ad-hoc modeling to rigorous Tidymodels. The result? A framework where data science is not trial-and-error, but guided discovery."

### Agent Personalities

**Ada Lovelace** 🏗️
- **Catchphrase**: "Structure enables creativity"
- **Quote**: "A good foundation is half the model"
- **Quirk**: Uses building metaphors ("laying foundation", "scaffolding")

**Grace Hopper** 🔬
- **Catchphrase**: "Let the data speak"
- **Quote**: "If you don't visualize, you're flying blind"
- **Quirk**: Shows excitement with ASCII plots

**Alan Turing** 🤖
- **Catchphrase**: "Trust metrics, not intuition"
- **Quote**: "Overfitting is the enemy of generalization"
- **Quirk**: Warns aggressively about data leakage

**Marie Curie** 📊
- **Catchphrase**: "Science without communication is incomplete"
- **Quote**: "An insight not shared is an insight wasted"
- **Quirk**: Always asks "How would you explain this to your CEO?"

### Easter Eggs

**Achievement System**:
```
🏆 "First Steps" - Completou primeiro setup
🏆 "Data Detective" - Encontrou 5+ insights em EDA
🏆 "Feature Wizard" - Criou 20+ features
🏆 "Model Master" - Modelo com >90% accuracy
🏆 "Production Pro" - Primeiro deploy bem-sucedido
🏆 "Lifecycle Legend" - Completou workflow full-lifecycle
```

**Quote Database** (mostra aleatoriamente):
```
"The best thing about being a statistician is that you get to play in everyone's backyard." - John Tukey

"Far better an approximate answer to the right question than an exact answer to the wrong question." - John Tukey

"The data may not contain the answer. The combination of some data and an aching desire for an answer does not ensure that a reasonable answer can be extracted from a given body of data." - John Tukey

"Make your code readable. Spend time on names." - Hadley Wickham

"You can't do data science in a GUI." - Hadley Wickham

"Feature engineering is the key. Models are commodities." - Andrew Ng

"Applied statistics is about reducing uncertainty." - Max Kuhn
```

**ASCII Art** (quando modelo atinge >90% accuracy):
```
    ⭐ OUTSTANDING MODEL ⭐

     📈 Accuracy: 92.5%

    ╔══════════════════╗
    ║   GREAT WORK!    ║
    ╚══════════════════╝
```

**Hidden Commands**:
- `[XX]` Show Achievement Progress
- `[QQ]` Random Quote
- `[EE]` Easter Egg Hunt (mostra lista de easter eggs)

### Workflow Celebrations

**On Completing full-lifecycle**:
```
🎉 CONGRATULATIONS! 🎉

You just completed the entire Data Science Lifecycle!

From raw data to production deployment, you followed
best practices every step of the way.

📊 Summary:
   - Setup: ✅
   - Data Quality: ✅
   - EDA Insights: ✅
   - Features Created: ✅
   - Model Performance: ✅
   - Report Generated: ✅
   - Production Deployed: ✅

🏆 Achievement Unlocked: "Lifecycle Legend"

"The journey of a thousand models begins with a single seed."
- Ancient Data Science Proverb
```

---

## 📂 Templates & Data Files

### Templates Directory Structure

```
_bmad/rds/templates/
├── project-structure/
│   ├── .gitignore
│   ├── .Rprofile
│   ├── README.template.md
│   ├── renv.lock.template
│   └── directory-structure.txt
│
├── quarto-reports/
│   ├── eda-report.qmd
│   ├── modeling-report.qmd
│   ├── executive-summary.qmd
│   └── dashboard.qmd
│
├── r-scripts/
│   ├── 01-setup.R
│   ├── 02-import.R
│   ├── 03-clean.R
│   ├── 04-eda.R
│   ├── 05-feature-engineering.R
│   ├── 06-modeling.R
│   ├── 07-tuning.R
│   ├── 08-evaluation.R
│   ├── 09-reporting.R
│   └── 10-deploy.R
│
└── notebooks/
    ├── exploratory-analysis.Rmd
    └── feature-engineering.Rmd
```

### Data Directory Structure

```
_bmad/rds/data/
├── decision-trees/
│   ├── encoding-strategy.md
│   ├── transformation-guide.md
│   ├── model-selection.md
│   ├── metric-selection.md
│   └── imbalance-strategies.md
│
├── checklists/
│   ├── setup-checklist.md
│   ├── import-checklist.md
│   ├── cleaning-checklist.md
│   ├── eda-checklist.md
│   ├── feature-eng-checklist.md
│   ├── modeling-checklist.md
│   ├── tuning-checklist.md
│   ├── evaluation-checklist.md
│   ├── communication-checklist.md
│   └── deploy-checklist.md
│
├── references/
│   ├── tidymodels-quick-ref.md
│   ├── ggplot2-quick-ref.md
│   ├── dplyr-quick-ref.md
│   ├── quarto-quick-ref.md
│   └── best-practices-summary.md
│
└── principles/
    ├── data-budgeting.md
    ├── honest-estimation.md
    ├── composable-workflows.md
    └── ten-principles.md
```

---

## 🎯 STEP 13: Review & Finalize

### Module Summary

**Name**: Data Science Lifecycle
**Code**: `rds`
**Type**: Standalone Module

**Agents**: 4
- Ada (Project Architect) 🏗️
- Grace (Data Scientist) 🔬
- Alan (ML Engineer) 🤖
- Marie (Communicator) 📊

**Workflows**: 7
- Main: full-lifecycle, quick-eda, modeling-pipeline, prototype-to-production
- Specialized: data-quality-check, hyperparameter-optimization, model-interpretation

**Templates**: 15+ (project structure, Quarto, R scripts)
**Data Files**: 25+ (decision trees, checklists, references)

**Target Users**: Data Scientists, ML Engineers, Analysts
**Value**: 40-60% time savings, production-ready code, guided decisions

### Ready for BMB Create Mode

✅ All strategic decisions made
✅ Agent architecture defined
✅ Workflow structure designed
✅ Scenarios documented
✅ Templates/data planned
✅ Creative elements defined

**Next Step**: Run `/bmad:bmb:workflows:module` (Create Mode - "C") with this brief

---

## 📋 Quick Copy-Paste Answers for BMB

### For BMB Interactive Mode

**Step 1 - Initial Idea**:
> "Módulo para orquestrar o ciclo de vida completo de projetos de Data Science em R, seguindo as melhores práticas do ecossistema moderno (Tidyverse + Tidymodels). Resolve 'blank canvas syndrome' com framework executável que guia decisões técnicas e gera código production-ready."

**Step 3 - Module Type**:
> "Standalone Module. Domínio independente, não estende módulo existente."

**Step 4 - Vision**:
> "Transformar o ciclo de vida de Data Science em R de processo ad-hoc para framework executável, guiado e production-ready."

**Step 5 - Identity**:
> Name: "Data Science Lifecycle"
> Code: "rds"
> Header: "10-Phase Framework for R Data Science Excellence"

**Step 6 - Users**:
> "Data Scientists profissionais, ML Engineers transitioning to R, Data Analysts upskilling to ML, e Data Science Teams que precisam padronização."

**Step 7 - Value**:
> "Decisões guiadas (não apenas execução), production-ready desde o início, integração com 20+ R skills, baseado em autoridades (Kuhn, Wickham, Silge), ensina enquanto executa."

**Step 8 - Agents**:
> "4 agentes: Ada (Project Architect - setup/import/clean), Grace (Data Scientist - EDA/features), Alan (ML Engineer - modeling/tuning/eval), Marie (Communicator - reports/deploy)."

**Step 9 - Workflows**:
> "7 workflows: full-lifecycle (10 fases), quick-eda (4 fases), modeling-pipeline (4 fases), prototype-to-production (5 fases), + 3 especializados."

**Step 11 - Scenarios**:
> "Scenario 1: Quick Prototype (4-8h, protótipo em deadline). Scenario 2: Full Production (2-3 weeks, production-ready completo). Scenario 3: EDA Exploration (3-6h, entender dados novos)."

**Step 12 - Creative**:
> "Agentes nomeados após pioneiros (Ada Lovelace, Grace Hopper, Alan Turing, Marie Curie). Achievement system. Quote database (Tukey, Wickham, Kuhn). ASCII art em milestones."

---

**Document Status**: ✅ COMPLETE - Ready for BMB Brief Mode
**Estimated BMB Time**: 2-3 hours (Interactive Mode)
**Next Action**: `/bmad:bmb:workflows:module` → Select "B" (Brief)

**Created**: 2026-03-17
**Version**: 1.0
