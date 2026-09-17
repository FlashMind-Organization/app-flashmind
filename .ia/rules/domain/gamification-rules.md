# Regra Invariante: Gamificação e Progresso

## Concessão de XP

- `forgot`: **5 XP** (zera combo).
- `difficult`: **10 XP** (mantém combo).
- `easy`: **15 XP** (incrementa combo).

## Fórmula de Nível e XP

- XP para o nível $N$:
  $$\text{xpRequiredForLevel}(N) = 100 + (N - 1) \times 50$$
- XP acumulado total para atingir o nível $N$:
  $$\text{totalXpRequiredForLevel}(N) = (N - 1) \times (100 + (N - 2) \times 25)$$

## Cálculo de Ofensiva (Streak)

- Normalizado exclusivamente pela data `DateTime(year, month, day)`.
- Múltiplos estudos no mesmo dia apenas aumentam `reviewsToday` sem alterar `streakDays`.
- Se o dia anterior foi exatamente ontem (`lastDay.add(Duration(days: 1)) == today`), `streakDays++`.
- Se houver hiato maior que 1 dia, `streakDays` reinicia em `1`.
- `studyDays` registra a lista de datas únicas estudadas para exibição no calendário.
