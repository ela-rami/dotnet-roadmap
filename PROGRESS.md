# Progress

*Ultimo aggiornamento: 29 ottobre 2026*

## Stato attuale

- **Fase:** inizio. Test di piazzamento fatto il 27 ottobre; il primo step pratico deve ancora partire.
- **Focus:** solo requisiti Must, partendo dalle lacune con step piccoli e isolati.
- **Priorità di partenza:** LINQ (usando l'SQL come ponte), dependency injection, EF Core (IQueryable, N+1), Git, alternati a LeetCode.
- **LeetCode:** stato dettagliato in [leetcode/CONTEXT.md](leetcode/CONTEXT.md) — lezione 2 (Arrays and strings) a metà, prossimo: step 7.
- **Step in corso:** Step 1 — LINQ di base con l'SQL come ponte (assegnato il 29 ottobre, vedi log).

## Ultima volta per argomento

Serve a capire cosa si sta arrugginendo e va ripreso.

| Argomento | Ultima volta | Note |
| --- | --- | --- |
| C# fondamentali | 27 ott 2026 (test) | |
| OOP | 27 ott 2026 (test) | |
| LINQ | 27 ott 2026 (test) | |
| API / HTTP | 27 ott 2026 (test) | |
| Dependency injection | 26 ott 2026 (test) | |
| EF Core | 27 ott 2026 (test) | |
| SQL | 27 ott 2026 (test) | |
| Git | 26 ott 2026 (test) | |
| LeetCode | 27 ott 2026 (test) | Lezioni: vedi leetcode/ |

## Log degli step

| # | Data | Area | Step | Esito |
| --- | --- | --- | --- | --- |
| 1 | 29 ott 2026 | LINQ | Tradurre 5 query SQL in LINQ su dati di produzione in memoria (`csharp/01-linq-basics`) | In corso — assegnato, da iniziare |

## Verifiche

| Data | Tipo | Risultato |
| --- | --- | --- |
| 26–27 ott 2026 | Test di piazzamento | Vedi sotto |

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
