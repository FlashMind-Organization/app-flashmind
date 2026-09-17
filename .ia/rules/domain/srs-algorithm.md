# Regra Invariante: Algoritmo de Repetição Espaçada (SRS)

## Escala Fixa de 10 Passos

Os intervalos em `SpacedRepetitionService` são canônicos:
```dart
static const reviewIntervals = [
  Duration(minutes: 1),   // Passo 0
  Duration(minutes: 5),   // Passo 1
  Duration(minutes: 15),  // Passo 2
  Duration(hours: 1),     // Passo 3
  Duration(hours: 6),     // Passo 4
  Duration(days: 1),      // Passo 5 -> Dominado (isMastered)
  Duration(days: 3),      // Passo 6
  Duration(days: 7),      // Passo 7
  Duration(days: 15),     // Passo 8
  Duration(days: 30),     // Passo 9
];
```

## Efeitos da Avaliação

1. `ReviewRating.forgot` ("Não sabia"):
   - `card.reviewStep = 0` (revisão em 1 minuto).
2. `ReviewRating.difficult` ("Difícil"):
   - `card.reviewStep = max(0, card.reviewStep - 2)` (recua 2 passos).
3. `ReviewRating.easy` ("Fácil"):
   - `if (card.reviewStep < 9) card.reviewStep++` (avança 1 passo).

## Definição de Estados

- `isDue`: `nextReviewAt.isBefore(DateTime.now())`.
- `isMastered`: `reviewStep >= 5`.
- `isInProgress`: `timesReviewed > 0 && !isMastered`.
