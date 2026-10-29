# Guida per chi mi guida (persona o AI)

Questo file dice **come** guidarmi sessione per sessione. Il **perché** e le regole sono in [CONTEXT.md](CONTEXT.md), lo **stato** in [PROGRESS.md](PROGRESS.md).

## All'inizio di ogni sessione

Leggi, in quest'ordine:

1. [CONTEXT.md](CONTEXT.md) — obiettivo, metodo, regole
2. [PROGRESS.md](PROGRESS.md) — stato attuale, ultimo step, tabella "ultima volta", log
3. [REQUIREMENTS.md](REQUIREMENTS.md) — requisiti e mio livello su ogni voce
4. [leetcode/CONTEXT.md](leetcode/CONTEXT.md) — solo se lo step riguarda LeetCode

Poi rispondi alla mia domanda tipica: **"qual è il prossimo step?"**

Non rifare il piano e non propormi roadmap nuove: il metodo è deciso. Il tuo lavoro è scegliere il passo giusto adesso.

## Come scegliere il prossimo step

Applica queste regole in ordine:

1. **Step a metà?** Se l'ultimo step nel log è "in corso", si riprende da lì, dal punto esatto annotato.
2. **Verifica dovuta?** Se dall'ultima verifica sono passati 6–8 step, il prossimo step è una verifica (vedi sotto).
3. **Argomento arrugginito?** Se un argomento Must già lavorato non si tocca da più di ~2 settimane (colonna "ultima volta"), inseriscilo, meglio se collegato a quello che sto facendo.
4. **Lacuna Must più grave.** Altrimenti scegli tra le voci Must con livello 🔴 o 🟠, partendo dalla più importante per i colloqui.
5. **Alterna.** Non due step di fila sulla stessa area, se si può evitare. LeetCode circa uno step ogni 3.
6. **Piccolo e isolato prima, combinato dopo.** Un concetto nuovo si esercita da solo; quando è solido si combina con altri in task più grandi, fino al progetto vero.

Indicativamente: Must prima di tutto; Should solo quando i Must sono almeno 🟡; frontend solo dopo il backend.

## Come presentare uno step

Breve, in italiano, con questo schema:

```
Step N — <Area>: <titolo>
Perché adesso: <una riga>
Obiettivo: <cosa devo saper fare alla fine>
Task: <cosa scrivere/fare, concreto e piccolo>
Durata indicativa: <15–45 min>
Dove salvarlo: <cartella/file>
```

Se lo step introduce un concetto che non conosco, prima una spiegazione corta con un caso concreto (meglio se dal mondo gestionale/industriale), poi il task. Se è solo teoria (es. Agile, merge vs rebase), il "task" è spiegarlo io a parole dopo la lezione.

## Durante lo step

- **Il codice lo scrivo io.** Non darmi la soluzione prima che ci abbia provato.
- Se sono bloccato: prima un indizio a parole, poi un indizio più preciso, solo alla fine la soluzione.
- Quando consegno: revisiona (cosa va, cosa no, perché), poi chiedimi di **spiegare** quello che ho scritto.
- Sii diretto sugli errori: preferisco saperlo.
- Lingua: si parla in italiano; le lezioni di teoria LeetCode sono in inglese; le domande di verifica ogni tanto in inglese.

## Le verifiche

Ogni 6–8 step, un mini colloquio simulato:

- 2–3 domande di teoria a cui rispondo a parole (almeno una in inglese)
- un piccolo esercizio di codice a tempo
- una query SQL

Mescola argomenti diversi tra quelli già fatti. Il risultato va in [PROGRESS.md](PROGRESS.md#verifiche) e i livelli in [REQUIREMENTS.md](REQUIREMENTS.md) si aggiornano.

## Alla fine di ogni step: aggiornare il repo

Se hai accesso in scrittura al repo, aggiorna tu; altrimenti dammi il testo da incollare.

1. **Il lavoro fatto** nella cartella dell'area (`csharp/`, `backend/`, `sql/`, `git/`, `leetcode/problems/`), un file per step: `NN-argomento.md` o `NN-argomento.cs`. In testa al file: obiettivo, il mio codice, gli errori trovati in revisione, cosa ho imparato. Se la cartella non esiste, creala con un README che fa da indice.
2. **[PROGRESS.md](PROGRESS.md):** una riga nel log (numero, data, area, step, esito: fatto / in corso con il punto esatto da cui riprendere), la data in "ultima volta", lo "Stato attuale" e il "Prossimo step" se è già chiaro.
3. **[REQUIREMENTS.md](REQUIREMENTS.md):** cambia un livello solo se c'è un'evidenza (esercizio fatto bene da solo, verifica).
4. **LeetCode:** segui le regole di aggiornamento di [leetcode/README.md](leetcode/README.md).
5. Commit con un messaggio chiaro (es. `Step 3: LINQ GroupBy con l'SQL come ponte`).

Se nella sessione ti racconto cose che ho imparato altrove (al lavoro, da un video…), annotale anche quelle in PROGRESS.md.

## Revisione dei requisiti

Ogni 6–8 settimane (la data è in testa a [REQUIREMENTS.md](REQUIREMENTS.md)): controlla gli annunci reali junior .NET a Vienna e da remoto, e aggiorna voci e priorità. Non a ogni sessione.
