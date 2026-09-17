# Mapa de Injeção de Dependências (DI) — AppScope

## Implementação com InheritedWidget

O FlashMind evita o acoplamento de bibliotecas de terceiros como Provider ou GetIt nesta fase, utilizando um `InheritedWidget` nativo de alto desempenho.

```dart
// lib/core/app_scope.dart
class AppScope extends InheritedWidget {
  final DeckService deckService;
  final UserProgressController userProgressController;
  final ReviewService reviewService;
}
```

### Inicialização no `main.dart`

```dart
final prefs = await SharedPreferences.getInstance();

final deckService = DeckService(repository: LocalDeckRepository(prefs));
await deckService.init();

final userProgressController = UserProgressController(
  repository: LocalUserProgressRepository(prefs),
);
await userProgressController.init();

final reviewService = ReviewService(
  spacedRepetitionService: SpacedRepetitionService(),
  gamificationService: const GamificationService(),
  userProgressController: userProgressController,
  deckService: deckService,
);

runApp(
  AppScope(
    deckService: deckService,
    userProgressController: userProgressController,
    reviewService: reviewService,
    child: FlashcardApp(...),
  ),
);
```

### Como consumir nos Widgets

```dart
final deckService = AppScope.of(context).deckService;
final userProgress = AppScope.of(context).userProgressController;
final reviewService = AppScope.of(context).reviewService;
```
