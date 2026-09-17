# IA do FlashMind Mobile (app-flashmind)

Guia de engenharia e contexto operacional específico para o aplicativo mobile Flutter do FlashMind.
O código em `lib/` e o vault de impacto em `../docs-flashmind/` são as fontes primárias de verdade.

| Para entender | Leia |
|---|---|
| **Impacto em telas ao mudar modelos** | `context/vault-de-impacto.md` → `../docs-flashmind/` |
| **Mapa de dependências da IA** | `dependency-map.md` |
| **Arquitetura, AppScope e fluxo de dados** | `context/architecture/system-overview.md` |
| **Onde cada classe e arquivo mora** | `context/conventions/project-structure.md` |
| **Estilo de código e convenções Dart** | `context/conventions/code-style.md` |
| **Regras obrigatórias do SRS** | `rules/domain/srs-algorithm.md` |
| **Regras da gamificação e streak** | `rules/domain/gamification-rules.md` |
| **Padrões de UI e temas claro/escuro** | `rules/mobile/theme-rules.md` |
| **Decisões arquiteturais registradas** | `memory/architecture-decisions.md` |
| **Fluxo para criar nova feature** | `workflows/feature-flow.md` |

## Estado Atual do Repositório

- Flutter 3.9+ / Dart com Material 3, tema claro (`#F6F7FB`) e escuro (`#0F1115`).
- Operação 100% *local-first* através de `SharedPreferences`.
- Injeção de dependência via `AppScope` (`InheritedWidget`).
- Preparado para transição para o padrão *Dual-DataSource* do Lumos quando a API backend for iniciada.

## Invariantes Inegociáveis

1. **Separação de Camadas**: `presentation → services/controllers → repositories → local storage`. Widgets nunca tocam o storage diretamente.
2. **Algoritmo SRS**: 10 passos fixos em `SpacedRepetitionService`. Não altere os intervalos de tempo sem documentação prévia.
3. **Fórmula de XP**: A progressão segue a função aritmética em `UserProgress.totalXpRequiredForLevel(level)`.
4. **Validação de Unicidade**: Baralhos não podem ter nomes duplicados (*case-insensitive*) e cartões não podem ter perguntas e respostas idênticas no mesmo deck.
5. **Consistência de Tema**: Todo widget novo deve suportar nativamente modo claro e escuro.
