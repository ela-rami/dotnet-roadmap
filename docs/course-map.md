# Course map

Everything the course must cover by the end. It is a **coverage map, not an order**: lessons are chosen one at a time, and a box gets ticked when a lesson has covered the topic *and* I've done the exercises.

:material-check-circle: Sections 1–9 = **interview-ready threshold** for junior backend .NET roles.

??? info "Skipped on purpose (for now)"
    Desktop GUIs (WinForms/WPF), Blazor and any frontend, microservices, Kubernetes, Terraform. Frontend will be a separate course after the backend.

## 1 · C# Fundamentals

- [ ] How a program runs: .NET vs .NET Framework, SDK vs runtime, CLR, IL and JIT, assemblies, the `dotnet` CLI, `.csproj` and NuGet
- [ ] Primitive types, `var`, conversions and casts, integer division, overflow and `checked`
- [ ] Operators and precedence, `++` prefix/postfix, short-circuit `&&`/`||` vs `&`/`|`
- [ ] Control flow: `if`, `switch` statements and switch expressions, loops, `break`/`continue`
- [ ] Methods: parameters, return values, overloads, optional and named parameters, `ref`/`out`/`in`
- [ ] Strings: immutability, interpolation, common methods, comparison and culture, `StringBuilder`
- [ ] Arrays: single, multi-dimensional, jagged
- [ ] Collections: `List<T>`, `Dictionary<K,V>`, `HashSet<T>`, `Queue<T>`, `Stack<T>` — when to use which, and their costs
- [ ] `null`: nullable value types, nullable reference types, `?.`, `??`, `??=`
- [ ] Exceptions: `try`/`catch`/`finally`, common types, `throw` vs `throw ex`, `Parse` vs `TryParse`, when *not* to use exceptions
- [ ] Scope and lifetime of variables, `const` vs `readonly`

## 2 · Object-Oriented Programming

- [ ] Classes and objects, constructors (and chaining), object initializers
- [ ] Fields vs properties, auto-properties, `init`, access modifiers
- [ ] Encapsulation: why and how
- [ ] Inheritance, `base`, `virtual`/`override`, `sealed`
- [ ] Abstract classes vs interfaces — and when to use which
- [ ] Polymorphism (e.g. machines that speak different protocols behind one interface)
- [ ] `static` members and static classes
- [ ] Value types vs reference types: `struct` vs `class`, copying, boxing, stack and heap (at a high level)
- [ ] `record` and value equality
- [ ] Composition vs inheritance
- [ ] `ToString`, `Equals`/`GetHashCode`, operator overloading (concepts)

## 3 · Intermediate C#

- [ ] Generics: generic classes and methods, constraints
- [ ] Delegates, `Func`/`Action`/`Predicate`, lambdas, closures
- [ ] Events (concept and basic use)
- [ ] Extension methods
- [ ] `IEnumerable<T>`, `IEnumerator`, `yield return`
- [ ] Pattern matching: `is`, switch patterns, property patterns
- [ ] `async`/`await`, `Task`, why it frees the thread, common mistakes (`async void`, `.Result`)
- [ ] `IDisposable`, `using`, the garbage collector (at a high level)
- [ ] Tuples and deconstruction
- [ ] Modern C#: file-scoped namespaces, top-level statements, primary constructors, collection expressions

## 4 · SQL Server (T-SQL)

- [ ] Relational model, primary and foreign keys, normalization (1NF–3NF)
- [ ] DDL: `CREATE`/`ALTER`/`DROP`, data types, constraints
- [ ] DML: `SELECT`, `INSERT`, `UPDATE`, `DELETE`
- [ ] Filtering and sorting: `WHERE`, `ORDER BY`, `TOP`, `OFFSET-FETCH`, `DISTINCT`, `LIKE`, `IN`, `BETWEEN`, `NULL`
- [ ] Joins: inner, left/right, full, cross, self join
- [ ] `GROUP BY`, `HAVING`, aggregate functions
- [ ] Subqueries (including correlated), `EXISTS`
- [ ] `CASE`
- [ ] CTEs
- [ ] Window functions: `ROW_NUMBER`, `RANK`, `SUM() OVER`, `PARTITION BY`
- [ ] Indexes: clustered vs non-clustered, when they help, reading an execution plan
- [ ] Transactions, ACID, isolation levels (concept)
- [ ] Stored procedures, functions, views
- [ ] SQL injection and parameterized queries

## 5 · LINQ

- [ ] What LINQ is, lambdas, method syntax vs query syntax
- [ ] `Where`, `Select`, `SelectMany`
- [ ] `OrderBy`/`ThenBy`, `Take`/`Skip`, paging
- [ ] `First`/`FirstOrDefault`/`Single`/`Last` — differences and exceptions
- [ ] `GroupBy`, `ToDictionary`, `ToLookup`
- [ ] Aggregates: `Count`, `Sum`, `Average`, `Min`/`Max`, `Any`/`All`, `Aggregate`
- [ ] `Join` and `GroupJoin`
- [ ] Set operations: `Distinct`, `Union`, `Intersect`, `Except`; `Zip`
- [ ] Deferred vs immediate execution, multiple enumeration
- [ ] `IEnumerable` vs `IQueryable`
- [ ] Hidden costs of LINQ

## 6 · Git & GitHub

- [ ] Repository, working tree, staging, commits; `status`, `log`, `diff`
- [ ] Branches
- [ ] `merge` vs `rebase`, fast-forward
- [ ] Resolving conflicts
- [ ] Remotes: `clone`, `fetch`, `pull`, `push`
- [ ] Undoing: `restore`, `reset`, `revert`, `stash`
- [ ] Pull requests, code review, feature-branch workflow
- [ ] Good practice: small commits, clear messages, `.gitignore`

## 7 · HTTP & REST

- [ ] Anatomy of a request: method, URL, headers, body
- [ ] Verbs: GET, POST, PUT, PATCH, DELETE; safety and idempotency
- [ ] Status codes: the common ones and when to use them
- [ ] JSON, content negotiation
- [ ] REST principles, resource and URL design
- [ ] Statelessness, cookies vs tokens (concept), CORS (concept)
- [ ] API versioning and pagination

## 8 · ASP.NET Core Web API

- [ ] Project structure, `Program.cs`, the host
- [ ] Request pipeline and middleware (order, custom middleware)
- [ ] Routing; controllers vs Minimal APIs
- [ ] Model binding, DTOs, validation
- [ ] **Dependency injection**: what and why, registration, Transient/Scoped/Singleton, classic mistakes
- [ ] Configuration: `appsettings`, environments, the Options pattern
- [ ] Logging with `ILogger`
- [ ] Global error handling, ProblemDetails
- [ ] Correct responses and status codes
- [ ] Swagger / OpenAPI

## 9 · Entity Framework Core

- [ ] What an ORM solves and what it costs
- [ ] `DbContext`, `DbSet`, configuration and connection
- [ ] Modelling: entities, conventions, Fluent API, 1-1 / 1-N / N-N relationships
- [ ] Migrations
- [ ] Querying with LINQ: `IQueryable`, translation to SQL, projections
- [ ] Loading related data: `Include`, lazy loading, the N+1 problem
- [ ] Change tracking, `AsNoTracking`
- [ ] Saving, transactions, optimistic concurrency (concept)
- [ ] Raw SQL, and when to prefer Dapper

## 10 · Testing

- [ ] Why test; unit vs integration vs end-to-end
- [ ] xUnit: `Fact`, `Theory`, Arrange-Act-Assert
- [ ] Mocks and stubs, and when to mock
- [ ] Integration tests for an API with `WebApplicationFactory`
- [ ] Testing code that uses a database (concept)

## 11 · Design & architecture

- [ ] SOLID with concrete examples
- [ ] Common patterns: repository, factory, strategy, decorator, singleton (and why DI replaces it)
- [ ] Layered architecture, Clean Architecture, vertical slices (concepts)
- [ ] DTOs and mapping
- [ ] Clean code: naming, small methods, refactoring

## 12 · API security

- [ ] Authentication vs authorization
- [ ] JWT: structure, issuing, validation
- [ ] Role- and policy-based authorization
- [ ] Password hashing, secret management
- [ ] OWASP Top 10 for APIs (concepts)

## 13 · Docker

- [ ] Containers vs virtual machines
- [ ] A Dockerfile for a .NET API, multi-stage builds
- [ ] Images, containers, volumes, networks
- [ ] Docker Compose: API + database

## 14 · CI/CD & Azure

- [ ] CI/CD concepts, a GitHub Actions pipeline (build, test)
- [ ] Azure: App Service, Azure SQL, configuration and secrets
- [ ] Deploying a .NET API to Azure

## 15 · Agile & teamwork

- [ ] Scrum: roles, events, artifacts
- [ ] User stories, estimates, sprints
- [ ] Kanban (concept)
- [ ] Working in a team: PRs, code review, definition of done

## In parallel: Algorithms & LeetCode

Data structures, complexity and the common interview patterns (hash maps, two pointers, sliding window, binary search, trees, graphs…), solved in C#. Lessons are scheduled alongside the main course.

## At the end

- [ ] A portfolio project that uses everything above
- [ ] A full mock interview in English
