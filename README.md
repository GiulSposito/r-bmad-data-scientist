# r-bmad-data-scientist

Repositório para desenvolvimento de um módulo BMAD que implementa o ciclo de vida completo de projetos de Data Science em R, seguindo as melhores práticas do ecossistema moderno (Tidyverse + Tidymodels + Quarto + Vetiver).

## 🎯 Objetivo

Criar um módulo BMAD através do BMB (BMAD Builder) que orquestre o workflow de 10 fases documentado em [`data-science-lifecycle-framework.md`](data-science-lifecycle-framework.md):

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

## 📦 Estrutura

```
/
├── _bmad/                          # Framework BMAD (não versionado)
│   ├── core/                       # Módulo core + bmad-master
│   ├── bmb/                        # Builder para criar módulos
│   └── ds-lifecycle/               # FUTURO: Módulo a desenvolver
│
├── .claude/
│   └── skills/                     # R Data Science Skills (não versionados)
│
├── data/                           # Dados de projeto (não versionados)
│   ├── raw/
│   └── processed/
│
├── outputs/                        # Resultados (não versionados)
│
├── CLAUDE.md                       # Instruções para Claude Code
├── data-science-lifecycle-framework.md  # Especificação completa do ciclo
└── README.md                       # Este arquivo
```

## 🚀 Como Usar

### Pré-requisitos

1. **BMAD Framework** instalado (core + bmb modules)
2. **Claude Code** com skills de R Data Science
3. **R** com tidyverse e tidymodels

### Desenvolvimento do Módulo

O desenvolvimento seguirá o workflow BMB:

1. **Brief Mode**: Criar visão do módulo usando `/bmad:bmb:workflows:module` (modo B)
2. **Create Mode**: Construir estrutura do módulo (modo C)
3. **Edit Mode**: Refinar agentes e workflows (modo E)
4. **Validate Mode**: Validar compliance (modo V)

## 📋 Status

- ✅ Framework BMAD instalado (v6.0.0-alpha.23)
- ✅ Skills R Data Science instalados (20+ skills)
- ✅ Especificação completa documentada
- ⏳ Módulo ds-lifecycle em desenvolvimento

## 🔧 Estratégia de Versionamento

**Versionado**:
- Documentação (CLAUDE.md, framework, README)
- Customizações do módulo ds-lifecycle
- Scripts e templates desenvolvidos

**Não Versionado** (via .gitignore):
- Framework BMAD base (_bmad/core, _bmad/bmb)
- Skills externos (.claude/skills/)
- Dados sensíveis (data/)
- Outputs gerados (_bmad-output/)
- Modelos treinados (models/)
- Configurações locais

## 📚 Recursos

- [CLAUDE.md](CLAUDE.md) - Guia para Claude Code
- [data-science-lifecycle-framework.md](data-science-lifecycle-framework.md) - Framework de 10 fases
- [BMAD Documentation](https://github.com/bmadcode/bmad-method) - Framework BMAD oficial