# RUNBOOK — operacje i awarie

Ten repo nie hostuje niczego — jest dokumentacją. "Awaria" tutaj oznacza awarię PRODUKTU
(`quickfix.is`), nie tego repo. To repo samo w sobie nie może "spaść".

## Podstawy
- Produkcja: https://quickfix.is
- Kod aplikacji: osobne repo [`homehug-services`](https://github.com/kamiljan11/homehug-services) (patrz README → Source)
- Ten repo: github.com/kamiljan11/quickfix-iceland (tylko dokumentacja)
- Sekrety: nie dotyczy tego repo (brak kodu, brak env)

## Deploy
Nie dotyczy tego repo. Deploy produktu opisany (jeśli w ogóle) w `homehug-services`.

## Healthcheck
```bash
curl -I https://quickfix.is   # 200 = strona wstaje
```
Jeśli nie 200: problem jest w `homehug-services` / hostingu tego produktu, nie tutaj.

## Typowe awarie
| Objaw | Pierwszy krok |
|---|---|
| `quickfix.is` nie odpowiada | Sprawdz hosting/DNS produktu — poza tym repo. Zacznij od `homehug-services`. |
| README tego repo mówi co innego niż strona | Zaufaj stronie (zweryfikuj `curl`/przeglądarką), popraw README w PR |
| Ktoś pyta o kod/logikę biznesową | Nie tutaj — skieruj do `homehug-services`, sprawdź czy ma dostęp |

## Kontakty
- Właściciel: Kamil Jan, mountainallservice@gmail.com
