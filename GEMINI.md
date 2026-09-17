# FlashMind Mobile Project Context

@.ai/INDEX.md

## Diretrizes do Aplicativo Flutter (`app-flashmind`)

Este é o aplicativo mobile do ecossistema FlashMind (Dart ^3.9, Material 3, InheritedWidget `AppScope`).
- **Fontes de Verdade**: O código em `lib/` e a documentação viva em `../docs-flashmind/`.
- **Invariantes**:
  1. Separação `presentation → controllers/services → repositories`.
  2. Algoritmo SRS baseado em 10 passos pré-definidos (`SpacedRepetitionService`).
  3. Cálculo de XP e progressão com fórmula aritmética (`UserProgress.totalXpRequiredForLevel`).
  4. Suporte simultâneo a Modo Claro e Modo Escuro em todos os widgets.
