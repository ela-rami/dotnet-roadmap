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

*(in corso)*
