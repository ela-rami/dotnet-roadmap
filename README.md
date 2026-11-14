# Self-learn — Backend .NET

Il mio percorso per diventare un **backend developer .NET/C# junior** candidabile sul mercato internazionale (inglese), con l'obiettivo di lavorare a Vienna o da remoto.

È un corso da zero, costruito una lezione alla volta. Le lezioni (in inglese) sono un sito: **https://ela-rami.github.io/dotnet-roadmap/**

## Da dove partire

Se stai riprendendo il percorso (io, una persona o un'AI senza contesto):

1. **[CONTEXT.md](CONTEXT.md)** — chi sono, obiettivo, metodo e regole
2. **[GUIDE.md](GUIDE.md)** — come guidarmi: scegliere la lezione successiva, scriverla, aggiornare il repo
3. **[PROGRESS.md](PROGRESS.md)** — dove sono e punto esatto da cui riprendere
4. **[docs/course-map.md](docs/course-map.md)** — cosa il corso deve coprire e cosa è già coperto
5. **[REQUIREMENTS.md](REQUIREMENTS.md)** — cosa chiedono gli annunci e il mio livello su ogni voce

Per iniziare una nuova chat basta passare il link del repo e chiedere: *"Leggi CLAUDE.md e andiamo avanti"*.

## Struttura

```
dotnet-roadmap/
├── README.md          → questa pagina
├── CLAUDE.md          → punto di ingresso per un'AI
├── CONTEXT.md         → obiettivo, metodo, regole
├── GUIDE.md           → come guidarmi sessione per sessione
├── PROGRESS.md        → dove sono, log
├── REQUIREMENTS.md    → requisiti degli annunci e mio livello
├── mkdocs.yml         → configurazione del sito
├── docs/              → le lezioni (il sito): una cartella per sezione
├── exercises/         → le mie soluzioni agli esercizi
├── leetcode/          → algoritmi e LeetCode in C#
├── archive/           → materiale dei metodi precedenti (esame d'ingresso di novembre)
└── localquest/        → roadmap PDF precedenti, SideQuest
```

Il sito si pubblica da solo a ogni push su `main` (GitHub Actions → branch `gh-pages` → GitHub Pages). Per vederlo in locale: `pip install -r requirements.txt` e `mkdocs serve`.

## Come si aggiorna

- A ogni lezione: la pagina in `docs/`, i miei esercizi in `exercises/`, stato e punto esatto in [PROGRESS.md](PROGRESS.md), argomenti spuntati in [docs/course-map.md](docs/course-map.md).
- A ogni sezione chiusa: il livello aggiornato in [REQUIREMENTS.md](REQUIREMENTS.md).
- Ogni 6–8 settimane: revisione dei requisiti in base agli annunci reali.
