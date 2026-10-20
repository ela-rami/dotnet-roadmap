# Roadmap LeetCode in C#

*v2 — 20 ottobre 2026 · Obiettivo: colloqui tecnici junior (.NET/C#)*

## Indice

1. [Come usarla](#come-usarla)
2. [Metodo](#metodo)
3. [Cheat sheet C# per LeetCode](#cheat-sheet-c-per-leetcode)
4. [Livello 1 — Soglia colloqui junior](#livello-1--soglia-colloqui-junior-47-problemi) (Fasi 0–6)
5. [Livello 2 — Colloqui più tecnici](#livello-2--colloqui-più-tecnici-38-problemi) (Fasi 7–11)
6. [Extra opzionali](#extra-opzionali-7-problemi) (Fase 12)
7. [Verifiche e traccia SQL](#verifiche-e-traccia-sql)

---

## Come usarla

92 problemi in 13 fasi, ordinati per pattern e risolti in C#. Ogni fase ha due parti: prima la **teoria da sapere**, poi i **problemi**.

| Blocco | Fasi | Problemi | Ore stimate |
| --- | --- | --- | --- |
| Livello 1 — soglia colloqui junior | 0–6 | 47 | ~42 |
| Livello 2 — colloqui più tecnici | 7–11 | 38 | ~39 |
| Extra opzionali | 12 | 7 | ~7 |

Non c'è un calendario fisso: il ritmo lo decidi settimana per settimana. Conta la costanza, non il volume: due sessioni da un'ora a settimana battono una maratona al mese.

| Ritmo | Ore a settimana | Livello 1 | Livelli 1 + 2 |
| --- | --- | --- | --- |
| Minimo | 2 | ~21 settimane | ~41 settimane |
| Leggero | 3 | ~14 settimane | ~27 settimane |
| Medio | 5 | ~9 settimane | ~16 settimane |
| Intenso | 8 | ~5 settimane | ~10 settimane |

Stime approssimative: circa 30 minuti per un Easy e 60 per un Medium, ripassi inclusi. Nelle settimane in cui SideQuest ha la priorità, scendi al ritmo minimo invece di fermarti.

Legenda: **E** = Easy, **M** = Medium. Tra parentesi accanto alla teoria, le parole chiave in inglese per cercare video o articoli.

---

## Metodo

L'obiettivo non è collezionare problemi risolti, ma riconoscere il pattern e saperlo scrivere a mano sotto pressione.

### Teoria

1. **Lezioni in inglese, un piccolo concetto alla volta.** Si avanza solo quando il passo precedente è chiaro.
2. **Appunti completi nel repo**, una lezione per file (`lessons/`): tutto quello che è stato spiegato, non un riassunto, comprese domande, risposte e correzioni.
3. **Check di fine lezione.** Domande di verifica prima di passare alla lezione successiva.
4. Se un concetto lo sai già spiegare a voce con la sua complessità, passa direttamente ai problemi.

### Problemi

1. **Prima del codice (5 min).** Riformula il problema, prova 2 esempi a mano, elenca i casi limite (input vuoto, un elemento, duplicati, negativi). Descrivi la soluzione brute force e la sua complessità.
2. **Timebox.** Easy: 20 minuti senza aiuti. Medium: 35 minuti.
3. **Se sei bloccato.** Un solo hint, poi altri 10–15 minuti. Ancora bloccato: leggi la soluzione, capiscila, chiudila e riscrivila da zero senza guardare.
4. **Regola AI.** L'AI non scrive il codice delle soluzioni: può dare un hint a parole, spiegare un concetto o revisionare la tua soluzione.
5. **Dopo.** In testa al file scrivi pattern, complessità tempo/spazio e l'idea chiave in una frase. Salva la soluzione in `problems/`.
6. **Ripasso.** Ogni problema risolto con aiuto lo rifai dopo 3 giorni e dopo 2 settimane. Spunta la casella solo quando lo risolvi da solo.
7. **Ad alta voce, in inglese.** Spiega il ragionamento mentre scrivi: è come si svolge un colloquio internazionale.
8. **Niente autocompletamento.** Nei colloqui spesso scrivi su un editor semplice: abituati a ricordare nomi e firme dei metodi.

---

## Cheat sheet C# per LeetCode

| Struttura | Tipo C# | Operazioni chiave | Attenzione |
| --- | --- | --- | --- |
| Array dinamico | `List<T>` | `Add`, `Count`, `list[i]`, `Insert`, `RemoveAt` | `Insert`/`RemoveAt` in mezzo costano O(n) |
| Hash map | `Dictionary<K,V>` | `TryGetValue`, `GetValueOrDefault`, `ContainsKey`, `d[k] = v` | Leggere `d[k]` con chiave assente lancia `KeyNotFoundException` |
| Hash set | `HashSet<T>` | `Add`, `Contains`, `Remove` | `Add` restituisce `false` se l'elemento c'era già: utile per i duplicati |
| Stack | `Stack<T>` | `Push`, `Pop`, `Peek`, `Count` | `Pop`/`Peek` su stack vuoto lanciano eccezione: controlla `Count` |
| Coda (BFS) | `Queue<T>` | `Enqueue`, `Dequeue`, `Count` | Per le coordinate usa le tuple: `Queue<(int r, int c)>` |
| Heap | `PriorityQueue<TElement,TPriority>` | `Enqueue(e, p)`, `Dequeue`, `Peek`, `Count` | È un min-heap; per il max-heap nega la priorità o passa un comparer inverso |
| Stringhe | `StringBuilder` | `Append`, `Insert`, `ToString` | `string` è immutabile: concatenare in un ciclo costa O(n²) |
| Ordinamento | `Array.Sort`, `List<T>.Sort` | `Array.Sort(iv, (a, b) => a[0].CompareTo(b[0]))` | O(n log n), non stabile |
| Caratteri | `char`, `int[26]` | `char.IsLetterOrDigit`, `char.ToLower`, `c - 'a'` | Un array da 26 è più veloce di un dizionario per gli anagrammi |

Altri metodi utili: `s.ToCharArray()` e `new string(chars)` per modificare una stringa per indice, `string.Join(",", list)`, `Array.Fill(arr, -1)`, `int.MaxValue` / `int.MinValue` come valori iniziali per minimi e massimi, `Math.Max` / `Math.Min` / `Math.Abs`.

Trappole frequenti:

- **Overflow.** Nella binary search usa `mid = left + (right - left) / 2`; per somme e prodotti grandi usa `long`.
- **LINQ.** Comodo, ma nasconde i costi (`OrderBy` è O(n log n), `Contains` su una lista è O(n)). In colloquio devi saper scrivere anche senza.
- **Lunghezze.** `string.Length` e `array.Length`, ma `List.Count`: errore classico senza autocompletamento.
- **Matrici.** LeetCode usa array frastagliati `int[][]` (`grid[r][c]`, `grid[0].Length`), non `int[,]`.
- **Null.** Liste e alberi: controlla sempre `node == null` prima di accedere a `.next` o `.left`.

---

## Livello 1 — Soglia colloqui junior (47 problemi)

### Fase 0 — Fondamenta e classici da colloquio .NET

Stringhe, cicli, indici e ricorsione: è quello che chiedono più spesso nei colloqui junior C#.

**Teoria da sapere**

*Big-O* (cerca: *Big O notation*, *amortized analysis*)
- Cosa misura: la crescita del costo al crescere dell'input, non i secondi
- Regole: togliere costanti e termini di ordine inferiore; passi in sequenza si sommano, annidati si moltiplicano; input diversi hanno variabili diverse (O(a + b), O(a · b)); la base del logaritmo non conta
- Le classi comuni: O(1), O(log n), O(n), O(n log n), O(n²), O(2ⁿ), O(n!)
- Usare i vincoli del problema per capire la complessità richiesta
- Costi nascosti in C# (`List.Contains`, concatenazione di stringhe, `Substring`, `Insert(0, x)`, `ToList`)
- Caso migliore, medio e peggiore; complessità ammortizzata
- Complessità in spazio, incluso lo stack della ricorsione
- Come esporre tempo, spazio e trade-off in un colloquio

*Array e stringhe* (cerca: *array memory layout*, *dynamic array*, *string immutability*)
- Array in memoria: blocco contiguo, dimensione fissa, elementi dello stesso tipo
- Perché l'accesso per indice è O(1) (calcolo dell'indirizzo) e perché gli indici partono da 0
- Perché inserire o cancellare in mezzo è O(n) (spostamento degli elementi) e in fondo è O(1)
- Array dinamico (`List<T>`): Count contro Capacity, raddoppio della capacità, `Add` O(1) ammortizzato
- Stringa come sequenza di `char`; `char` contro `string`; un `char` è un numero (`'c' - 'a' = 2`)
- Immutabilità delle stringhe: ogni "modifica" crea una nuova stringa; il trucco `ToCharArray` / `new string(...)`
- La trappola della concatenazione nei cicli e `StringBuilder`
- Tecniche in-place su array: scrittura con un indice separato, scambio di elementi

*Ricorsione* (cerca: *recursion*, *call stack*, *memoization*)
- Caso base e chiamata ricorsiva
- Lo stack delle chiamate e come tracciare a mano una ricorsione
- Ricorsione contro iterazione; rischio di `StackOverflowException`
- Introduzione alla memoization (es. Fibonacci da O(2ⁿ) a O(n))

**Problemi**

- [ ] [412. Fizz Buzz](https://leetcode.com/problems/fizz-buzz/) · E
- [ ] [344. Reverse String](https://leetcode.com/problems/reverse-string/) · E
- [ ] [9. Palindrome Number](https://leetcode.com/problems/palindrome-number/) · E
- [ ] [13. Roman to Integer](https://leetcode.com/problems/roman-to-integer/) · E
- [ ] [14. Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/) · E
- [ ] [387. First Unique Character in a String](https://leetcode.com/problems/first-unique-character-in-a-string/) · E
- [ ] [26. Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/) · E
- [ ] [283. Move Zeroes](https://leetcode.com/problems/move-zeroes/) · E
- [ ] [509. Fibonacci Number](https://leetcode.com/problems/fibonacci-number/) · E — risolvilo in tre modi: ricorsivo, con memoization, iterativo

### Fase 1 — Array e hashing

Scambiare memoria per tempo: da O(n²) a O(n) con `Dictionary` e `HashSet`.

**Teoria da sapere** (cerca: *hash table explained*, *hash collisions*, *bucket sort*)

- Come funziona una hash table: funzione hash, bucket, indice calcolato dalla chiave
- Collisioni: chaining e open addressing
- Load factor e ridimensionamento della tabella
- Perché la ricerca costa O(1) in media e O(n) nel caso peggiore
- In C#: `GetHashCode` ed `Equals`, e perché contano quando usi oggetti o tuple come chiavi
- Differenza tra `Dictionary` (chiave → valore) e `HashSet` (solo chiavi)
- Contare le frequenze con un dizionario; il bucket sort come alternativa all'ordinamento

**Problemi**

- [ ] [1. Two Sum](https://leetcode.com/problems/two-sum/) · E
- [ ] [217. Contains Duplicate](https://leetcode.com/problems/contains-duplicate/) · E
- [ ] [242. Valid Anagram](https://leetcode.com/problems/valid-anagram/) · E
- [ ] [49. Group Anagrams](https://leetcode.com/problems/group-anagrams/) · M
- [ ] [347. Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/) · M
- [ ] [238. Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/) · M
- [ ] [128. Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/) · M

### Fase 2 — Two pointers

Due indici che si muovono verso il centro o nella stessa direzione, di solito su input ordinato.

**Teoria da sapere** (cerca: *two pointers technique*)

- Puntatori convergenti (uno all'inizio, uno alla fine) contro puntatori nella stessa direzione
- Perché su un array ordinato riducono O(n²) a O(n)
- Come evitare i duplicati nei risultati (3Sum)

**Problemi**

- [ ] [125. Valid Palindrome](https://leetcode.com/problems/valid-palindrome/) · E
- [ ] [167. Two Sum II](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/) · M
- [ ] [15. 3Sum](https://leetcode.com/problems/3sum/) · M
- [ ] [11. Container With Most Water](https://leetcode.com/problems/container-with-most-water/) · M

### Fase 3 — Sliding window e prefix sum

Sottoarray e sottostringhe contigue senza ricalcolare tutto a ogni passo.

**Teoria da sapere** (cerca: *sliding window technique*, *prefix sum*)

- Finestra di dimensione fissa contro finestra variabile (allarga a destra, restringi a sinistra)
- Prefix sum: precalcolare le somme per avere la somma di un intervallo in O(1)
- Prefix sum + hash map per contare i sottoarray con una certa somma

**Problemi**

- [ ] [121. Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/) · E
- [ ] [643. Maximum Average Subarray I](https://leetcode.com/problems/maximum-average-subarray-i/) · E
- [ ] [724. Find Pivot Index](https://leetcode.com/problems/find-pivot-index/) · E
- [ ] [3. Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/) · M
- [ ] [424. Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/) · M
- [ ] [567. Permutation in String](https://leetcode.com/problems/permutation-in-string/) · M
- [ ] [560. Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/) · M

### Fase 4 — Stack e code

Tutto ciò che "si apre e si chiude" o cerca il prossimo elemento più grande.

**Teoria da sapere** (cerca: *stack and queue*, *monotonic stack*)

- Stack (LIFO) e coda (FIFO): operazioni, complessità O(1), usi tipici
- Implementare una coda con due stack (costo ammortizzato) — domanda classica
- Monotonic stack: trovare il prossimo elemento più grande o più piccolo in O(n)

**Problemi**

- [ ] [20. Valid Parentheses](https://leetcode.com/problems/valid-parentheses/) · E
- [ ] [232. Implement Queue using Stacks](https://leetcode.com/problems/implement-queue-using-stacks/) · E
- [ ] [155. Min Stack](https://leetcode.com/problems/min-stack/) · M
- [ ] [150. Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/) · M
- [ ] [739. Daily Temperatures](https://leetcode.com/problems/daily-temperatures/) · M

### Fase 5 — Ordinamento e binary search

Dimezzare lo spazio di ricerca, anche quando non è un array ma un intervallo di risposte possibili.

**Teoria da sapere** (cerca: *sorting algorithms*, *merge sort*, *quick sort*, *binary search template*)

- Algoritmi di ordinamento: bubble e insertion sort (O(n²)), merge sort e quick sort (O(n log n)); saperli spiegare e confrontare
- Stabilità e ordinamento in-place; `Array.Sort` in .NET è un introsort, non stabile
- Binary search su array ordinato: O(log n), gestione di `left`, `right` e della condizione del ciclo
- Binary search sulla risposta: cercare il valore minimo che soddisfa una condizione

**Problemi**

- [ ] [704. Binary Search](https://leetcode.com/problems/binary-search/) · E
- [ ] [35. Search Insert Position](https://leetcode.com/problems/search-insert-position/) · E
- [ ] [912. Sort an Array](https://leetcode.com/problems/sort-an-array/) · M — implementa tu il merge sort, senza `Array.Sort`
- [ ] [74. Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/) · M
- [ ] [875. Koko Eating Bananas](https://leetcode.com/problems/koko-eating-bananas/) · M
- [ ] [153. Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/) · M
- [ ] [33. Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/) · M

### Fase 6 — Linked list

Puntatori, nodi fittizi (dummy) e la tecnica lento/veloce.

**Teoria da sapere** (cerca: *linked list*, *Floyd cycle detection*, *LRU cache*)

- Lista concatenata singola e doppia: struttura del nodo, accesso O(n), inserimento O(1) se hai il nodo
- Array contro linked list: quando conviene l'uno o l'altra (domanda classica)
- Nodo dummy, puntatori lento/veloce (algoritmo di Floyd)
- LRU cache: hash map + lista doppia, entrambe le operazioni in O(1)

**Problemi**

- [ ] [206. Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/) · E
- [ ] [21. Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/) · E
- [ ] [141. Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/) · E
- [ ] [876. Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/) · E
- [ ] [19. Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/) · M
- [ ] [143. Reorder List](https://leetcode.com/problems/reorder-list/) · M
- [ ] [2. Add Two Numbers](https://leetcode.com/problems/add-two-numbers/) · M
- [ ] [146. LRU Cache](https://leetcode.com/problems/lru-cache/) · M

---

## Livello 2 — Colloqui più tecnici (38 problemi)

### Fase 7 — Alberi binari

Ricorsione, DFS e BFS: la fase più lunga, ma dopo i primi tre problemi lo schema si ripete.

**Teoria da sapere** (cerca: *binary tree traversal*, *binary search tree*)

- Terminologia: radice, foglia, altezza, profondità, albero bilanciato
- Visite DFS: preorder, inorder, postorder, in versione ricorsiva e iterativa con `Stack`
- Visita BFS per livelli con `Queue`
- Lo schema ricorsivo "calcola sui figli, combina nel padre" (altezza, diametro, bilanciamento)
- BST: proprietà sinistra < nodo < destra, ricerca O(log n) se bilanciato e O(n) se degenere; la visita inorder restituisce i valori ordinati

**Problemi**

- [ ] [226. Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/) · E
- [ ] [104. Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/) · E
- [ ] [100. Same Tree](https://leetcode.com/problems/same-tree/) · E
- [ ] [572. Subtree of Another Tree](https://leetcode.com/problems/subtree-of-another-tree/) · E
- [ ] [543. Diameter of Binary Tree](https://leetcode.com/problems/diameter-of-binary-tree/) · E
- [ ] [110. Balanced Binary Tree](https://leetcode.com/problems/balanced-binary-tree/) · E
- [ ] [102. Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/) · M
- [ ] [199. Binary Tree Right Side View](https://leetcode.com/problems/binary-tree-right-side-view/) · M
- [ ] [98. Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/) · M
- [ ] [235. Lowest Common Ancestor of a BST](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/) · M
- [ ] [230. Kth Smallest Element in a BST](https://leetcode.com/problems/kth-smallest-element-in-a-bst/) · M

### Fase 8 — Heap

"I k elementi più grandi o più vicini" si risolve quasi sempre con `PriorityQueue`.

**Teoria da sapere** (cerca: *heap data structure*, *heapify*, *priority queue*)

- Heap binario min e max, rappresentato come array (figli di `i` in `2i + 1` e `2i + 2`)
- Sift up e sift down
- Complessità: inserimento ed estrazione O(log n), lettura del minimo O(1), costruzione O(n)
- Top K con un heap di dimensione k: O(n log k) invece di ordinare tutto

**Problemi**

- [ ] [703. Kth Largest Element in a Stream](https://leetcode.com/problems/kth-largest-element-in-a-stream/) · E
- [ ] [1046. Last Stone Weight](https://leetcode.com/problems/last-stone-weight/) · E
- [ ] [215. Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/) · M
- [ ] [973. K Closest Points to Origin](https://leetcode.com/problems/k-closest-points-to-origin/) · M

### Fase 9 — Grafi e griglie

DFS e BFS su matrici e su liste di adiacenza, più l'ordinamento topologico.

**Teoria da sapere** (cerca: *graph BFS DFS*, *topological sort*)

- Terminologia: nodi, archi, grafi orientati e non orientati, pesati e non pesati
- Rappresentazioni: lista di adiacenza contro matrice di adiacenza
- DFS e BFS su un grafo, con l'insieme dei nodi visitati
- Una griglia è un grafo: 4 vicini per cella, marcare le celle visitate
- BFS per il cammino minimo su grafi non pesati; BFS da più sorgenti
- Ordinamento topologico (algoritmo di Kahn) e rilevazione dei cicli
- Dijkstra e Union-Find: basta sapere a cosa servono, non implementarli

**Problemi**

- [ ] [733. Flood Fill](https://leetcode.com/problems/flood-fill/) · E
- [ ] [200. Number of Islands](https://leetcode.com/problems/number-of-islands/) · M
- [ ] [695. Max Area of Island](https://leetcode.com/problems/max-area-of-island/) · M
- [ ] [133. Clone Graph](https://leetcode.com/problems/clone-graph/) · M
- [ ] [994. Rotting Oranges](https://leetcode.com/problems/rotting-oranges/) · M
- [ ] [207. Course Schedule](https://leetcode.com/problems/course-schedule/) · M

### Fase 10 — Backtracking

Generare tutte le combinazioni: scegli, esplora, annulla la scelta.

**Teoria da sapere** (cerca: *backtracking*)

- L'albero delle decisioni: scegli, esplora, annulla la scelta
- Complessità esponenziale: 2ⁿ sottoinsiemi, n! permutazioni
- Potatura: interrompere un ramo appena non può portare a una soluzione

**Problemi**

- [ ] [78. Subsets](https://leetcode.com/problems/subsets/) · M
- [ ] [46. Permutations](https://leetcode.com/problems/permutations/) · M
- [ ] [39. Combination Sum](https://leetcode.com/problems/combination-sum/) · M
- [ ] [22. Generate Parentheses](https://leetcode.com/problems/generate-parentheses/) · M
- [ ] [79. Word Search](https://leetcode.com/problems/word-search/) · M

### Fase 11 — Programmazione dinamica, greedy e intervalli

La più difficile: parti sempre dalla ricorsione, poi aggiungi la memoization, solo alla fine la tabella.

**Teoria da sapere** (cerca: *dynamic programming*, *memoization*, *tabulation*, *greedy algorithm*)

- Programmazione dinamica: sottoproblemi sovrapposti e sottostruttura ottima
- Memoization (top-down, ricorsione + cache) contro tabulation (bottom-up, tabella)
- DP a una dimensione e a due dimensioni (griglie, due stringhe)
- Greedy: la scelta migliore a ogni passo, e perché a volte non basta
- Intervalli: ordinare per inizio, poi unire o contare le sovrapposizioni

**Problemi**

- [ ] [70. Climbing Stairs](https://leetcode.com/problems/climbing-stairs/) · E
- [ ] [746. Min Cost Climbing Stairs](https://leetcode.com/problems/min-cost-climbing-stairs/) · E
- [ ] [198. House Robber](https://leetcode.com/problems/house-robber/) · M
- [ ] [53. Maximum Subarray](https://leetcode.com/problems/maximum-subarray/) · M
- [ ] [322. Coin Change](https://leetcode.com/problems/coin-change/) · M
- [ ] [300. Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/) · M
- [ ] [62. Unique Paths](https://leetcode.com/problems/unique-paths/) · M
- [ ] [1143. Longest Common Subsequence](https://leetcode.com/problems/longest-common-subsequence/) · M
- [ ] [55. Jump Game](https://leetcode.com/problems/jump-game/) · M
- [ ] [56. Merge Intervals](https://leetcode.com/problems/merge-intervals/) · M
- [ ] [57. Insert Interval](https://leetcode.com/problems/insert-interval/) · M
- [ ] [435. Non-overlapping Intervals](https://leetcode.com/problems/non-overlapping-intervals/) · M

---

## Extra opzionali (7 problemi)

### Fase 12 — Matrici, bit e trie

Argomenti meno frequenti nei colloqui junior, ma che compaiono: da fare quando hai finito il Livello 2, o prima se un'azienda li chiede.

**Teoria da sapere** (cerca: *matrix traversal*, *bit manipulation*, *trie data structure*)

- Matrici: visita per righe, colonne e a spirale; trasformazioni in-place (trasposta + inversione delle righe)
- Operatori sui bit: `&`, `|`, `^`, `~`, `<<`, `>>`; proprietà dello XOR (`x ^ x = 0`, `x ^ 0 = x`); il trucco `n & (n - 1)`
- Trie (albero dei prefissi): struttura del nodo, inserimento e ricerca in O(lunghezza della parola)

**Problemi**

- [ ] [136. Single Number](https://leetcode.com/problems/single-number/) · E
- [ ] [191. Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/) · E
- [ ] [268. Missing Number](https://leetcode.com/problems/missing-number/) · E
- [ ] [48. Rotate Image](https://leetcode.com/problems/rotate-image/) · M
- [ ] [54. Spiral Matrix](https://leetcode.com/problems/spiral-matrix/) · M
- [ ] [73. Set Matrix Zeroes](https://leetcode.com/problems/set-matrix-zeroes/) · M
- [ ] [208. Implement Trie (Prefix Tree)](https://leetcode.com/problems/implement-trie-prefix-tree/) · M

---

## Verifiche e traccia SQL

**Verifica di fine fase.** Scegli dalla lista "Similar Questions" di LeetCode un problema nuovo dello stesso pattern. 35 minuti, nessun aiuto, ragionamento ad alta voce in inglese. Se non lo chiudi, ripassa i problemi della fase segnati con aiuto prima di andare avanti.

**Simulazione dopo la Fase 6.** Due problemi nuovi in 60 minuti (un Easy e un Medium), con timer, spiegando approccio e complessità come davanti a un intervistatore. Meglio ancora con un amico che fa le domande.

**Simulazione dopo la Fase 11.** Stessa formula, con due Medium.

**Traccia SQL (opzionale, in parallelo).** Lo study plan SQL 50 di LeetCode, un paio di query a sessione. Usa lo stesso dialetto di SideQuest (SQL Server o PostgreSQL). Focus su JOIN, GROUP BY con HAVING, subquery e window function.
