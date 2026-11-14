# Guida per chi mi guida (persona o AI)

Come guidarmi sessione per sessione. Il **perché** e le regole sono in [CONTEXT.md](CONTEXT.md), cosa va coperto in [docs/course-map.md](docs/course-map.md), lo **stato** in [PROGRESS.md](PROGRESS.md).

## All'inizio di ogni sessione

Leggi, in quest'ordine:

1. [CONTEXT.md](CONTEXT.md) — obiettivo, metodo, regole
2. [PROGRESS.md](PROGRESS.md) — dove sono, ultima lezione, esito degli esercizi, punti deboli
3. [docs/course-map.md](docs/course-map.md) — cosa è coperto e cosa manca
4. L'ultima lezione in `docs/` e i miei esercizi in `exercises/`
5. [leetcode/CONTEXT.md](leetcode/CONTEXT.md) — solo se si fa LeetCode

Le mie frasi tipiche: **"andiamo avanti"** / **"qual è il prossimo step?"**. Non rifare il piano e non propormi metodi nuovi: il metodo è deciso.

## Come scegliere la lezione successiva

Non c'è una scaletta. Ogni volta scegli tu, guardando:

1. **Esercizi in sospeso:** se non ho finito o consegnato gli esercizi dell'ultima lezione, prima quelli (revisione inclusa).
2. **Come sono andati gli esercizi:** se un concetto non è entrato, una lezione o un esercizio di rinforzo prima di andare avanti.
3. **I miei commenti** sulle lezioni.
4. **Argomenti arrugginiti:** riprendili dentro la lezione nuova, collegandoli a quello che si sta facendo.
5. **L'obiettivo:** colloqui da junior backend .NET. Prima le sezioni 1–9 (soglia di candidabilità), poi le altre.
6. **Diagnosi dall'archivio:** l'esame d'ingresso dell'8–9 novembre ([archive/](archive/esame-ingresso-modulo-0/esami.md)) mostra i buchi: overflow e `checked`, `++` prefisso/postfisso, `&` vs `&&`, boxing e `==` su `object`, riferimenti passati per valore, parametri nominati/opzionali, `out` e TryParse, collezioni oltre `List` e array (non le ricorda), stringhe immutabili. Insisti lì con gli esercizi.
7. **LeetCode:** decidi tu quando, non prima di aver ripreso le collezioni (sezione 1). Poi più o meno una sessione ogni tre, o un problema come esercizio di fine lezione quando c'entra.

## Come scrivere una lezione

Ogni lezione è una pagina Markdown **in inglese** in `docs/<sezione>/NN-titolo.md`, con questa struttura (vedi la lezione 1.1 come modello):

1. **Goals** (admonition `abstract`)
2. **Why this matters** — una riga sul perché serve ai colloqui o al lavoro
3. **Spiegazione** divisa in paragrafi numerati: un concetto alla volta, esempi concreti (meglio dal mondo industriale/gestionale), tabelle e diagrammi Mermaid dove aiutano
4. **"In an interview"** (admonition `question`): domanda tipica e risposta modello
5. **Common mistakes**
6. **Summary**
7. **Exercises**: piccoli, concreti, con tempi indicativi, output attesi, cartella dove salvarli (`exercises/<sezione>/<lezione>/`). Indizi solo in blocchi richiudibili (`??? tip`). **Mai la soluzione nella pagina.**
8. **Explain it**: domande da rispondere a parole, in inglese
9. **Official docs**: link Microsoft Learn

Stile: chiaro, diretto, al mio livello (laurea + un anno di lavoro), senza fronzoli. Verifica i fatti che cambiano nel tempo (versioni, supporto) prima di scriverli.

Dopo aver scritto una lezione:
- aggiungila al `nav` in [mkdocs.yml](mkdocs.yml) e alla tabella nell'`index.md` della sezione
- aggiorna "Latest lesson" e la tabella "Where I am" in [docs/index.md](docs/index.md)
- verifica con `mkdocs build --strict`
- commit e push: il sito si aggiorna da solo (GitHub Actions → branch `gh-pages`)

## Durante e dopo gli esercizi

- **Il codice lo scrivo io.** Se sono bloccato: prima un indizio a parole, poi uno più preciso, solo alla fine la soluzione.
- Quando consegno: revisione (cosa va, cosa no, perché), poi mi chiedi di spiegare quello che ho scritto. Sii diretto sugli errori.
- Lingua: in chat italiano (o inglese se scrivo in inglese); lezioni e risposte "Explain it" in inglese.
- Una domanda alla volta quando mi interroghi.

## Fine sezione

Quiz (domande dense al mio livello: "cosa stampa", teoria a parole in parte in inglese, bug da trovare) + un assignment realistico che combina gli argomenti della sezione. Risultati in PROGRESS.md.

## Alla fine di ogni sessione: aggiornare il repo

1. [PROGRESS.md](PROGRESS.md): lezione in corso, stato degli esercizi, punto esatto da cui riprendere, una riga nel log, punti deboli emersi.
2. [docs/course-map.md](docs/course-map.md): spunta gli argomenti coperti **e** esercitati.
3. Lezioni: correggi o arricchisci in base ai miei commenti.
4. [REQUIREMENTS.md](REQUIREMENTS.md): aggiorna un livello quando una sezione è chiusa.
5. Commit con un messaggio chiaro (es. `Lesson 1.2: types and conversions`).

## Revisione dei requisiti

Ogni 6–8 settimane (data in testa a [REQUIREMENTS.md](REQUIREMENTS.md)): controlla gli annunci reali junior .NET a Vienna e da remoto. Se emerge qualcosa che la mappa non copre, proponi di aggiungerlo.
