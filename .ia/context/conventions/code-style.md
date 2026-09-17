# Convenções de Código — app-flashmind

## Regras Dart & Flutter

1. **Null Safety Rigoroso**:
   - Evite `!` (force unwrap) desnecessários; trate nulos com `??` ou guards precoces.
2. **Imutabilidade em Modelos**:
   - Classes de modelo devem usar `final` em seus atributos e oferecer `copyWith`.
   - Listas internas de coleções em serviços devem ser expostas com `List.unmodifiable(...)`.
3. **Padrão de Nomenclatura**:
   - Telas: `*Screen` (ex: `DecksScreen`).
   - Widgets: Substantivo claro (ex: `DeckListItem`, `StatsSection`).
   - Controladores/Serviços: `*Service` ou `*Controller`.
   - Repositórios: `*Repository` (interface) e `Local*Repository` / `InMemory*Repository`.
4. **Cores e Design Tokens**:
   - Cor primária: Indigo (`#6366F1`).
   - Superfície Clara: `#F6F7FB` / Cards: `#FFFFFF` / Bordas: `#E4E4E7`.
   - Superfície Escura: `#0F1115` / Cards: `#18181B` / Bordas: `#27272A`.
   - Nunca use `Colors.black` ou `Colors.white` puros para texto; use `Theme.of(context).textTheme` ou a cor correspondente do tema.
