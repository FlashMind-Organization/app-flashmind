# Regra de Design e Temas — app-flashmind

## Diretrizes de Tema

1. **Suporte Obrigatório a Dark Mode**:
   - Todo novo widget precisa ser testado visualmente com `ThemeMode.light` e `ThemeMode.dark`.
2. **Tokens de Cores**:
   - Primary: `Color(0xFF6366F1)` (Indigo)
   - Fundo Claro: `Color(0xFFF6F7FB)` / Cards: `Colors.white` / Bordas: `Color(0xFFE4E4E7)`
   - Fundo Escuro: `Color(0xFF0F1115)` / Cards: `Color(0xFF18181B)` / Bordas: `Color(0xFF27272A)`
3. **Tipografia e Contraste**:
   - Em modo escuro, títulos usam `Color(0xFFFAFAFA)` e subtítulos `Color(0xFFA1A1AA)`.
   - Em modo claro, títulos usam `Color(0xFF09090B)` e subtítulos `Color(0xFF71717A)`.
