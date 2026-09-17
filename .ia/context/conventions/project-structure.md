# Estrutura do Projeto — app-flashmind

Organização centrada em funcionalidades (`features/`) complementada por um núcleo transversal (`core/`).

```text
lib/
├── main.dart                      # Inicialização, AppScope, ThemeData (Light/Dark)
├── core/
│   ├── app_scope.dart             # InheritedWidget de injeção de dependências
│   ├── progress/                  # Módulo de progresso global do usuário
│   │   ├── controllers/           # UserProgressController (ChangeNotifier)
│   │   ├── models/                # UserProgress
│   │   ├── repositories/          # UserProgressRepository (Local e InMemory)
│   │   └── services/              # GamificationService (Cálculo de XP e Streak)
│   └── review/
│       └── review_service.dart    # ReviewService (Orquestrador do SRS)
└── features/
    ├── home/                      # Dashboard principal
    │   ├── data/                  # quotes_data.dart, user_progress_data.dart
    │   ├── models/                # quote.dart, stats_data.dart
    │   ├── screens/               # home_screen.dart
    │   └── widgets/               # level_card.dart, stats_section.dart, quote_card.dart...
    ├── decks/                     # Gestão de baralhos
    │   ├── controllers/           # deck_details_controller.dart, create_deck_controller.dart
    │   ├── data/                  # decks_data.dart (seeds)
    │   ├── models/                # deck.dart
    │   ├── repositories/          # deck_repository.dart, local_deck_repository.dart...
    │   ├── screens/               # decks_screen.dart, deck_details_screen.dart...
    │   ├── services/              # deck_service.dart (ChangeNotifier)
    │   └── widgets/               # deck_list.dart, deck_list_item.dart...
    ├── flashcards/                # Sessão de repetição espaçada
    │   ├── controllers/           # create_flashcard_controller.dart, edit_flashcard_controller.dart
    │   ├── models/                # flashcard.dart, review_rating.dart, flashcard_achievement.dart
    │   ├── screens/               # flashcard_session_screen.dart, create_flashcard_screen.dart...
    │   ├── services/              # spaced_repetition_service.dart (SM-2)
    │   └── widgets/               # flashcard_view.dart, answer_buttons.dart...
    └── progress/                  # Calendário e detalhes de ofensiva
        ├── controllers/           # streak_controller.dart
        ├── screens/               # streak_screen.dart
        └── widgets/               # streak_calendar.dart
```
