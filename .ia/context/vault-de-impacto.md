# Conexão com o Vault de Impacto (`docs-flashmind`)

O projeto mantém um vault Obsidian de impacto e documentação viva em:
`../docs-flashmind/`

## O que consultar antes de editar código

- Se você vai mexer em um **Flashcard** ou **Deck**:
  - Consulte `../docs-flashmind/models/flutter/Deck.md` e `Flashcard.md`.
- Se você vai mexer na **lógica de repetição espaçada**:
  - Consulte `../docs-flashmind/dominios/Repetição Espaçada e Sessão.md` e `../docs-flashmind/guias/Algoritmo SRS e Gamificação.md`.
- Se você vai mexer em **telas**:
  - Consulte a nota correspondente em `../docs-flashmind/ui/flutter/`.

## Validação da Documentação

Ao criar ou renomear qualquer tela ou modelo no Flutter, execute o scanner do vault para garantir que a documentação acompanhe o código:
```bash
python3 ../docs-flashmind/_gerador/scan_app.py
```
