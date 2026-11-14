# Progress

*Ultimo aggiornamento: 14 novembre 2026*

## Stato attuale

- **Metodo (dal 14 novembre 2026):** corso da zero a lezioni, una lezione alla volta scelta dal tutor, con esercizi a fine lezione. Lezioni in inglese sul sito ([docs/](docs/), pubblicato su GitHub Pages). Vedi [CONTEXT.md](CONTEXT.md) e [GUIDE.md](GUIDE.md).
- **Sezione in corso:** 1 · C# Fundamentals.
- **Lezione in corso:** 1.1 — How a C# program runs ([docs/csharp-fundamentals/01-how-a-csharp-program-runs.md](docs/csharp-fundamentals/01-how-a-csharp-program-runs.md)). Pubblicata il 14 nov.
- **Punto esatto:** esercizi della lezione 1.1 da fare (in `exercises/01-csharp-fundamentals/1.1-how-a-csharp-program-runs/`), poi revisione in chat.
- **Punti deboli da riprendere** (dall'esame d'ingresso in [archive/](archive/esame-ingresso-modulo-0/esami.md)): overflow e `checked`; `++` prefisso/postfisso; `&` vs `&&`; boxing e `==` su `object`; riferimenti passati per valore; parametri nominati e opzionali; `out` e pattern TryParse; collezioni oltre `List` e array (non le ricorda); immutabilità delle stringhe (`ToUpper()` senza assegnare).
- **LeetCode:** fermo alla lezione 2 (Arrays and strings), step 7 ([leetcode/CONTEXT.md](leetcode/CONTEXT.md)). Si riprende dopo aver rivisto le collezioni nella sezione 1.

## Lezioni

| Lezione | Pubblicata | Esercizi | Note |
| --- | --- | --- | --- |
| 1.1 How a C# program runs | 14 nov 2026 | da fare | |

## Log

| # | Data | Cosa | Esito |
| --- | --- | --- | --- |
| 1 | 29 ott – 8 nov 2026 | Esercizio SQL → LINQ, poi lezione LINQ parte 1 (in chat) | Sospeso: LINQ arriverà nella sezione 5 |
| 2 | 8 nov 2026 | Passaggio al corso a moduli con esame d'ingresso | Sostituito il 14 nov |
| 3 | 8–9 nov 2026 | Esame d'ingresso Modulo 0: blocco 1 (3 domande) corretto; blocco 2, domanda 1 risposta, domanda 2 iniziata | Interrotto; risultati archiviati come diagnosi in [archive/](archive/esame-ingresso-modulo-0/esami.md) |
| 4 | 14 nov 2026 | Passaggio al corso da zero a lezioni, con sito MkDocs su GitHub Pages | Fatto |
| 5 | 14 nov 2026 | Lezione 1.1 pubblicata | Esercizi da fare |

## Verifiche

| Data | Tipo | Risultato |
| --- | --- | --- |
| 26–27 ott 2026 | Test di piazzamento (generale) | Vedi sotto: serve come prima idea, i moduli fanno comunque il proprio esame completo |

### Test di piazzamento — 27 ottobre 2026

Domande a voce e in chat, una o due per area. È una **stima di partenza**, non un giudizio definitivo: si ricalibra man mano.

| Area | Domanda | Come è andata | Livello |
| --- | --- | --- | --- |
| C# / EF Core | `IEnumerable` vs `IQueryable` | Uso quasi solo `IEnumerable`, non conoscevo la differenza | 🟠 |
| SQL | `INNER JOIN` vs `LEFT JOIN` | Corretto | 🟢 |
| SQL | Clienti con totale ordini > 1000 | `GROUP BY` + `HAVING` corretto, spiegato bene `HAVING` vs `WHERE`. Raggruppare per Id e non per nome | 🟢 |
| DI | Cos'è, Transient/Scoped/Singleton | Non la conoscevo (l'ho confusa con `using`) | 🔴 |
| Git | `merge` vs `rebase` | Non lo sapevo | 🔴 |
| OOP | Leggere dati da macchine con protocolli diversi in modo uniforme | Tre classi giuste, ma non sono arrivato all'interfaccia comune e al polimorfismo | 🟡 |
| OOP | Interfaccia vs classe astratta | Concetto invertito | 🟡 |
| API | Verbi HTTP per un CRUD + status se non trovato | GET/POST/DELETE sì; mancavano PUT/PATCH e gli status code (404, 201, 400) | 🟠 |
| C# | A cosa servono `async`/`await` in un'API | Sapevo che "aspetta"; mancava il punto chiave: il thread viene liberato → scalabilità | 🟡 |
| C# | `struct` vs `class` (copia di variabili) | Risposto `5 5`, corretto `1 5`: tipo valore vs riferimento | 🟡 |
| LINQ | Riscrivere la query SQL dei clienti in LINQ | La uso ma non so scriverla da zero | 🟠 |
| EF Core | Query dentro un ciclo `foreach` | Non ho individuato il problema N+1 | 🟠 |
| LeetCode | Two Sum, solo approccio | Brute force O(n²) corretto; idea di ordinare + ricerca binaria; il dizionario mi era venuto in mente ma pensavo fosse "barare". Errore: ordinare costa O(n log n), non n² | 🟢 ragionamento |

**Sintesi:** basi teoriche buone (SQL e algoritmi soprattutto); manca la padronanza scritta a mano dell'ecosistema .NET — LINQ, EF Core, DI, API — e Git.
