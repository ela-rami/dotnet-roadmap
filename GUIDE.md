# Guida per chi mi guida (persona o AI)

Questo file dice **come** guidarmi sessione per sessione. Il **perché** e le regole sono in [CONTEXT.md](CONTEXT.md), il **programma** in [COURSE.md](COURSE.md), lo **stato** in [PROGRESS.md](PROGRESS.md).

## All'inizio di ogni sessione

Leggi, in quest'ordine:

1. [CONTEXT.md](CONTEXT.md) — obiettivo, metodo, regole
2. [COURSE.md](COURSE.md) — moduli, checklist degli argomenti, come funzionano esami e lezioni
3. [PROGRESS.md](PROGRESS.md) — stato del corso, punto esatto in cui sono, log
4. La cartella del modulo in corso (`course/NN-nome/`): esami fatti, appunti delle lezioni
5. [leetcode/CONTEXT.md](leetcode/CONTEXT.md) — solo se lo step riguarda LeetCode

Poi rispondi alla mia domanda tipica: **"qual è il prossimo step?"**

Non rifare il piano e non propormi roadmap nuove: il corso è deciso. Il tuo lavoro è portarmi avanti nel corso.

## Come scegliere il prossimo step

1. **Qualcosa a metà?** Se un esame, una lezione o un esercizio è "in corso" in PROGRESS.md, si riprende da lì, dal punto esatto annotato.
2. **Altrimenti, il passo successivo del modulo in corso**, seguendo il flusso di COURSE.md: esame d'ingresso → correzione → studio dei soli argomenti 🟡/🔴 (un argomento alla volta) → esame finale.
3. **Alterna con LeetCode:** circa uno step ogni tre è LeetCode (dalla sua roadmap), per variare.
4. **Moduli in ordine.** Si passa al modulo successivo solo quando quello attuale è superato.

## Come presentare uno step

Breve, in italiano:

```
Step N — Modulo X: <titolo>
Cosa facciamo: <esame parte k/n · lezione su <argomento> · esercizio · esame finale>
Durata indicativa: <15–30 min>
```

Poi si parte subito.

## Come condurre un esame

- Segui le regole di [COURSE.md](COURSE.md#gli-esami): completo, diviso in parti, tipi di domanda mescolati, alcune in inglese.
- **Una domanda alla volta.** Aspetta la mia risposta prima di passare alla successiva. Non dare la soluzione subito.
- Alla fine di ogni parte: correzione argomento per argomento (cosa era giusto, cosa no, perché), con il livello 🟢/🟡/🔴.
- Sii severo: 🟢 solo se la risposta è giusta e so spiegare il perché. Meglio scoprire un buco ora che a un colloquio.

## Come condurre una lezione

- Un concetto per messaggio: spiegazione breve, esempio concreto, poi stop. Io scrivo "avanti" o faccio domande.
- Dopo ogni concetto, un mini esercizio che scrivo io.
- Link alla pagina Microsoft Learn di riferimento.
- **Il codice lo scrivo io.** Se sono bloccato: prima un indizio a parole, poi uno più preciso, solo alla fine la soluzione.
- Quando consegno codice: revisione (cosa va, cosa no, perché), poi mi chiedi di spiegarlo.
- Sii diretto sugli errori.

## Alla fine di ogni step: aggiornare il repo

Se hai accesso in scrittura, aggiorna tu; altrimenti dammi il testo da incollare.

1. **Nella cartella del modulo** (`course/NN-nome/`, creala se non c'è con un README che fa da indice):
   - `esami.md` — domande, mie risposte, correzione e livello per argomento
   - `lezioni.md` — appunti completi delle lezioni, con mie domande e correzioni
   - `esercizi/` — il mio codice, con in testa obiettivo, errori trovati in revisione e cosa ho imparato
2. **[PROGRESS.md](PROGRESS.md):** stato del corso, punto esatto da cui riprendere, una riga nel log.
3. **[REQUIREMENTS.md](REQUIREMENTS.md):** aggiorna il livello di un'area quando un modulo viene superato.
4. **LeetCode:** segui le regole di [leetcode/README.md](leetcode/README.md).
5. Commit con un messaggio chiaro (es. `Modulo 0: esame d'ingresso parte 1`).

Se ti racconto cose che ho imparato altrove (al lavoro, da un video…), annotale in PROGRESS.md.

## Revisione dei requisiti

Ogni 6–8 settimane (la data è in testa a [REQUIREMENTS.md](REQUIREMENTS.md)): controlla gli annunci reali junior .NET a Vienna e da remoto. Se emerge qualcosa che il corso non copre, proponi di aggiungerlo a COURSE.md.
