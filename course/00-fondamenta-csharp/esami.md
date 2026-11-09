# Modulo 0 — Esami

## Esame d'ingresso

### Parte A — Domande, blocco 1/3 (iniziato l'8 novembre 2026)

Argomenti del blocco: tipi e conversioni, overflow, operatori e uguaglianza, metodi e passaggio dei parametri.

#### Domanda 1 — conversioni, overflow, uguaglianza

```csharp
int a = 7, b = 2;
double r1 = a / b;
double r2 = (double)a / b;

int max = int.MaxValue;
int x = max + 1;

object o1 = 5, o2 = 5;
string s1 = "ciao";
string s2 = string.Concat("ci", "ao");

Console.WriteLine($"{r1} {r2}");   // riga 1
Console.WriteLine(x);              // riga 2
Console.WriteLine(o1 == o2);       // riga 3
Console.WriteLine(o1.Equals(o2));  // riga 4
Console.WriteLine(s1 == s2);       // riga 5
```

Bonus: cosa cambia con `checked(max + 1)`? E con `int.MaxValue + 1` scritto direttamente?

**Mie risposte (finali, 9 nov):**
1. `3, 3.5` — "il primo non è double ma il secondo sì"
2. "StackOverflow, perché supera il range massimo di memoria"
3. `True` — "entrambi sono di tipo object e puntano alla stessa zona di memoria"
4. `False` — "Equals per object controlla il valore"
5. `True` — "anche se string è un oggetto, == controlla solo il valore"
Bonus: non ancora risposto.

**Correzione:** a fine blocco.

#### Domanda 2 — metodi e passaggio dei parametri

**a)** Cosa stampa ogni riga, e perché?

```csharp
static void A(int n) { n = 10; }
static void B(ref int n) { n = 20; }
static void C(int[] arr) { arr[0] = 30; arr = new int[] { 99 }; }
static string Greet(string name, string greeting = "Hello") => $"{greeting}, {name}!";

int x = 1;
A(x);
Console.WriteLine(x);                                   // riga 1
B(ref x);
Console.WriteLine(x);                                   // riga 2

int[] nums = { 1, 2, 3 };
C(nums);
Console.WriteLine(nums[0]);                             // riga 3

Console.WriteLine(Greet(greeting: "Hi", name: "Elias")); // riga 4
```

**b)** Scrivere a mano `static bool TryParsePositive(string? s, out int value)`: `true` e il numero in `value` se `s` è un intero > 0; altrimenti `false` e `value = 0` (null, vuoto, testo, zero, negativi); non deve mai lanciare eccezioni. Più una riga che la chiama.

**Mie risposte (9 nov):**

a)
1. `5` — "A usa una copia del valore"
2. `10` — "cambia il valore originale con ref"
3. "Non sono sicuro"
4. `Hello Elias!` — "Hi è stato cambiato in Hello, e il metodo è direttamente dentro WriteLine"

b)
```csharp
static bool TryParsePositive(string? s, out int value){
if(int32.Parse(s) > 0){
value = s;
return true;
}
else{
value =  0;
reurn false;
}
int value = -1;
Console.WriteLine(TryParsePositive("5"));
Console.WriteLine(value);
```

**Correzione:** a fine blocco.

#### Domanda 3 — controllo di flusso e operatori

```csharp
int total = 0;
for (int i = 0; i < 10; i++)
{
    if (i % 2 == 0) continue;
    if (i > 7) break;
    total += i;
}
Console.WriteLine(total);                 // riga 1

int k = 5;
int y = k++ + ++k;
Console.WriteLine($"{k} {y}");            // riga 2

static string Classify(int temp) => temp switch
{
    < 0           => "freezing",
    >= 0 and < 20 => "cold",
    >= 20 and < 30 => "ok",
    _             => "hot"
};
Console.WriteLine(Classify(20));          // riga 3

static bool Check(string? s) => s != null && s.Length > 3;
Console.WriteLine(Check(null));           // riga 4
```

In più: cosa succede alla riga 4 se `&&` diventa `&`?

**Mie risposte (9 nov):**
1. `16` — "somma solo 1, 3, 5, 7: continue salta il valore, break esce dal ciclo"
2. "k = 7, y non so se 7+7 o 6+7"
3. `ok` — "temp rientra in >= 20 and < 30"
4. `False` — "s è null, e deve almeno essere non null per essere true"
In più: non risposto.

---

### Correzione del blocco 1 (9 novembre 2026)

**Domanda 1**

| Riga | Giusto | Mia risposta | Spiegazione |
| --- | --- | --- | --- |
| 1 | `3 3.5` (con cultura italiana: `3 3,5`) | `3 3.5` ✓ | `a / b` è una divisione **tra int**: fa 3 (tronca) e *dopo* viene convertita in double (3.0, stampato `3`). `r1` è un double, ma la divisione avviene prima dell'assegnazione. Con `(double)a` il cast avviene prima della divisione → 3.5. |
| 2 | `-2147483648` | StackOverflow ✗ | Overflow di un int in contesto *unchecked* (il default): il valore "fa il giro" e diventa `int.MinValue`. `int.MaxValue` = 2.147.483.647 = 2³¹−1. Lo StackOverflow non c'entra: riguarda lo stack delle chiamate (es. ricorsione infinita). |
| 3 | `False` | `True` ✗ | Assegnare un int a un `object` fa **boxing**: ogni assegnazione crea un oggetto nuovo sull'heap. `o1` e `o2` sono due box distinti, e `==` su `object` confronta i **riferimenti** → False. |
| 4 | `True` | `False` ✗ | `Equals` è virtuale: su un int boxato chiama `Int32.Equals`, che confronta i **valori** → True. (La spiegazione "controlla il valore" era giusta, la risposta no.) |
| 5 | `True` | `True` ✓ | `string` ridefinisce `==` per confrontare il contenuto, anche se `s2` è un oggetto diverso creato a runtime. |
| Bonus | `checked(...)` → `OverflowException` a runtime. `int.MaxValue + 1` scritto con costanti → **errore di compilazione**, perché il compilatore calcola le espressioni costanti e rileva l'overflow. | non risposto ✗ | |

**Domanda 2a**

| Riga | Giusto | Mia risposta | Spiegazione |
| --- | --- | --- | --- |
| 1 | `1` | `5` ✗ | Ragionamento giusto (A riceve una copia), ma `x` vale 1: ho letto male il valore. |
| 2 | `20` | `10` ✗ | Ragionamento giusto (con `ref` si modifica l'originale), ma B assegna 20, non 10. Di nuovo lettura frettolosa. |
| 3 | `30` | non sicuro ✗ | L'array è un tipo **riferimento**, ma il riferimento viene passato **per valore** (una copia dell'indirizzo). `arr[0] = 30` modifica l'array condiviso → il chiamante lo vede. `arr = new int[]{99}` cambia solo la copia locale del riferimento → il chiamante non lo vede. |
| 4 | `Hi, Elias!` | `Hello Elias!` ✗ | Argomenti **nominati**: l'ordine non conta, e passando `greeting: "Hi"` il valore di default `"Hello"` viene sostituito. Il default si usa solo se l'argomento manca. |

**Domanda 2b** — problemi:
- `int32` → `Int32` / `int`. Soprattutto `int.Parse` **lancia eccezioni** (null → `ArgumentNullException`, "abc" → `FormatException`, numero troppo grande → `OverflowException`): viola il requisito "non lanciare mai".
- `value = s;` assegna una string a un int → errore di compilazione.
- `reurn`, parentesi graffa di chiusura mancante.
- La chiamata deve passare l'argomento `out`: `TryParsePositive("5", out int n)`. Non si può chiamare senza.
- ✓ Giusto: assegnare `value` in tutti i rami (obbligatorio con `out`).

Soluzione di riferimento:

```csharp
static bool TryParsePositive(string? s, out int value)
{
    if (int.TryParse(s, out value) && value > 0)
        return true;

    value = 0;   // TryParse potrebbe aver messo un negativo, es. -5
    return false;
}

if (TryParsePositive("42", out int n))
    Console.WriteLine($"Valid: {n}");
```

`int.TryParse` accetta anche `null` (restituisce false) e non lancia mai eccezioni: è il pattern "Try" di .NET, da usare quando l'input può essere sbagliato.

**Domanda 3**

| Riga | Giusto | Mia risposta | Spiegazione |
| --- | --- | --- | --- |
| 1 | `16` | `16` ✓ | Spiegazione corretta. |
| 2 | `7 12` | k=7 ✓, y ✗ | `k++` restituisce il valore **vecchio** (5) e poi porta k a 6; `++k` incrementa **prima** (k=7) e restituisce 7. y = 5 + 7 = 12. |
| 3 | `ok` | `ok` ✓ | Switch expression con pattern relazionali, corretto. |
| 4 | `False` | `False` ✓ | Manca il punto chiave: `&&` è **short-circuit**. Se `s != null` è false, `s.Length` non viene valutato → nessuna eccezione. |
| In più | Con `&` vengono valutati **entrambi** i lati → `NullReferenceException`. | non risposto ✗ | |

**Nota generale:** due errori (2a righe 1 e 2) sono di lettura, non di concetto. Nei "cosa stampa" ai colloqui conviene seguire il codice riga per riga, con i valori annotati.

### Livelli dopo il blocco 1

| Argomento (checklist Modulo 0) | Livello |
| --- | --- |
| Tipi primitivi, conversioni e cast | 🟡 risultato giusto, spiegazione imprecisa |
| Overflow, `checked`, espressioni costanti | 🔴 |
| Operatori: `++` prefisso/postfisso | 🔴 |
| Operatori: short-circuit `&&` vs `&` | 🟡 |
| `==` vs `Equals`, boxing | 🔴 (string 🟢) |
| Controllo di flusso: cicli, `continue`/`break`, switch expression | 🟢 |
| Metodi: passaggio per valore e `ref` | 🟡 concetto giusto, valori letti male |
| Metodi: tipo riferimento passato per valore | 🔴 |
| Metodi: parametri opzionali e nominati | 🔴 |
| Metodi: `out` e pattern TryParse | 🔴 |
| Eccezioni di `Parse` vs `TryParse` | 🔴 (si riverifica nel blocco 3) |
