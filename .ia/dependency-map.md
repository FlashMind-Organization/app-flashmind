# Mapa de Dependências — FlashMind Mobile

## Context Layer

```text
context/architecture/system-overview
  → used_by: ALL agents, ALL workflows
  → defines: AppScope, ReviewService, DeckService, UserProgressController

context/architecture/data-flow
  → used_by: agents/mobile, workflows/debugging-flow
  → depends_on: context/architecture/system-overview

context/architecture/di-map
  → used_by: agents/mobile, agents/architect
  → defines: AppScope (InheritedWidget) provendo serviços essenciais

context/stack/flutter-stack
  → used_by: agents/mobile, agents/qa
  → defines: Flutter 3.9+, Material 3, SharedPreferences, ThemeData

context/vault-de-impacto
  → used_by: ALL agents
  → points_to: ../docs-flashmind
```

## Rules Layer

```text
rules/domain/srs-algorithm
  → enforced_by: agents/qa, agents/mobile
  → specifies: 10 passos fixos, forgot (step 0), difficult (step - 2), easy (step + 1)

rules/domain/gamification-rules
  → enforced_by: agents/qa, agents/mobile
  → specifies: +5 XP / +10 XP / +15 XP, fórmula aritmética de níveis, normalização de streak

rules/mobile/state-management
  → enforced_by: agents/architect, agents/mobile
  → specifies: ChangeNotifier para serviços globais, setState local para animações e flips

rules/mobile/theme-rules
  → enforced_by: agents/qa, agents/mobile
  → specifies: Dark & Light theme compatíveis, sem cores hardcoded
```

## Agents Layer

```text
agents/mobile
  → responsible_for: implementação de widgets, telas, controllers e repositories
  → enforces: ALL rules

agents/qa
  → responsible_for: testes unitários (flutter test) e análise estática (flutter analyze)

agents/architect
  → responsible_for: evolução arquitetural, AppScope e preparação para a futura API
```

## Workflows Layer

```text
workflows/feature-flow
  → guides: criação de novo baralho, novos widgets, novos modelos

workflows/api-migration-flow
  → guides: introdução de Dual-DataSource e Dio sem quebrar a UI
```
