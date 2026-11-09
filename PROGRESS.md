# Progress

*Ultimo aggiornamento: 8 novembre 2026*

## Stato attuale

- **Metodo (dall'8 novembre 2026):** corso strutturato a moduli, vedi [COURSE.md](COURSE.md). Ogni modulo: esame d'ingresso completo → studio solo dei buchi → esame finale completo. Si parte dalle basi: ripassare non fa male, e quello che so già lo supero in fretta all'esame.
- **Modulo in corso:** Modulo 0 — Fondamenta di C#.
- **Punto esatto:** esame d'ingresso del Modulo 0 — Parte A, blocco 1/3 completato e corretto il 9 nov (vedi [course/00-fondamenta-csharp/esami.md](course/00-fondamenta-csharp/esami.md)). Prossimo: blocco 2/3 (stringhe, array, collezioni, null e nullable). Poi blocco 3/3 (eccezioni, scope, const/readonly) e Parte B: assignment.
- **LeetCode:** stato dettagliato in [leetcode/CONTEXT.md](leetcode/CONTEXT.md) — lezione 2 (Arrays and strings) a metà, prossimo: step 7.

## Stato del corso

🟢 superato · 🟡 in corso · ⬜ da iniziare

| Modulo | Stato | Esame d'ingresso | Esame finale | Note |
| --- | --- | --- | --- | --- |
| 0 — Fondamenta di C# | 🟡 | in corso: blocco 1/3 fatto | — | Blocco 1: 🟢 flusso, ref/valore, Equals; 🔴 overflow, ++, == su object e boxing, riferimenti passati per valore, parametri nominati, out/TryParse |
| 1 — OOP in C# | ⬜ | | | |
| 2 — C# intermedio | ⬜ | | | |
| 3 — SQL e SQL Server | ⬜ | | | |
| 4 — LINQ | ⬜ | | | Lezione già avviata l'8 nov (parte 1: cos'è LINQ e le lambda) |
| 5 — Git e GitHub | ⬜ | | | |
| 6 — HTTP e REST | ⬜ | | | |
| 7 — ASP.NET Core Web API | ⬜ | | | |
| 8 — Entity Framework Core | ⬜ | | | Fine della soglia di candidabilità |
| 9 — Testing | ⬜ | | | |
| 10 — Design e architettura | ⬜ | | | |
| 11 — Sicurezza delle API | ⬜ | | | |
| 12 — Docker | ⬜ | | | |
| 13 — CI/CD e Azure | ⬜ | | | |
| 14 — Agile e lavoro in team | ⬜ | | | |

## Log

| # | Data | Modulo | Cosa | Esito |
| --- | --- | --- | --- | --- |
| 1 | 29 ott – 8 nov 2026 | LINQ | Esercizio SQL → LINQ, poi lezione LINQ parte 1 | Superato dal nuovo metodo: LINQ si fa nel Modulo 4. L'esercizio resta valido per quel modulo |
| 2 | 8 nov 2026 | — | Passaggio al corso strutturato a moduli (COURSE.md) | Fatto |
| 3 | 8–9 nov 2026 | 0 | Esame d'ingresso, Parte A, blocco 1/3 (3 domande) | Fatto e corretto — vedi esami.md |

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
