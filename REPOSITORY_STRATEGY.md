# Estratégia do Repositório r-bmad-data-scientist

## 🎯 Propósito

Este repositório serve como **workspace de desenvolvimento** para criar um módulo BMAD que implementa o ciclo de vida completo de projetos de Data Science em R.

## 🏗️ Arquitetura do Repositório

### Componentes Não Versionados (Dependências Externas)

#### 1. Framework BMAD (`_bmad/`)
- **Origem**: Instalação externa via BMAD installer
- **Tamanho**: ~1.3MB, 168 arquivos
- **Conteúdo**:
  - `core/`: Módulo core (bmad-master, workflows fundamentais)
  - `bmb/`: Builder module (criação de agentes, workflows, módulos)
  - `_config/`: Manifests e configurações geradas
- **Por que não versionar**: Framework é instalado/atualizado via installer oficial

#### 2. R Data Science Skills (`.claude/skills/`)
- **Origem**: Coleção de skills externos
- **Tamanho**: ~1.9MB, 99 arquivos
- **Conteúdo**: 20+ skills especializados (tidyverse, tidymodels, ggplot2, quarto, etc.)
- **Por que não versionar**: Skills são mantidos em repositórios separados e instalados via Claude Code

### Componentes Versionados (Desenvolvimento Próprio)

#### 1. Documentação Core
- `CLAUDE.md`: Instruções para Claude Code operar neste repositório
- `README.md`: Visão geral do projeto
- `data-science-lifecycle-framework.md`: Especificação completa das 10 fases
- `REPOSITORY_STRATEGY.md`: Este arquivo

#### 2. Módulo ds-lifecycle (FUTURO)
- `_bmad/ds-lifecycle/`: Módulo a ser criado via BMB
  - `agents/`: Agentes especializados por fase
  - `workflows/`: Workflows orquestrando as 10 fases
  - `config.yaml`: Configuração do módulo
  - `README.md`: Documentação do módulo

#### 3. Customizações e Templates
- Scripts R reutilizáveis
- Templates de projetos
- Configurações customizadas

### Componentes Gerados (Não Versionados)

#### 1. Outputs BMAD (`_bmad-output/`)
- Artefatos gerados pelos workflows
- Briefs, planos, e outputs temporários
- **Motivo**: São regeneráveis e específicos de cada execução

#### 2. Dados de Projetos (`data/`)
- Dados brutos e processados de projetos de exemplo
- **Motivo**: Podem ser sensíveis, grandes, e específicos de contexto
- **Exceção**: Amostras pequenas para exemplos (versionadas)

#### 3. Modelos Treinados (`models/`)
- Artefatos de modelos .rds, .h5, etc.
- **Motivo**: Binários grandes, regeneráveis

#### 4. Outputs de Análise (`outputs/`)
- Plots, reports HTML/PDF
- **Motivo**: Regeneráveis a partir de scripts
- **Exceção**: Figuras finais para documentação

## 📋 Workflow de Desenvolvimento

### Fase Atual: Setup e Especificação ✅

- [x] Instalação BMAD framework
- [x] Instalação R skills
- [x] Criação da especificação completa (data-science-lifecycle-framework.md)
- [x] Configuração do repositório (.gitignore, .gitattributes)
- [x] Documentação inicial (CLAUDE.md, README.md)

### Próxima Fase: Criação do Módulo ⏳

**Usando BMB Module Workflow**:

1. **Brief Mode** (B)
   ```
   /bmad:bmb:workflows:module
   → Selecionar "Brief"
   → Explorar visão do módulo ds-lifecycle
   → Definir agentes, workflows, e funcionalidades
   → Salvar brief em _bmad-output/bmb-creations/ds-lifecycle-brief.md
   ```

2. **Create Mode** (C)
   ```
   → Selecionar "Create"
   → Carregar brief
   → BMB gera estrutura completa:
     - _bmad/ds-lifecycle/config.yaml
     - _bmad/ds-lifecycle/agents/*.md
     - _bmad/ds-lifecycle/workflows/*/workflow.md
     - _bmad/ds-lifecycle/README.md
   ```

3. **Edit Mode** (E)
   ```
   → Refinar agentes individuais
   → Ajustar workflows
   → Adicionar data files e templates
   ```

4. **Validate Mode** (V)
   ```
   → Validar compliance BMAD Core
   → Verificar integridade dos agentes
   → Testar workflows
   ```

### Estrutura do Módulo ds-lifecycle (Planejado)

```
_bmad/ds-lifecycle/
├── config.yaml                     # Configuração do módulo
├── README.md                       # Documentação do módulo
│
├── agents/                         # Agentes especializados
│   ├── project-setup.md           # Fase 1: Setup
│   ├── data-inspector.md          # Fase 2: Importação/Inspeção
│   ├── data-cleaner.md            # Fase 3: Limpeza
│   ├── eda-analyst.md             # Fase 4: EDA
│   ├── feature-engineer.md        # Fase 5: Feature Engineering
│   ├── modeler.md                 # Fase 6: Modelagem
│   ├── tuner.md                   # Fase 7: Tuning
│   ├── evaluator.md               # Fase 8: Avaliação
│   ├── communicator.md            # Fase 9: Comunicação
│   └── deployer.md                # Fase 10: Deploy
│
├── workflows/                      # Workflows orquestrando fases
│   ├── full-lifecycle/            # Workflow completo de 10 fases
│   │   ├── workflow.md
│   │   └── steps/
│   │       ├── step-01-setup.md
│   │       ├── step-02-import.md
│   │       └── ...
│   │
│   ├── eda-only/                  # Workflow apenas EDA
│   ├── modeling-pipeline/         # Workflow de modelagem
│   └── quick-prototype/           # Prototipagem rápida
│
├── templates/                      # Templates reutilizáveis
│   ├── project-structure/         # Estrutura de diretórios
│   ├── renv-config/               # Configurações renv
│   ├── quarto-report/             # Templates Quarto
│   └── eda-notebook/              # Notebooks de análise
│
└── data/                           # Data files e referencias
    ├── decision-trees/            # Árvores de decisão (encoding, transformações)
    ├── checklists/                # Checklists por fase
    └── references/                # Referências técnicas
```

## 🔄 Ciclo de Atualização

### Framework BMAD
```bash
# Atualizar framework (quando nova versão disponível)
bmad update

# Isso atualiza _bmad/core e _bmad/bmb
# Não afeta customizações em _bmad/ds-lifecycle
```

### R Skills
```bash
# Skills são atualizados via Claude Code
# Configuração em .claude/settings.json
```

### Módulo ds-lifecycle
```bash
# Versionado via git normalmente
git add _bmad/ds-lifecycle
git commit -m "feat: implementa agente de EDA"
git push origin main
```

## 🚀 Distribuição do Módulo (Futuro)

Quando o módulo estiver completo, ele pode ser:

1. **Empacotado** como módulo BMAD independente
2. **Distribuído** via repositório próprio
3. **Instalado** em outros projetos via BMAD installer

```bash
# Usuário instalaria com:
bmad install ds-lifecycle
```

## 🔒 Segurança e Privacidade

### Dados Sensíveis
- `.gitignore` previne commit de:
  - Dados brutos e processados
  - Credenciais e secrets
  - Configurações locais com informações pessoais
  - Modelos treinados (podem conter dados)

### Configurações Pessoais
- `_bmad/core/config.yaml` contém `user_name` e preferências
- Não versionado, mas template pode ser compartilhado
- Cada desenvolvedor tem sua própria configuração local

### Outputs
- `_bmad-output/` pode conter informações sensíveis
- Sempre ignorado do git
- Usar cuidado ao compartilhar artefatos gerados

## 📊 Métricas do Repositório

**Framework Instalado**:
- BMAD v6.0.0-alpha.23
- Módulos: core, bmb
- Total: ~1.3MB

**Skills Instalados**:
- 20+ skills R Data Science
- Total: ~1.9MB

**Documentação**:
- CLAUDE.md: 9.7KB
- data-science-lifecycle-framework.md: 26KB
- README.md e outros: ~5KB

**Status**: Setup completo, pronto para desenvolvimento do módulo

## 🎓 Princípios de Design

1. **Separação de Responsabilidades**
   - Framework = Infraestrutura (não versionada)
   - Módulo = Lógica de negócio (versionada)
   - Skills = Conhecimento de domínio (externos)

2. **Regenerabilidade**
   - Tudo que pode ser regenerado não é versionado
   - Dados, outputs, modelos = regeneráveis
   - Código, documentação = versionados

3. **Modularidade**
   - Módulo ds-lifecycle é independente
   - Pode ser extraído e distribuído separadamente
   - Segue padrões BMAD Core

4. **Reproduzibilidade**
   - renv.lock versiona dependências R
   - BMAD manifests rastreiam versões de framework
   - Documentação clara de setup

5. **Colaboração**
   - .gitignore previne conflitos com configs locais
   - .gitattributes garante line endings consistentes
   - Documentação facilita onboarding

## 📝 Manutenção

### Revisão Periódica
- [ ] Atualizar BMAD framework (trimestral)
- [ ] Atualizar R skills (quando necessário)
- [ ] Revisar data-science-lifecycle-framework.md (anual)
- [ ] Atualizar documentação conforme módulo evolui

### Backups
- Framework e skills: reinstalável via installer
- Módulo e docs: versionados no GitHub
- Dados: backups separados (não no git)

---

**Última Atualização**: 2026-03-16
**Status**: Setup completo, pronto para desenvolvimento
**Próximo Marco**: Criar brief do módulo ds-lifecycle via BMB
