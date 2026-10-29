# Requisiti — cosa chiedono gli annunci

*Prima versione: 27 ottobre 2026 · Prossima revisione: metà dicembre 2026*

Fonte: scansione di annunci junior .NET/C# a Vienna e in Austria (devjobs.at, jobs.at, Indeed AT) e di annunci junior remoti in Europa e UK. È un campione, non un'analisi rigorosa: va raffinato con annunci reali salvati da LinkedIn.

**Livello** = stima di partenza dal test di piazzamento del 27 ottobre (dettagli in [PROGRESS.md](PROGRESS.md#test-di-piazzamento--27-ottobre-2026)). Si aggiorna man mano.

🟢 solido · 🟡 da ripassare · 🟠 lacuna pratica · 🔴 lacuna · ⚪ non ancora verificato

## Must — soglia di candidabilità

| Area | Cosa serve sapere | Livello |
| --- | --- | --- |
| C# fondamentali | Tipi valore/riferimento, async/await, eccezioni, generics, collezioni | 🟡 |
| OOP e design | Interfacce, classi astratte, polimorfismo, SOLID di base | 🟡 |
| LINQ | Scrivere da zero query con Where/Select/GroupBy/OrderBy; lambda | 🟠 |
| ASP.NET Core Web API | Controller o Minimal API, routing, verbi HTTP, status code, validazione | 🟠 |
| Dependency injection | Cos'è, perché, lifetime Transient/Scoped/Singleton | 🔴 |
| EF Core | DbContext, migrazioni, IQueryable vs IEnumerable, Include, problema N+1 | 🟠 |
| SQL / SQL Server | JOIN, GROUP BY/HAVING, subquery, CASE, CTE, window function, indici, transazioni | 🟢 basi · ⚪ intermedio |
| Git | Branch, commit, merge vs rebase, conflitti, pull request | 🔴 |
| LeetCode | Easy in ~20 min, Medium comuni in ~40, ragionamento ad alta voce in inglese | 🟢 basi teoriche · 🟠 pratica |

## Should — fanno passare davanti agli altri

| Area | Cosa serve sapere | Livello |
| --- | --- | --- |
| Unit testing | xUnit o NUnit, Arrange-Act-Assert, mock | ⚪ |
| Docker | Dockerfile per un'API .NET, docker compose con un database | ⚪ |
| Azure e CI/CD | Azure DevOps o GitHub Actions, deploy di base su Azure | ⚪ |
| Design pattern | Repository, factory, strategy, i più comuni | ⚪ |
| Agile / Scrum | Ruoli, cerimonie, user story, come si lavora in uno sprint | ⚪ |
| Autenticazione | JWT, autorizzazione per ruoli in ASP.NET Core | ⚪ |

## Nice — utili ma non decisivi

| Area | Cosa serve sapere | Livello |
| --- | --- | --- |
| Dapper | Query SQL esplicite da C# | ⚪ |
| Messaggistica | RabbitMQ / Azure Service Bus, concetti base | ⚪ |
| Logging e diagnostica | ILogger, livelli di log, Serilog | ⚪ |
| Frontend | Angular, React o Blazor — molti "junior .NET" a Vienna sono full stack | ⚪ (dopo il backend) |

## Note dal mercato

- Molti annunci "junior .NET" a Vienna sono in realtà full stack, spesso con Angular o Blazor: il frontend servirà prima di quanto sembra. Prima di sceglierlo, confrontare Angular e React sugli annunci austriaci.
- Il full remote junior è la porta più stretta (spesso con vincoli di paese); un ruolo ibrido a Vienna è più raggiungibile.
- Diversi annunci austriaci chiedono il tedesco: scelta consapevole di puntare solo su quelli in inglese.
