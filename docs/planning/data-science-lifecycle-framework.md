# 🔬 Ciclo de Vida de Projetos de Ciência de Dados em R - Framework Completo

**Baseado em 20+ Skills BMAD para R Data Science**

**Autor**: Análise profunda dos skills instalados
**Data**: 2026-03-16
**Versão**: 1.0

---

## 📋 Visão Geral do Ciclo

```
┌─────────────────────────────────────────────────────────────┐
│  CICLO DE VIDA - DATA SCIENCE EM R (Tidyverse + Tidymodels) │
└─────────────────────────────────────────────────────────────┘

1. SETUP & PLANEJAMENTO          [Estrutura, Deps, Docs]
2. IMPORTAÇÃO & INSPEÇÃO         [Importar, Glimpse, Summary]
3. LIMPEZA & WRANGLING          [Tidyr, Dplyr, Missings]
4. ANÁLISE EXPLORATÓRIA (EDA)   [Visualização, Estatísticas]
5. FEATURE ENGINEERING          [Transformações, Encoding, Interações]
6. MODELAGEM                    [Split, Recipe, Model, Workflow]
7. TUNING & VALIDAÇÃO          [CV, Grid Search, Métricas]
8. AVALIAÇÃO FINAL             [Test Set, Diagnóstico, Interpretação]
9. COMUNICAÇÃO                  [Quarto, Dashboards, Reports]
10. DEPLOY & MONITORAMENTO      [Vetiver, APIs, Tracking]
```

---

## 📊 FASE 1: Setup & Planejamento

### Objetivo
Estruturar o projeto de forma reproduzível, escalável e colaborativa

### Ferramentas
- **Organização**: Estrutura de diretórios (data/, scripts/, outputs/, docs/)
- **Dependências**: `renv` para controle de versões de pacotes
- **Versionamento**: Git + GitHub
- **Documentação inicial**: README.md, projeto R (.Rproj)

### Ações Principais
```r
# Criar estrutura de projeto
usethis::create_project("meu-projeto-ds")

# Controle de dependências
renv::init()

# Git
usethis::use_git()
usethis::use_github()

# Estrutura de diretórios
fs::dir_create(c("data/raw", "data/processed",
                  "scripts", "outputs", "docs"))
```

### Best Practices
✅ Use `.Rproj` para gerenciar working directory
✅ Configure `renv` logo no início
✅ Crie `README.md` descrevendo objetivo e estrutura
✅ Use `.gitignore` para dados sensíveis
✅ Defina `seed` global para reproduzibilidade

---

## 📥 FASE 2: Importação & Inspeção

### Objetivo
Carregar dados e fazer inspeção inicial para entender estrutura, tipos e qualidade

### Ferramentas
- **Importação**: `readr`, `readxl`, `haven`, `vroom` (grandes datasets)
- **Inspeção**: `glimpse()`, `summary()`, `skimr::skim()`, `visdat::vis_dat()`

### Ações Principais
```r
library(tidyverse)
library(skimr)

# Importar
df_raw <- read_csv("data/raw/dataset.csv")

# Inspeção estrutural
glimpse(df_raw)
skim(df_raw)

# Inspeção visual de dados faltantes
naniar::vis_miss(df_raw)
visdat::vis_dat(df_raw)

# Estatísticas descritivas
summary(df_raw)
```

### O Que Observar
- Tipos de variáveis (numeric, character, factor, date)
- Distribuição de missings (padrões? MAR, MCAR, MNAR?)
- Valores fora do esperado (outliers, impossíveis)
- Cardinalidade de categóricas
- Ranges de variáveis numéricas

---

## 🧹 FASE 3: Limpeza & Data Wrangling

### Objetivo
Transformar dados brutos em dados limpos, estruturados e prontos para análise

### Ferramentas
- **Manipulação**: `dplyr` (filter, select, mutate, summarize, arrange)
- **Reshape**: `tidyr` (pivot_longer, pivot_wider, separate, unite)
- **Strings**: `stringr`
- **Datas**: `lubridate`
- **Categóricas**: `forcats`

### Ações Principais
```r
df_clean <- df_raw %>%
  # Filtrar casos problemáticos
  filter(!is.na(key_variable)) %>%
  filter(age > 0, age < 120) %>%

  # Renomear variáveis
  rename(customer_id = id) %>%

  # Criar/modificar variáveis
  mutate(
    age_group = case_when(
      age < 18 ~ "Menor",
      age < 65 ~ "Adulto",
      TRUE ~ "Idoso"
    ),
    date = ymd(date_string),
    month = month(date),
    year = year(date)
  ) %>%

  # Lidar com categóricas
  mutate(
    category = fct_lump_n(category, n = 10),  # Agrupa raras
    category = fct_infreq(category)            # Ordena por freq
  ) %>%

  # Remover duplicatas
  distinct() %>%

  # Ordenar
  arrange(date, customer_id)
```

### Best Practices
✅ **Documente decisões**: Por que removeu casos? Que critérios usou?
✅ **Preserve raw**: Nunca sobrescreva dados originais
✅ **Pipeline legível**: Use pipe `%>%` ou `|>` para clareza
✅ **Valide joins**: Use `anti_join()` para detectar problemas
✅ **SEMPRE** `ungroup()` após operações agrupadas

---

## 📊 FASE 4: Análise Exploratória de Dados (EDA)

### Objetivo
Entender distribuições, relações, padrões e formular hipóteses

### Ferramentas
- **Visualização**: `ggplot2` (grammar of graphics)
- **Paletas**: `viridis` (colorblind-safe)
- **Tabelas**: `gt`, `knitr::kable()`
- **Correlações**: `corrr`, `GGally::ggpairs()`

### Ações Principais

**Univariadas (Distribuições)**:
```r
# Numéricas - Histogramas/Density
ggplot(df_clean, aes(x = age)) +
  geom_histogram(binwidth = 5, fill = "steelblue") +
  theme_minimal()

# Categóricas - Barplots
df_clean %>%
  count(category, sort = TRUE) %>%
  ggplot(aes(x = fct_reorder(category, n), y = n)) +
  geom_col(fill = "coral") +
  coord_flip() +
  theme_minimal()
```

**Bivariadas (Relações)**:
```r
# Numérica vs Numérica - Scatterplot
ggplot(df_clean, aes(x = age, y = salary)) +
  geom_point(alpha = 0.5) +
  geom_smooth(method = "loess") +
  theme_minimal()

# Categórica vs Numérica - Boxplot/Violin
ggplot(df_clean, aes(x = category, y = value)) +
  geom_violin(fill = "lightblue") +
  geom_boxplot(width = 0.1, alpha = 0.5) +
  theme_minimal()

# Correlações
library(GGally)
df_clean %>%
  select(where(is.numeric)) %>%
  ggpairs()
```

**Multivariadas**:
```r
# Faceting por categoria
ggplot(df_clean, aes(x = x, y = y, color = outcome)) +
  geom_point() +
  facet_wrap(~group) +
  scale_color_viridis_d() +
  theme_minimal()
```

### O Que Buscar
- **Outliers**: Valores extremos que podem distorcer modelos
- **Skewness**: Assimetria (considerar transformações)
- **Relações não-lineares**: Podem precisar de polinômios/splines
- **Interações**: Variáveis com efeito diferente em subgrupos
- **Multicolinearidade**: Variáveis muito correlacionadas

### Best Practices
✅ Use **paletas colorblind-safe** (Viridis)
✅ **Rotule diretamente** gráficos (evite legendas complexas)
✅ Sempre defina **binwidth** explicitamente em histogramas
✅ Use `coord_cartesian()` para zoom (preserva dados)
✅ Agregue antes de plotar datasets grandes

---

## ⚙️ FASE 5: Feature Engineering

### Objetivo
Re-representar dados para maximizar poder preditivo dos modelos

### Framework de Decisão (baseado em "Feature Engineering and Selection" - Max Kuhn)

#### 5.1 Missing Data

**Estratégia depende do padrão e proporção**:

```r
# Imputação simples (< 5% missing, MCAR)
step_impute_median(all_numeric_predictors())
step_impute_mode(all_nominal_predictors())

# Imputação sofisticada (5-20% missing)
step_impute_knn(all_predictors(), neighbors = 5)
step_impute_bag(all_predictors())  # Bagged trees

# Missing como informação (> 20% ou MNAR)
step_indicate_na(all_predictors())  # Cria flag de missing
```

#### 5.2 Encoding de Categóricas

**Decisão por cardinalidade**:

```r
# Baixa cardinalidade (< 10 níveis)
step_dummy(all_nominal_predictors())

# Média cardinalidade (10-50 níveis) + supervised
embed::step_lencode_mixed(categoria, outcome = vars(target))

# Alta cardinalidade (> 50 níveis)
embed::step_embed(categoria, outcome = vars(target), num_terms = 5)
# OU
textrecipes::step_texthash(categoria, num_terms = 64)
```

**Ordem crítica**:
```r
recipe(outcome ~ .) %>%
  step_novel(all_nominal_predictors()) %>%  # ANTES de dummy!
  step_dummy(all_nominal_predictors()) %>%
  step_zv(all_predictors())  # DEPOIS de dummy
```

#### 5.3 Transformações Numéricas

**Decisão por tipo de modelo e distribuição**:

```r
# Tree-based (RF, XGBoost): NENHUMA transformação necessária

# Linear/SVM/KNN: SEMPRE normalizar
step_normalize(all_numeric_predictors())

# Dados assimétricos + modelo linear
step_BoxCox(all_numeric_predictors())  # Dados positivos
step_YeoJohnson(all_numeric_predictors())  # Com zeros/negativos

# Log transform (alternativa simples para skewed)
step_log(variavel, base = 10, offset = 1)
```

#### 5.4 Criação de Features

```r
recipe(outcome ~ .) %>%
  # Interações (domain knowledge)
  step_interact(~ age:income) %>%

  # Polinômios (relações não-lineares)
  step_poly(age, degree = 2) %>%

  # Splines (flexibilidade)
  step_ns(age, deg_free = 4) %>%

  # Features de data
  step_date(date, features = c("month", "dow", "year")) %>%
  step_holiday(date, holidays = timeDate::listHolidays("US")) %>%

  # Binning (último recurso)
  step_discretize(age, num_breaks = 5)
```

#### 5.5 Detecção Sistemática de Interações

**Abordagem por tamanho do problema**:

```r
# Pequeno (< 20 features): Testar todas as combinações
library(caret)
interactions <- combn(names(df), 2, paste, collapse = ":")

# Médio (20-50): Usar importância de RF
rf_model <- ranger::ranger(outcome ~ ., data = train, importance = "permutation")
top_vars <- vip::vip(rf_model, num_features = 10)$data$Variable
interactions <- combn(top_vars, 2, paste, collapse = ":")

# Grande (>50): Two-stage (main effects → residuals)
# Fit modelo com main effects, depois testa interações nos resíduos
```

#### 5.6 Dimensionalidade Reduzida

```r
# PCA (linear, não supervisionado)
step_pca(all_numeric_predictors(), num_comp = 5)

# UMAP (não-linear, preserva estrutura local)
embed::step_umap(all_numeric_predictors(), num_comp = 2)

# Supervised (usa target)
embed::step_pls(all_numeric_predictors(), outcome = vars(target), num_comp = 5)
```

#### 5.7 Class Imbalance

```r
# Downsampling (rápido, perde dados)
themis::step_downsample(outcome)

# Upsampling (duplica minoritária)
themis::step_upsample(outcome, over_ratio = 0.5)

# SMOTE (sintético, mais sofisticado)
themis::step_smote(outcome, over_ratio = 0.8, neighbors = 5)

# Borderline-SMOTE (foca na fronteira)
themis::step_bsmote(outcome)
```

### Best Practices
✅ **SEMPRE dentro de CV**: Features derivadas de training só
✅ **Ordem importa**: novel → dummy → zv → normalize
✅ **Re-representation > complexidade**: Melhores features batem modelos complexos
✅ **Domain knowledge**: Estatística guia, mas domínio decide
✅ **Validar tudo**: Cross-validation para toda engenharia

---

## 🤖 FASE 6: Modelagem (Tidymodels Framework)

### Filosofia: 3 Fases

**Baseado em "Tidy Modeling with R" (Max Kuhn & Julia Silge)**:

1. **Foundation**: Split, recipe, model, avaliação básica
2. **Optimization**: Resampling, tuning, comparação de modelos
3. **Production**: Ensembles, interpretabilidade, deploy

### 6.1 Data Budgeting

```r
library(tidymodels)

# SEMPRE primeiro passo: split ESTRATIFICADO
set.seed(123)
split <- initial_split(df_clean, prop = 0.80, strata = outcome)
train <- training(split)
test <- testing(split)

# Resampling (para tuning/comparação)
folds <- vfold_cv(train, v = 10, strata = outcome)
```

**⚠️ CRÍTICO**: Test set só toca UMA VEZ no final!

### 6.2 Recipe (Preprocessing Pipeline)

```r
base_recipe <- recipe(outcome ~ ., data = train) %>%
  # 1. Missings
  step_impute_median(all_numeric_predictors()) %>%
  step_impute_mode(all_nominal_predictors()) %>%

  # 2. Engenharia de features
  step_mutate(age_squared = age^2) %>%
  step_interact(~ age:income) %>%

  # 3. Encoding
  step_novel(all_nominal_predictors()) %>%
  step_dummy(all_nominal_predictors()) %>%
  step_zv(all_predictors()) %>%

  # 4. Class imbalance (se necessário)
  themis::step_smote(outcome) %>%

  # 5. Transformações
  step_normalize(all_numeric_predictors())
```

### 6.3 Model Specification

```r
# Baseline: Sempre comece simples!
logistic_spec <- logistic_reg() %>%
  set_engine("glm") %>%
  set_mode("classification")

# Random Forest
rf_spec <- rand_forest(
  mtry = tune(),
  trees = 1000,
  min_n = tune()
) %>%
  set_engine("ranger", importance = "impurity") %>%
  set_mode("classification")

# XGBoost (geralmente o melhor)
xgb_spec <- boost_tree(
  trees = tune(),
  tree_depth = tune(),
  learn_rate = tune(),
  min_n = tune()
) %>%
  set_engine("xgboost") %>%
  set_mode("classification")

# Regularização (interpretável)
glmnet_spec <- logistic_reg(
  penalty = tune(),
  mixture = tune()  # 0 = ridge, 1 = lasso
) %>%
  set_engine("glmnet")
```

### 6.4 Workflow (Recipe + Model)

```r
# Workflow individual
wf <- workflow() %>%
  add_recipe(base_recipe) %>%
  add_model(rf_spec)

# OU: Workflow set (comparar múltiplos)
wf_set <- workflow_set(
  preproc = list(
    basic = basic_recipe,
    advanced = advanced_recipe
  ),
  models = list(
    logistic = logistic_spec,
    rf = rf_spec,
    xgb = xgb_spec
  ),
  cross = TRUE  # Todas as combinações
)
```

### 6.5 Seleção de Modelo por Problema

| Problema | Baseline | Produção | Quando Usar |
|----------|----------|----------|-------------|
| **Classificação balanceada** | Logistic | Random Forest, XGBoost | Acurácia > interpretabilidade |
| **Classificação desbalanceada** | SMOTE + Logistic | Weighted XGBoost | Recall/Precision críticos |
| **Regressão** | Linear | Random Forest, XGBoost | RMSE/MAE otimização |
| **Alta dimensionalidade** | Lasso | Elastic Net, XGBoost | p >> n |
| **Interpretabilidade** | Logistic/Linear + Lasso | GAM, Decision Tree | Explicabilidade > performance |
| **Séries temporais** | ARIMA | Prophet, XGBoost com lags | Dados temporais |

---

## 🎯 FASE 7: Tuning & Validação

### 7.1 Estratégias de Tuning

```r
# Grid Search (regular grid)
grid_results <- tune_grid(
  wf,
  resamples = folds,
  grid = 20,  # 20 combinações aleatórias
  metrics = metric_set(roc_auc, accuracy, sensitivity)
)

# Grid Search (space-filling)
grid_results <- tune_grid(
  wf,
  resamples = folds,
  grid = grid_latin_hypercube(size = 30),
  metrics = metric_set(roc_auc, accuracy)
)

# Bayesian Optimization (eficiente, menos avaliações)
library(finetune)
bayes_results <- tune_bayes(
  wf,
  resamples = folds,
  initial = 10,
  iter = 20,
  metrics = metric_set(roc_auc)
)

# Racing (early stopping)
race_results <- tune_race_anova(
  wf,
  resamples = folds,
  grid = 30,
  metrics = metric_set(roc_auc)
)
```

### 7.2 Comparação de Modelos

```r
# Com workflow_set
results <- wf_set %>%
  workflow_map(
    fn = "tune_grid",
    resamples = folds,
    grid = 20,
    metrics = metric_set(roc_auc, accuracy)
  )

# Ranking
rank_results(results, rank_metric = "roc_auc")

# Visualização
autoplot(results, metric = "roc_auc")
```

### 7.3 Métricas por Tipo de Problema

**Classificação Balanceada**:
- Accuracy, ROC-AUC, F1-score

**Classificação Desbalanceada**:
- PR-AUC (Precision-Recall), Sensitivity, Specificity
- F1-score (balance precision/recall)

**Regressão**:
- RMSE (penaliza outliers)
- MAE (robusta a outliers)
- R² (proporção de variância explicada)

```r
# Definir métricas customizadas
custom_metrics <- metric_set(
  roc_auc,
  pr_auc,      # Para imbalance
  sensitivity,
  specificity,
  f_meas       # F1-score
)
```

### Best Practices
✅ **Múltiplas métricas**: Não confie só em accuracy
✅ **Stratified CV**: Sempre `strata = outcome`
✅ **Seed fixo**: Reproduzibilidade
✅ **Não tune no test**: Use CV para tuning, test só no final
✅ **Visualize tuning**: `autoplot()` mostra trade-offs

---

## 📈 FASE 8: Avaliação Final

### 8.1 Finalização do Modelo

```r
# Selecionar melhor configuração
best_params <- select_best(grid_results, metric = "roc_auc")

# Finalizar workflow
final_wf <- finalize_workflow(wf, best_params)

# Fit final no train + avaliar no test (UMA VEZ!)
final_fit <- last_fit(final_wf, split)

# Métricas finais
collect_metrics(final_fit)
```

### 8.2 Diagnóstico Completo

```r
# Extrair predições
predictions <- collect_predictions(final_fit)

# Confusion Matrix
conf_mat(predictions, truth = outcome, estimate = .pred_class)

# Curvas ROC e PR
predictions %>%
  roc_curve(truth = outcome, .pred_Yes) %>%
  autoplot()

predictions %>%
  pr_curve(truth = outcome, .pred_Yes) %>%
  autoplot()

# Calibração de probabilidades
library(probably)
cal_plot_breaks(predictions, truth = outcome, estimate = .pred_Yes)
```

### 8.3 Interpretabilidade

```r
# Variable Importance
library(vip)

final_fit %>%
  extract_fit_parsnip() %>%
  vip(num_features = 20)

# SHAP values (XGBoost)
library(SHAPforxgboost)
shap_values <- shap.values(
  xgb_model = extract_fit_engine(final_fit),
  X_train = train_matrix
)
shap.plot.summary(shap_values)

# Partial Dependence Plots
library(pdp)
partial(final_fit, pred.var = "age", plot = TRUE)
```

### 8.4 Threshold Optimization (Classificação)

```r
# Otimizar threshold para maximizar F1
threshold_results <- predictions %>%
  threshold_perf(
    truth = outcome,
    estimate = .pred_Yes,
    thresholds = seq(0.1, 0.9, by = 0.05),
    metrics = metric_set(j_index, f_meas, sens, spec)
  )

# Melhor threshold
best_threshold <- threshold_results %>%
  filter(.metric == "f_meas") %>%
  filter(.estimate == max(.estimate)) %>%
  pull(.threshold)
```

### 8.5 Checklist de Validação

✅ **Performance generaliza?** CV ≈ Test performance
✅ **Sem overfitting?** Train >> Test = overfitting
✅ **Calibração OK?** Probabilidades próximas de frequências
✅ **Features importantes fazem sentido?** Domain knowledge check
✅ **Funciona em subgrupos?** Avaliar por segmentos críticos
✅ **Métricas de negócio atendidas?** Não só métricas técnicas

---

## 📊 FASE 9: Comunicação & Documentação

### 9.1 Quarto Reports (Framework Recomendado)

**Estrutura de um Report Completo**:

```yaml
---
title: "Análise Preditiva de Churn"
author: "Giu"
date: today
format:
  html:
    toc: true
    code-fold: true
    theme: cosmo
execute:
  warning: false
  message: false
---
```

```markdown
## Executive Summary

<!-- KPIs principais, decisões recomendadas -->

## Objetivo e Metodologia

<!-- Problema de negócio, approach técnico -->

## Análise Exploratória

```{r}
#| label: eda
#| fig-cap: "Distribuição das principais variáveis"

# Visualizações EDA
```

## Feature Engineering

<!-- Decisões sobre transformações, encoding, etc. -->

## Modelagem

```{r}
#| label: results
#| tbl-cap: "Comparação de Modelos"

# Tabela de resultados
```

## Resultados e Interpretação

<!-- Variable importance, insights de negócio -->

## Recomendações

<!-- Ações práticas baseadas no modelo -->

## Próximos Passos

<!-- Deploy, monitoramento, melhorias -->
```

### 9.2 Dashboards Interativos

```yaml
---
title: "Dashboard de Performance do Modelo"
format: dashboard
---

# Overview

## Row

```{r}
#| content: valuebox
#| title: "Accuracy"
list(
  value = "87.5%",
  color = "success"
)
```

```{r}
#| content: valuebox
#| title: "AUC-ROC"
list(
  value = "0.92",
  color = "primary"
)
```

## Row

```{r}
#| title: "Confusion Matrix"
conf_mat_plot
```

```{r}
#| title: "Feature Importance"
vip_plot
```
```

### 9.3 Visualizações Profissionais

**Princípios do skill ggplot2**:

```r
library(ggplot2)

# Theme publication-ready
theme_set(theme_minimal(base_size = 12))

# Paleta colorblind-safe
library(viridis)
scale_color_viridis_d()

# Direct labeling (melhor que legenda)
library(ggrepel)
geom_text_repel()

# Multi-panel com patchwork
library(patchwork)
(plot1 | plot2) / plot3
```

### Best Practices Comunicação
✅ **Executive summary primeiro**: Decisões antes de detalhes técnicos
✅ **Visualizações auto-explicativas**: Títulos, labels, legendas claras
✅ **Code folding**: Esconda código técnico em reports HTML
✅ **Reproduzibilidade**: Parameterized reports com Quarto
✅ **Múltiplos formatos**: HTML (interativo), PDF (print), Word (edição)

---

## 🚀 FASE 10: Deploy & Monitoramento

### 10.1 Deploy com Vetiver

```r
library(vetiver)

# Criar modelo versionado
v <- vetiver_model(final_fit, "churn_model")

# Salvar modelo
board <- pins::board_folder("models/")
vetiver_pin_write(board, v)

# API REST
library(plumber)
pr <- vetiver_api(v)
pr_run(pr, port = 8080)

# Deploy em produção (Posit Connect, Docker, etc.)
vetiver_deploy_rsconnect(
  board = board,
  name = "churn_model",
  server = "connect.company.com"
)
```

### 10.2 Monitoramento

**O que monitorar**:
- **Performance**: Métricas continuam estáveis?
- **Data Drift**: Distribuição de features mudou?
- **Concept Drift**: Relação X→Y mudou?
- **Latência**: Tempo de resposta OK?

```r
# Monitorar métricas ao longo do tempo
library(yardstick)

# Novo batch de dados
new_preds <- predict(v, new_data)

# Calcular métricas
metrics_today <- metric_set(accuracy, roc_auc)(
  data = new_preds,
  truth = outcome,
  estimate = .pred_class
)

# Comparar com baseline
# Se degradação > threshold → retreinar
```

### 10.3 Retreinamento

**Triggers para retreinamento**:
- Accuracy cai > 5%
- Data drift detectado
- Nova versão de features disponível
- Periodicidade definida (mensal, trimestral)

---

## 🎓 Princípios Fundamentais do Framework

### 1. **Data Budgeting First**
Split ANTES de qualquer análise. Test set é sagrado (toca UMA VEZ).

### 2. **Honest Estimation**
TODO preprocessing dentro de CV. Nada de fit em all data.

### 3. **Workflows Composable**
Recipe + Model = Workflow. Garante consistência.

### 4. **Re-representation > Complexity**
Melhores features batem modelos complexos.

### 5. **Start Simple, Add Complexity**
Baseline sempre. Só complexifica se necessário.

### 6. **Validate Everything**
Cross-validation para TODAS as decisões.

### 7. **Domain Knowledge + Statistics**
Estatística guia, domínio decide.

### 8. **Reproducibility**
Seed, renv, Quarto, Git. Sempre.

### 9. **Communication Matters**
Modelo que não comunica não serve.

### 10. **Monitor & Iterate**
Deploy não é o fim, é o começo.

---

## 📚 Stack Tecnológico Recomendado

```r
# Core
library(tidyverse)      # Data wrangling
library(tidymodels)     # ML workflow

# Feature Engineering
library(recipes)        # Preprocessing
library(embed)          # Advanced encoding
library(themis)         # Class imbalance

# Modeling
library(ranger)         # Random Forest
library(xgboost)        # Gradient Boosting
library(glmnet)         # Regularization

# Evaluation
library(vip)            # Variable importance
library(probably)       # Calibration

# Visualization
library(ggplot2)        # Grammar of graphics
library(patchwork)      # Multi-panel
library(ggrepel)        # Smart labels

# Communication
library(quarto)         # Reports/Dashboards
library(gt)             # Tables

# Deploy
library(vetiver)        # Model versioning/API
library(pins)           # Model storage

# Infrastructure
library(renv)           # Dependency management
```

---

## ✅ Checklist Completo do Projeto

```
☐ Setup
  ☐ .Rproj criado
  ☐ renv::init()
  ☐ Git configurado
  ☐ README.md
  ☐ Estrutura de diretórios

☐ Data
  ☐ Dados importados
  ☐ Inspeção estrutural (glimpse, skim)
  ☐ Missings analisados
  ☐ Dados limpos salvos

☐ EDA
  ☐ Distribuições univariadas
  ☐ Relações bivariadas
  ☐ Outliers identificados
  ☐ Padrões/hipóteses documentados

☐ Feature Engineering
  ☐ Estratégia de missings definida
  ☐ Encoding de categóricas
  ☐ Transformações numéricas
  ☐ Features criadas (domain knowledge)
  ☐ Recipe validado em CV

☐ Modeling
  ☐ Split estratificado (80/20)
  ☐ Baseline model criado
  ☐ Múltiplos modelos comparados
  ☐ Tuning realizado

☐ Evaluation
  ☐ Best model selecionado
  ☐ Avaliação final no test
  ☐ Diagnóstico completo
  ☐ Interpretabilidade (VIP, SHAP)
  ☐ Validação de negócio

☐ Communication
  ☐ Quarto report criado
  ☐ Visualizações profissionais
  ☐ Executive summary
  ☐ Recomendações documentadas

☐ Deploy
  ☐ Modelo versionado (vetiver)
  ☐ API criada
  ☐ Monitoramento configurado
  ☐ Plano de retreinamento
```

---

## 🎯 Resumo Executivo

Este framework representa **as melhores práticas** do ecossistema moderno de ciência de dados em R, combinando:

- **Tidyverse** para manipulação elegante de dados
- **Tidymodels** para workflows de ML rigorosos
- **Quarto** para comunicação profissional
- **Vetiver** para deploy robusto

**Tempo estimado por fase** (projeto médio):
- Setup: 1-2 horas
- Importação/Inspeção: 2-4 horas
- Limpeza: 1-2 dias
- EDA: 2-3 dias
- Feature Engineering: 2-5 dias
- Modelagem: 1-3 dias
- Tuning: 1-2 dias
- Avaliação: 1 dia
- Comunicação: 1-2 dias
- Deploy: 1-2 dias

**Total: 2-4 semanas** para projeto completo com alta qualidade.

---

## 📖 Referências Principais

1. **"Tidy Modeling with R"** - Max Kuhn & Julia Silge (https://www.tmwr.org/)
2. **"Feature Engineering and Selection"** - Max Kuhn & Kjell Johnson (https://feat.engineering/)
3. **"R for Data Science"** - Hadley Wickham & Garrett Grolemund (https://r4ds.had.co.nz/)
4. **"ggplot2: Elegant Graphics for Data Analysis"** - Hadley Wickham (https://ggplot2-book.org/)
5. **Tidymodels Documentation** - https://www.tidymodels.org/
6. **Tidyverse Documentation** - https://www.tidyverse.org/

---

## 📝 Notas

- Este framework foi derivado da análise profunda de 20+ skills BMAD instalados
- Baseado em best practices dos principais autores do ecossistema R
- Foca em reproduzibilidade, rigor estatístico e comunicação efetiva
- Adequado tanto para projetos acadêmicos quanto industriais
- Escalável de pequenos experimentos a pipelines de produção

---

**Criado**: 2026-03-16
**Fonte**: Análise dos skills BMAD r-bmad-data-scientist
**Versão**: 1.0
**Licença**: Para uso interno e educacional
