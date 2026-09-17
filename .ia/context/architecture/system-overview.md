# Visão Geral da Arquitetura — FlashMind Mobile

## Pilares Fundamentais

1. **Local-First por Padrão**:
   Toda a leitura e escrita acontece no dispositivo local (`SharedPreferences`), garantindo carregamento instantâneo e uso offline completo.

2. **Hierarquia Limpa de Responsabilidades**:
   - `Screens / Widgets`: Capturam toques, exibem estados e disparam intenções.
   - `Controllers / Services`: Guardam a lógica de negócio (`DeckService`, `UserProgressController`, `ReviewService`).
   - `Repositories`: Escondem os detalhes de persistência sob interfaces abstratas (`DeckRepository`, `UserProgressRepository`).

3. **Orquestração de Sessão**:
   O `ReviewService` age como mediador central durante o estudo:
   ```text
   FlashcardSessionScreen (UI)
          ↓ reviewFlashcard(deck, card, rating)
   ReviewService
     ├── 1. SpacedRepetitionService.reviewCard(...)  [calcula novo step e nextReviewAt]
     ├── 2. DeckService.updateFlashcard(...)         [persiste no baralho via repository]
     ├── 3. GamificationService.applyReview(...)     [calcula novo XP, streak e combo]
     └── 4. UserProgressController.setProgress(...)  [notifica ouvintes da UI e salva]
   ```
