# Quality backlog — quickfix-iceland

Świadomie odłożone przy PG v3 github-ready (2026-09-05). Nie blokuje merge'a tego PR.

| # | Co | Dlaczego odłożone | Ryzyko jak zostanie |
|---|---|---|---|
| 1 | `eslint.config.mjs` (strict baseline) dodany przez bootstrap, ale nie ma żadnego pliku JS/TS do lintowania | Repo nie ma kodu — to placeholder na wypadek, gdyby kiedyś tu wylądował kod | Zerowe — plik jest bierny, `eslint` bez configu docelowego po prostu nic nie znajdzie |
| 2 | Widoczność repo `homehug-services` (publiczne/prywatne) niejasna w README ("access may be restricted") | Osobna decyzja Kamila, poza zakresem tego zadania (patrz `docs/adr/0001-...md`, sekcja "Nierozwiązane świadomie") | Niskie — stan opisany uczciwie (hedge, nie fałszywe "private"); nie zmieniano widoczności ani nie zgadywano stanu |
| 3 | Stack wdrożeniowy produktu (hosting, framework, baza) nieznany z tego repo | Kod jest w `homehug-services`, którego ten agent nie otwierał (poza zakresem) | Niskie — `docs/ARCHITECTURE.md` oznacza to wprost jako [NIEPEWNE] zamiast zgadywać |

## Co NIE jest długiem (świadomie tak zostaje)
- Brak `package.json`/testów/builda — to repo nie ma kodu z założenia (patrz ADR-0001). Dodawanie pustego szkieletu Node tylko po to, żeby "coś" leciało w CI, byłoby teatrem, nie jakością.
