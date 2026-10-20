# Lesson 1 — Big-O notation

*Phase 0 · Date: 12 October 2026 · Status: completed (check questions answered and corrected)*

← [Back to index](../README.md) · Next: [Lesson 2 — Arrays and strings](02-arrays-strings.md)

---

## 1. What Big-O actually measures

Big-O describes **how the cost of an algorithm grows as the input size grows**. It doesn't measure seconds, which depend on the machine, the language and the compiler. It measures the *shape* of the growth: if I double the input, does the work stay the same, double, or quadruple?

- **n** is the size of the input: the length of an array, the number of characters in a string, the number of nodes in a tree.
- **Time complexity** counts basic operations (comparisons, assignments, arithmetic).
- **Space complexity** counts the *extra* memory the algorithm uses.

Formally, Big-O is an **upper bound**. In practice, in interviews "the Big-O" means the tight worst-case bound: the most accurate description of how bad it gets.

## 2. The simplification rules

**Drop constants.** O(2n), O(5n + 3) and O(n/2) are all **O(n)**. Constants depend on implementation details; growth doesn't.

**Drop lower-order terms.** O(n² + n) becomes **O(n²)**. For large n, the biggest term dominates: with n = 1,000,000, n² is a trillion and n is only a million.

**Sequential steps add, nested steps multiply.**
- A loop, then another loop: O(n) + O(n) = O(n)
- A loop inside a loop: O(n) × O(n) = O(n²)

**Different inputs get different variables.** If a function takes two arrays of sizes `a` and `b`, the cost is O(a + b) or O(a · b), never O(n). Calling both "n" is a classic interview mistake.

**The base of the logarithm doesn't matter.** log₂ n and log₁₀ n differ only by a constant factor, so we just write O(log n).

## 3. The common classes, from fastest to slowest

| Big-O | Name | Typical example | Operations for n = 1,000,000 |
|---|---|---|---|
| O(1) | Constant | Array access by index, dictionary lookup | 1 |
| O(log n) | Logarithmic | Binary search | ~20 |
| O(n) | Linear | One pass over an array | 1,000,000 |
| O(n log n) | Linearithmic | Good sorting (merge sort, `Array.Sort`) | ~20,000,000 |
| O(n²) | Quadratic | Comparing every pair | 1,000,000,000,000 |
| O(2ⁿ) | Exponential | All subsets of a set | impossible |
| O(n!) | Factorial | All permutations | impossible |

**Why log n is so small:** log n answers the question "how many times can I cut n in half before reaching 1?". A million halves down to 1 in about 20 steps; a billion in about 30.

**A practical trick for LeetCode:** the constraints at the bottom of each problem tell you which complexity is expected. As a rough rule, a computer does on the order of 10⁸ simple operations per second, so:

| Constraint | Complexity you can afford |
|---|---|
| n ≤ 20 | O(2ⁿ), O(n!) → backtracking |
| n ≤ 1,000 | O(n²) |
| n ≤ 100,000 | O(n log n) or O(n) |
| n ≤ 10⁹ | O(log n) or O(1) |

## 4. Reading complexity from code

**Single loop → O(n)**
```csharp
int sum = 0;
foreach (int x in nums)   // runs n times
    sum += x;             // O(1) each
```

**Nested loops → O(n²)**
```csharp
for (int i = 0; i < n; i++)
    for (int j = i + 1; j < n; j++)   // still O(n²)
        Compare(nums[i], nums[j]);
```
Even though the inner loop starts at `i + 1`, the total is n(n−1)/2 comparisons. Drop the constant ½ and the lower term: **O(n²)**.

**Halving loop → O(log n)**
```csharp
while (n > 1)
    n /= 2;
```

**Loop around a halving loop → O(n log n)**
```csharp
for (int i = 0; i < n; i++)        // n times
    for (int k = n; k > 1; k /= 2) // log n times
        DoWork();
```

**Two different inputs → O(a + b) or O(a · b)**
```csharp
foreach (var x in arrA) { }   // a
foreach (var y in arrB) { }   // b   → O(a + b)

foreach (var x in arrA)
    foreach (var y in arrB) { }      // → O(a · b)
```

### Hidden costs (where people lose points)

A single line of code is **not** automatically O(1). In C#:

- `list.Contains(x)` on a `List<T>` is **O(n)**: it scans the whole list. Inside a loop it turns your O(n) into O(n²). With a `HashSet<T>` it's O(1) on average.
- `s1 + s2` builds a **new string**. Concatenating in a loop is O(n²) overall; `StringBuilder` fixes it.
- `s.Substring(i, k)` copies k characters: **O(k)**.
- `list.Insert(0, x)` and `list.RemoveAt(0)` shift every element: **O(n)**.
- `.ToList()`, `.ToArray()`, `.OrderBy()`: the first two copy (O(n)), the third sorts (O(n log n)).

## 5. Best, average and worst case

The same algorithm can behave differently on different inputs:

- **Linear search:** best O(1) (first element), worst O(n) (not found).
- **Quicksort:** average O(n log n), worst O(n²) (bad pivots).
- **Hash table lookup:** average O(1), worst O(n) (every key collides into the same bucket).

The convention in interviews: give the **worst case**, except for hash structures, where everyone assumes the **average O(1)**. If you want to stand out, mention the worst case too.

## 6. Amortized complexity

`List<T>.Add` is backed by an array. When the array is full, .NET allocates a new one **twice as big** and copies everything: that single `Add` costs O(n).

But it happens rarely. Across n additions, the copies add up to 1 + 2 + 4 + … + n ≈ 2n, so the total is O(n), and the **average per operation is O(1)**. That's what "amortized O(1)" means: occasionally expensive, cheap on average across many operations. `Dictionary` and `HashSet` resize the same way.

## 7. Space complexity

It counts the **extra** memory, beyond the input itself:

- A few variables → **O(1)**
- A new array, dictionary or set proportional to the input → **O(n)**
- **The recursion call stack.** Each pending recursive call occupies a stack frame:

```csharp
int Sum(int[] a, int i)
{
    if (i == a.Length) return 0;
    return a[i] + Sum(a, i + 1);   // n frames on the stack → O(n) space
}
```
The iterative version with a loop uses O(1) space. Forgetting the stack is the most common space-complexity mistake.

Convention: the space for the **output** (the array you must return) usually isn't counted. It's worth saying which convention you're using.

## 8. Recursion, briefly

For recursive functions: **number of calls × work per call**. Naive Fibonacci calls itself twice per level, so it makes about 2ⁿ calls → **O(2ⁿ)**. With memoization each value is computed once → **O(n)**. More in the recursion lesson.

## 9. Costs of C# collections

| Operation | Cost |
|---|---|
| `array[i]`, `list[i]` | O(1) |
| `List.Add` | O(1) amortized |
| `List.Insert` / `RemoveAt` (not at the end) | O(n) |
| `List.Contains` / `IndexOf` | O(n) |
| `Dictionary` / `HashSet`: `Add`, `ContainsKey`, `Contains`, `Remove` | O(1) average |
| `Stack` / `Queue`: Push, Pop, Enqueue, Dequeue, Peek | O(1) |
| `PriorityQueue`: `Enqueue`, `Dequeue` | O(log n) |
| `SortedDictionary` / `SortedSet` | O(log n) |
| `Array.Sort` / `List.Sort` | O(n log n) |

## 10. How to talk about it in an interview

After every solution, without being asked:

> "This runs in O(n) time, where n is the length of the array, because we make a single pass. It uses O(n) extra space for the hash set. We could get O(1) space by sorting first, but that costs O(n log n) time."

Define n, give **time and space**, and when it makes sense name the **trade-off**. That last sentence is often what separates a junior who memorized solutions from one who understands them.

---

## Check questions — my answers and corrections

### Q1. Two nested loops: the outer over an array of size n, the inner over a *different* array of size m. Time complexity?

- **My answer:** O(N·M)
- **Verdict:** ✅ Correct. Different inputs get different variables.

### Q2. `while (n > 1) n /= 3;` Time complexity?

- **My answer:** "O(n3log)"
- **Verdict:** ⚠️ The idea is right, the notation isn't.
- **Correction:** Dividing by 3 each time gives log₃ n steps, written **O(log₃ n)**. Since the base of a logarithm only changes a constant factor, the standard answer is simply **O(log n)**. Dividing by 2, 3 or 10 is all O(log n).

### Q3. `foreach (var x in a) if (b.Contains(x)) count++;` — `a` has n elements, `b` is a `List<int>` with m elements. Complexity, and how to improve it?

- **My answer:** O(n·m), would improve with a HashSet
- **Verdict:** ✅ Correct, but finish the thought: state the new complexity.
- **Complete answer:**
  - Build a `HashSet<int>` from `b`: O(m) time, O(m) space
  - Then each `Contains` is O(1) on average, n times: O(n)
  - **Total: O(n + m) time, O(m) extra space**
- **Lesson:** in an interview, always state the new complexity *and* what it costs you (here, extra memory).

### Q4. Why is O(n² + 1000n) still O(n²), even though 1000 is a big constant?

- **My answer:** "Because n² is bigger"
- **Verdict:** ⚠️ Half right.
- **Correction:** n² isn't *always* bigger than 1000n: for n < 1000, 1000n wins. The real reason is that Big-O describes growth **as n becomes large**. Past n = 1000, n² grows faster and keeps pulling away (at n = 1,000,000 it's a trillion vs a billion), so the 1000n term becomes negligible. Constants and lower-order terms never change the growth rate, so we drop them.

### Q5. A recursive `f(n)` that calls `f(n − 1)` once and does O(1) work per call. Time and space?

- **My answer:** O(n) both
- **Verdict:** ✅ Correct: **O(n) time and O(n) space.**
- **Why:**
  - **Time:** f(n) → f(n−1) → … → f(0) is n + 1 calls, each doing O(1) work → O(n).
  - **Space:** none of those calls returns until the base case is reached, so at the deepest point **all n frames sit on the call stack at once** → O(n).
- That's the key difference from a loop: an iterative version does the same work in O(1) space. It's also why a very deep recursion in C# can crash with a `StackOverflowException`.

---

## Key takeaways

- Big-O = growth rate as n gets large; drop constants and lower-order terms.
- Sequential → add; nested → multiply; different inputs → different variables.
- Base of the log doesn't matter: dividing by any constant is O(log n).
- Watch hidden costs: `List.Contains`, string concatenation, `Substring`, `Insert(0, …)`.
- Always give **time and space**; recursion uses stack space.
- When you optimize, say the new complexity and the trade-off.
