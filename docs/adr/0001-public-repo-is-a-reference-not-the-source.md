# ADR-0001 — Ten publiczny repo to referencja, nie źródło aplikacji

Data: 2026-09-05 | Status: przyjęte (widoczne w historii repo od 2026-08-10)

**Kontekst:** `quickfix-iceland` jest publiczne na GitHubie (portfolio/audyt), ale sam produkt
(strona `quickfix.is`) ma logikę biznesową, ceny i strukturę kontaktu z klientami, których Kamil
nie chce trzymać w publicznym repo. Wcześniej (do 2026-08-10) README twierdziło wprost
"Source is private" — co było nieścisłe: kod istnieje w osobnym repo (`homehug-services`), a to
sformułowanie sugerowało, że w ogóle nie ma gdzie zajrzeć, zamiast po prostu wskazać, gdzie kod
jest i jaki ma status.

**Decyzja:** `quickfix-iceland` zawiera wyłącznie dokumentację (README, ARCHITECTURE, ADR,
RUNBOOK, GLOSSARY) — zero `package.json`, zero `src/`. Rzeczywisty kod strony żyje w osobnym
repo `homehug-services` i jest nazwany wprost w sekcji "Source" README, zamiast ukryty za ogólnym
"private" (commit `docs: sprostowanie sekcji Source`, 2026-08-10).

**Rozważone alternatywy:**
- *Trzymać ogólne "Source is private" bez nazwy repo* — odrzucone 2026-08-10: to nieprawda w
  sensie dosłownym (kod ISTNIEJE i ma nazwę) i nie daje nikomu możliwości zweryfikowania czegokolwiek.
- *Umieścić kod aplikacji w tym samym publicznym repo* — odrzucone: strona ma dane sprzedażowe
  i strukturę kontaktu klienta, których Kamil nie chce publicznie widocznych obok portfolio.
- *Prywatne monorepo bez żadnej publicznej wizytówki* — odrzucone: portfolio/audyt (np. rekruter,
  klient) potrzebuje czegoś do obejrzenia bez proszenia o dostęp za każdym razem.

**Konsekwencje:**
- CI w tym repo (`quality.yml`) sprawdza tylko treść dokumentacji (gitleaks, Semgrep) — kroki
  npm (lint/typecheck/test/build) pomijają się przez `hashFiles('package.json')`, bo nie ma czego
  budować. Zielona bramka tutaj oznacza "brak sekretów w docs", nie "aplikacja działa".
- Jedyny wiarygodny "smoke test" tego repo to zewnętrzny `curl -I https://quickfix.is` (patrz
  `docs/RUNBOOK.md`) — nie lokalny test frameworka, bo lokalnie nie ma czego uruchomić.
- **Nierozwiązane świadomie**: widoczność `homehug-services` na GitHubie (publiczne/prywatne) to
  osobna, jeszcze nie podjęta decyzja Kamila — ten ADR dotyczy WYŁĄCZNIE podziału
  wizytówka/źródło, nie tego, kto może czytać kod w `homehug-services`. Nie zmieniaj widoczności
  tamtego repo przy okazji tego zadania.

**Pułapki dla przyszłego siebie:**
- Nie dopisuj tu kodu "tymczasowo, żeby coś pokazać" — jeśli aplikacja kiedyś ma być publiczna,
  to osobna, świadoma decyzja (i osobny ADR), nie commit poboczny.
- Link do `homehug-services` w README ma być realną nazwą repo, nie ogólnikiem — jeśli nazwa się
  zmieni, popraw w tym samym PR co zmianę.
