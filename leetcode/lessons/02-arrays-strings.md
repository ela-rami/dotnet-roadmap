# Lesson 2 — Arrays and strings

*Phase 0 · Started: 12 October 2026 · Status: in progress (steps 1–6 of 8 done)*

← [Lesson 1 — Big-O](01-big-o.md) · [Back to index](../README.md)

Remaining: Step 7 (the concatenation trap and `StringBuilder`), Step 8 (in-place array techniques), check questions.

---

## Step 1 — What an array is in memory

An array is a **single block of memory**, with all its elements placed **one right after another**, with no gaps.

```csharp
int[] nums = { 10, 20, 30, 40 };
```

In memory it looks like this (an `int` takes 4 bytes):

```
address:  1000   1004   1008   1012
value:    [10]   [20]   [30]   [40]
index:     0      1      2      3
```

Three properties follow from this layout:

1. **Fixed size.** The block is reserved when the array is created. `new int[4]` stays size 4 forever; it can't grow.
2. **Same type.** All elements have the same size, so they line up perfectly.
3. **Contiguous.** No gaps between elements.

These three properties are what make it possible to get any element instantly (Step 2).

---

## Step 2 — Why index access is O(1)

Since every element has the same size and they sit next to each other, the computer doesn't need to *search* for an element. It **calculates** where the element is:

```
address of nums[i] = start address + i × element size
```

With the array from Step 1 (start = 1000, `int` = 4 bytes):

```
nums[2] → 1000 + 2 × 4 = 1008 → value 30
nums[3] → 1000 + 3 × 4 = 1012 → value 40
```

It's **one multiplication and one addition**, whether the array has 4 elements or 4 million. That's why `nums[i]` is **O(1)**.

It also explains why indexes start at **0**: the index is the *offset* from the start. The first element is 0 steps away from the beginning.

---

## Step 3 — Why inserting in the middle is O(n)

Because the elements must stay **contiguous**, you can't just "squeeze" a new value in between two others. Everything after that position has to **shift one place to the right** to make room.

Insert `15` at index 1:

```
before:   [10] [20] [30] [40] [  ]
                ↓    ↓    ↓
shift:    [10] [  ] [20] [30] [40]
insert:   [10] [15] [20] [30] [40]
```

To insert at index 1 we moved 3 elements. In the worst case (inserting at index 0) we move **all n elements**, so it's **O(n)**.

**Deleting** works the same way in reverse: everything after the removed element shifts **one place to the left** to close the gap, so it's also O(n).

The only cheap position is the **end**: adding or removing the last element moves nothing, so it's O(1).

---

## Step 4 — Dynamic arrays (`List<T>` in C#)

A plain array has a fixed size. But in practice we often don't know in advance how many elements we'll have. That's what a **dynamic array** solves: in C# it's `List<T>`.

Inside, a `List<T>` is just a normal array that's **bigger than needed**. It tracks two numbers:

- **Count:** how many elements you actually stored
- **Capacity:** how many slots the internal array has

```
list.Add(10); list.Add(20); list.Add(30);

internal array:  [10] [20] [30] [  ]
Count = 3, Capacity = 4
```

When you `Add` and there's a free slot, the value goes at the end: **O(1)**.

When the array is **full**, `List<T>` does three things:

1. creates a **new array twice as big**
2. **copies** all the elements into it, which costs O(n)
3. adds the new element

```
full:     [10] [20] [30] [40]                       Capacity 4
Add(50) → [10] [20] [30] [40] [50] [ ] [ ] [ ]      Capacity 8
```

Because the size doubles, these expensive copies get **rarer and rarer**, so on average `Add` is **O(1) amortized** (see Lesson 1, section 6).

Insertions and deletions in the middle are still O(n), exactly like in Step 3: it's still an array underneath.

---

## Step 5 — Strings are arrays of characters

A `string` in C# is, underneath, a **sequence of `char` stored contiguously**, just like an array. So everything from Steps 1–2 applies:

```csharp
string s = "hello";

// index:   0    1    2    3    4
// chars:  'h'  'e'  'l'  'l'  'o'

char c = s[1];      // 'e' → O(1), same address calculation
int len = s.Length; // 5   → O(1), the length is stored, not counted
```

Three details worth knowing:

- **`char` vs `string`.** `'h'` (single quotes) is one `char`; `"h"` (double quotes) is a `string` containing one character. They're different types.
- **A `char` is a number underneath.** Each character has a numeric code: `'a'` is 97, `'b'` is 98, and so on. This lets you do arithmetic like `'c' - 'a' = 2`, which comes up a lot (e.g. counting letters with an `int[26]`).
- **`Length`, not `Count`.** Strings and arrays use `.Length`; `List<T>` uses `.Count`. Easy to mix up without autocomplete.

There's one big difference from an array, though: **you can't change a character in place** (Step 6).

---

## Step 6 — Strings are immutable

**Immutable** means that once a string is created, **it can never be changed**.

```csharp
string s = "hello";
s[0] = 'H';   // ❌ compile error: the indexer is read-only
```

Every operation that seems to "modify" a string actually **creates a new one** and leaves the original untouched:

```csharp
string s = "hello";
string t = s.ToUpper();   // t = "HELLO", a brand-new string
                          // s is still "hello"

s = s + "!";              // builds a NEW string "hello!"
                          // and points s at it; the old "hello" is discarded
```

So `s = s + "!"` looks like a small change, but under the hood it **copies every character** into a new string: that's **O(n)**, not O(1).

If you need to change characters by index, the usual trick is to work on a `char[]` and turn it back into a string at the end:

```csharp
char[] chars = s.ToCharArray();   // O(n) copy, but now mutable
chars[0] = 'H';                   // ✅ allowed
string result = new string(chars);
```

This matters because it creates a **trap in loops** — that's Step 7.

---

## Step 7 — *(next)* The concatenation trap and `StringBuilder`

## Step 8 — *(to do)* In-place array techniques

## Check questions — *(to do)*
