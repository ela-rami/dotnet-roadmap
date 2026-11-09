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

*(in corso)*
