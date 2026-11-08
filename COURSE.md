# Il corso — Backend .NET da zero a junior/mid

*v1 — 8 novembre 2026*

Un corso completo, strutturato in moduli come un corso universitario o Coursera, ma con un principio diverso: **prima l'esame, poi lo studio solo dove serve.** Non si salta niente, ma non si perde tempo su quello che so già.

Lo stato di ogni modulo è in [PROGRESS.md](PROGRESS.md#stato-del-corso). Il collegamento con quello che chiedono gli annunci è in [REQUIREMENTS.md](REQUIREMENTS.md).

## Come funziona ogni modulo

```
1. Esame d'ingresso COMPLETO  →  copre ogni argomento della checklist del modulo
2. Correzione                 →  ogni argomento: 🟢 superato · 🟡 parziale · 🔴 non saputo
3. Studio solo su 🟡 e 🔴      →  lezioni a piccoli passi + esercizi scritti a mano
4. Esame finale COMPLETO      →  di nuovo tutta la checklist, con domande nuove
5. Modulo superato            →  tutti gli argomenti 🟢; altrimenti si torna al punto 3 solo sui buchi
```

- Se all'esame d'ingresso è tutto 🟢, il modulo è superato subito.
- Se un modulo è quasi tutto 🔴 (argomento mai visto davvero), si fa la lezione completa del modulo e poi l'esame finale.

## Gli esami

- **Completi:** almeno una domanda per ogni argomento della checklist del modulo. Nessun argomento viene dato per scontato.
- **Divisi in parti** da ~20–30 minuti (es. "Esame Modulo 0 — parte 1/3"), così si possono fare anche in sessioni brevi.
- **Tipi di domanda, mescolati:**
  - teoria a parole, come a un colloquio (alcune **in inglese**)
  - "cosa stampa questo codice e perché?"
  - scrivere codice a mano, senza autocompletamento né AI
  - trovare e correggere un bug
  - per problemi vaghi: fare prima le domande di chiarimento
- **Senza aiuti.** Un argomento è 🟢 solo se la risposta è giusta *e* so spiegare il perché. Imprecisioni di sintassi minori non contano.
- **Ripasso cumulativo:** dall'esame finale del Modulo 2 in poi, ogni esame finale include 2–3 domande dei moduli precedenti.
- I risultati vanno in `course/NN-nome/esami.md` e la sintesi in PROGRESS.md.

## Le lezioni

- In italiano, **un concetto alla volta**: spiegazione breve, esempio concreto (meglio se dal mondo gestionale/industriale), poi stop. Scrivo "avanti" o faccio domande.
- Dopo ogni concetto, un mini esercizio da scrivere io.
- Per ogni argomento, il link alla documentazione ufficiale **Microsoft Learn** come riferimento da rileggere.
- Gli appunti completi vanno in `course/NN-nome/lezioni.md`: tutto quello che è stato spiegato, le mie domande e le correzioni, rileggibili mesi dopo senza la chat.

## I moduli

**Moduli 0–8 = soglia di candidabilità** (requisiti Must). Finiti questi, si può iniziare a candidarsi seriamente mentre si continua.

### Modulo 0 — Fondamenta di C#
- Tipi primitivi, `var`, conversioni e cast, `checked`/overflow
- Operatori, precedenza, `==` vs `Equals`
- Controllo di flusso: `if`, `switch` (anche switch expression), cicli, `break`/`continue`
- Metodi: parametri, valori di ritorno, overload, parametri opzionali e nominati, `ref`/`out`/`in`
- Stringhe: immutabilità, interpolazione, metodi comuni, `StringBuilder`, confronto
- Array (mono, multi e frastagliati)
- Collezioni: `List<T>`, `Dictionary<K,V>`, `HashSet<T>`, `Queue<T>`, `Stack<T>` — quando usare quale e quanto costano
- `null`, tipi nullable (`int?`), nullable reference types, `?.` e `??`
- Eccezioni: `try/catch/finally`, tipi comuni, lanciare e rilanciare (`throw` vs `throw ex`), quando *non* usarle
- Scope e ciclo di vita delle variabili; `const` vs `readonly`

### Modulo 1 — Programmazione a oggetti in C#
- Classi e oggetti, costruttori (anche concatenati), inizializzatori
- Campi vs proprietà, auto-property, `init`, modificatori di accesso
- Incapsulamento: perché e come
- Ereditarietà, `base`, `virtual`/`override`, `sealed`
- Classi astratte vs interfacce — differenze e quando usare quale
- Polimorfismo (con un caso concreto: macchine con protocolli diversi)
- Membri `static` e classi statiche
- Tipi valore vs tipi riferimento: `struct` vs `class`, copia, stack/heap (a grandi linee)
- `record` e uguaglianza per valore
- Composizione vs ereditarietà
- Overload degli operatori, `ToString`, `Equals`/`GetHashCode` (concetti)

### Modulo 2 — C# intermedio
- Generics: classi e metodi generici, vincoli (`where T : ...`)
- Delegati, `Func`/`Action`/`Predicate`, lambda, closure
- Eventi (concetto e uso base)
- Extension methods
- `IEnumerable<T>`, `IEnumerator`, `yield return`
- Pattern matching (`is`, `switch` con pattern, property pattern)
- `async`/`await`, `Task`, `Task<T>`, perché libera il thread, `ConfigureAwait` (concetto), errori comuni (`async void`, `.Result`)
- `IDisposable`, `using` (istruzione e dichiarazione), garbage collector (a grandi linee)
- Tuple e deconstruction
- Novità utili del C# moderno: file-scoped namespace, top-level statements, primary constructor, collection expression

### Modulo 3 — SQL e SQL Server (T-SQL)
- Modello relazionale, chiavi primarie ed esterne, normalizzazione (1NF–3NF)
- DDL: `CREATE`/`ALTER`/`DROP`, tipi di dato, vincoli
- DML: `SELECT`, `INSERT`, `UPDATE`, `DELETE`
- `WHERE`, `ORDER BY`, `TOP`/`OFFSET-FETCH`, `DISTINCT`, `LIKE`, `IN`, `BETWEEN`, `NULL`
- JOIN: inner, left/right, full, cross, self join
- `GROUP BY`, `HAVING`, funzioni di aggregazione
- Subquery (anche correlate), `EXISTS`
- `CASE`
- CTE (anche ricorsive, concetto)
- Window function: `ROW_NUMBER`, `RANK`, `SUM() OVER`, `PARTITION BY`
- Indici: clustered vs non-clustered, quando aiutano e quando no, piano di esecuzione (lettura base)
- Transazioni, ACID, livelli di isolamento (concetto)
- Stored procedure, funzioni, viste
- SQL injection e query parametrizzate

### Modulo 4 — LINQ
- Cos'è LINQ, lambda, sintassi a metodi vs sintassi a query
- `Where`, `Select`, `SelectMany`
- `OrderBy`/`ThenBy`, `Take`/`Skip`, paginazione
- `First`/`FirstOrDefault`/`Single`/`Last` — differenze e eccezioni
- `GroupBy`, `ToDictionary`, `ToLookup`
- Aggregati: `Count`, `Sum`, `Average`, `Min`/`Max`, `Any`/`All`, `Aggregate`
- `Join` e `GroupJoin`
- `Distinct`, `Union`, `Intersect`, `Except`, `Zip`
- Esecuzione differita vs immediata, enumerazione multipla
- `IEnumerable` vs `IQueryable` (ponte verso EF Core)
- Costi nascosti di LINQ (complessità)

### Modulo 5 — Git e GitHub
- Repository, working tree, staging, commit; `status`, `log`, `diff`
- Branch: creare, spostarsi, cancellare
- `merge` vs `rebase`; fast-forward
- Risolvere i conflitti
- Remote: `clone`, `fetch`, `pull`, `push`
- Annullare: `restore`, `reset`, `revert`, `stash`
- Pull request e code review; workflow a feature branch
- Buone pratiche: commit piccoli, messaggi chiari, `.gitignore`

### Modulo 6 — HTTP e REST
- Come funziona una richiesta HTTP: metodo, URL, header, body
- Verbi: GET, POST, PUT, PATCH, DELETE; sicurezza e idempotenza
- Status code: 2xx, 3xx, 4xx, 5xx — i più usati e quando
- JSON, content negotiation
- Principi REST, design delle risorse e degli URL
- Stateless, cookie vs token (concetto)
- CORS (concetto)
- Versioning e paginazione delle API

### Modulo 7 — ASP.NET Core Web API
- Struttura di un progetto, `Program.cs`, host e configurazione
- Pipeline delle richieste e middleware (ordine, middleware custom)
- Routing; controller vs Minimal API
- Model binding, DTO, validazione (Data Annotations / FluentValidation)
- **Dependency injection:** cos'è e perché, registrazione, lifetime Transient/Scoped/Singleton, errori classici
- Configurazione: `appsettings`, environment, Options pattern
- Logging con `ILogger`
- Gestione globale degli errori, ProblemDetails
- Risposte e status code corretti, `IActionResult`/`Results`
- Swagger/OpenAPI

### Modulo 8 — Entity Framework Core
- ORM: cosa risolve e cosa costa
- `DbContext`, `DbSet`, configurazione e connessione
- Modellazione: entità, convenzioni, Fluent API, relazioni 1-1, 1-N, N-N
- Migrazioni
- Query con LINQ: `IQueryable`, traduzione in SQL, proiezioni con `Select`
- Caricamento dei dati correlati: `Include`, lazy loading, il problema N+1
- Change tracking, `AsNoTracking`
- Salvataggi, transazioni, concorrenza ottimistica (concetto)
- Query SQL dirette e quando preferire Dapper

**Moduli 9–14 = fanno la differenza** (requisiti Should).

### Modulo 9 — Testing
- Perché testare; unit vs integration vs end-to-end
- xUnit: `Fact`, `Theory`, Arrange-Act-Assert
- Mock e stub (Moq/NSubstitute), quando mockare
- Integration test di un'API con `WebApplicationFactory`
- Testare codice con database (in-memory vs Testcontainers, concetto)

### Modulo 10 — Design e architettura
- SOLID con esempi concreti
- Design pattern comuni: repository, factory, strategy, decorator, singleton (e perché la DI lo sostituisce)
- Architettura a livelli e Clean Architecture (concetti), vertical slice
- DTO e mapping
- Codice pulito: naming, metodi piccoli, refactoring

### Modulo 11 — Sicurezza delle API
- Autenticazione vs autorizzazione
- JWT: struttura, emissione, validazione
- Autorizzazione per ruoli e policy
- Hashing delle password, secret management
- OWASP Top 10 a livello API (concetti)

### Modulo 12 — Docker
- Container vs macchina virtuale
- Dockerfile per un'API .NET, build multi-stage
- Immagini, container, volumi, rete
- Docker Compose: API + database

### Modulo 13 — CI/CD e Azure
- CI/CD: concetti, pipeline con GitHub Actions (build, test)
- Azure: App Service, Azure SQL, configurazione e segreti
- Deploy di un'API .NET su Azure

### Modulo 14 — Agile e lavoro in team
- Scrum: ruoli, eventi, artefatti
- User story, stime, sprint
- Kanban (concetto)
- Come si lavora in team: PR, code review, definition of done

### Dopo i moduli
- **Progetto portfolio** costruito con quello che si è imparato (da definire quando arriviamo lì, idealmente nel dominio industriale/gestionale).
- **Colloquio simulato completo**, in inglese, che mescola tutti i moduli.
- Il **frontend** sarà un corso a parte, dopo il backend.

## Traccia parallela: LeetCode

Gira in parallelo con la sua roadmap ([leetcode/roadmap.md](leetcode/roadmap.md)) e le sue regole ([leetcode/CONTEXT.md](leetcode/CONTEXT.md)), circa uno step ogni tre, per variare e perché nei colloqui serve.
