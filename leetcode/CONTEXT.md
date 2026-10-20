# Context — read this first

This file is for anyone (a person or an AI) who picks up guiding my learning. It says who I am, what I'm aiming for, how I want to be taught, and where I am now.

## Who I am and the goal

- Junior software developer (C#/.NET), Bachelor's in IoT, Big Data and Machine Learning (UNIUD).
- I already studied algorithms and data structures at university: this is a **review**, not learning from scratch. But nothing should be skipped, so I don't lose pieces.
- Goal: pass technical interviews for **junior .NET/C# roles**, international market (English-speaking), remote or in Austria.
- I solve problems in **C#**.
- Weekly time is variable; this runs alongside my .NET study project (SideQuest), which has priority in busy weeks.

## How I want lessons taught

1. **In English.**
2. **One small concept per message.** A short explanation, a tiny example if useful, then stop. I reply "next" to continue or ask a question about that step. No long walls of text.
3. **Check questions at the end of each lesson**, then correct my answers (explain what was right, what was half right, and why).
4. **Complete notes in this repo**, one file per lesson in `lessons/`: everything that was explained, not a summary — including my questions, my answers to the checks and the corrections. I must be able to reread them months later and understand everything without the chat.

## Rules for problems

- **The AI does not write my solutions.** It can give a hint in words, explain a concept, or review code I wrote.
- Timebox: Easy 20 min, Medium 35 min without help; then one hint; then read the solution, close it, rewrite from scratch.
- Explain my reasoning out loud in English, as in a real interview.
- Full method in [roadmap.md](roadmap.md#metodo).

## Current status

*Last updated: 20 October 2026*

- **Phase:** 0 (Foundations)
- **Lesson 1 — Big-O:** done, check questions answered and corrected. See [lessons/01-big-o.md](lessons/01-big-o.md).
- **Lesson 2 — Arrays and strings:** in progress. Steps 1–6 done (memory layout, O(1) index access, O(n) insert/delete, `List<T>`, strings as char arrays, immutability). **Next: Step 7 — the concatenation trap in loops and `StringBuilder`**, then Step 8 (in-place array techniques), then the check questions.
- **Then:** Lesson 3 (recursion), then the 9 Phase 0 problems.
- **Problems solved:** none yet.

## Weak spots noticed so far

- Notation: wrote "O(n3log)" instead of O(log n) — the idea of halving/dividing was right, the notation wasn't. Remember: the base of the log doesn't matter.
- When improving a solution, state the **new complexity and its cost** (e.g. "O(n + m) time, O(m) extra space"), not just the idea.
- "Why drop lower-order terms": the reason is growth for large n, not that one term is "bigger" (it isn't for small n).
