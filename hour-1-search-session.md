# 🎓 Hour 1 Live Session Notes — SEARCH (your personal version)

*This is the record of our live tutoring session. Re-read this instead of the generic files — it has YOUR analogies and YOUR specific mistakes marked. Personal traps are the most valuable study notes you own.*

**Progress log:**
```
✅ Hill climbing (trace + why useful + both fixes)
✅ Greedy best-first (trace + rule)
✅ A* (trace + rule)
✅ Comparison table
```

---

## 1. HILL CLIMBING — learned via YOUR analogy

### 🧠 YOUR analogy (memorize THIS, not the textbook):
> *"Suppose I am at a random landlocked place. I look at all sides where another top is, and I move to that place. After reaching that top I again look for another. If I don't find another top — THAT is the top of the hill I climbed."*

That was already ~90% correct! The official mapping:

| Your words | Exam term |
|---|---|
| "random landlocked place" | random initial state |
| "look all sides" | evaluate all neighbors |
| "move to that place" | step to the best neighbor |
| "again look for another" | repeat |
| "no better top → that's my top" | stop when no neighbor improves h |

### Two upgrades that make it exam-perfect:
1. **"Look all sides" = one STEP only** — you're in FOG 🌫️. You can't see the next mountain; you only feel the ground around your feet (neighbors = one move away).
2. **"The top of MY hill" ≠ the tallest mountain** → **local maximum**. The exam sentence: *"Hill climbing terminates at a local maximum, which may not be the global maximum — hence it is incomplete."*

### The landscape picture:
```
                         🏔️ global max (real goal)
                        /\
            ⛰️ local   /  \
            max   ⭕ /    \      ← you stop here thinking you won
               /\  /
              /  \___plateau___   ← flat: no direction better
   ──────────────────────────────
        (ridge = diagonal slope, single steps all worse)
```

### Why HC is still USED (the "why necessary" answer):
1. **Memory O(1)** — keeps no frontier. A*/BFS die of memory explosion on huge problems; HC doesn't care.
2. **"Good enough, fast"** beats "best, slow" for timetables, router placement, game AI under a clock.
3. **Friendly landscapes** (one peak only) → HC = optimal there.
4. It's the **base algorithm** that its own fixes upgrade.

### The fixes (🚁 or 🌡️ — NOT another search algorithm!):
- **Random-restart HC** = helicopter drop on a random new spot, climb again → eventually guaranteed to find global max slope
- **Simulated annealing** = take a downhill step ON PURPOSE occasionally → cross the valley → climb bigger mountain. Early = hot 🔥 (downhill allowed freely), late = cold ❄️ (pure HC). Formula: `P = e^(ΔE/T)`

### ✅ Solved trace (the actual 2082 Q6):
Initial `A,D,C,B` → Goal `D,C,B,A`, h = +1 per correct block, −1 wrong (list reads top→bottom).
- h(initial) = −4 (all wrong)
- Moves: **A to end → D,C,B,A = +4 ✅** · D to end → −4 · C to end → −2
- HC picks "A to end" → GOAL in one step.

| Step | Current state | h | Best move | New h |
|---|---|---|---|---|
| 0 | A, D, C, B | −4 | Move A to end | +4 = GOAL ✓ |

---

## 2. THE FRONTIER — the concept everything else hangs on

> **Frontier = the waiting list of discovered-but-not-yet-expanded nodes.**
> Every search algorithm = **a frontier + a rule for picking from it.**

```
        S(h=12)                          h-values: S=12, A=8, D=9,
      /    |    \                                  B=7, E=4, C=5, G=0
   A(8)  D(9)  B(7)                    edge costs: S→A=4, S→D=2, S→B=4,
    |     |     |                                 A→E=4, D→C=3, B→E=2,
   E(4) C(5)  E(4)                                C→G=4, E→G=5
    |     |     |
     \    |    /
        G(h=0)
```

---

## 3. GREEDY BEST-FIRST — rule: expand LOWEST h

| Step | Expanded | Why | Frontier after |
|---|---|---|---|
| 1 | S(12) | start | {A(8), D(9), B(7)} |
| 2 | B(7) | lowest h | {A(8), D(9), E(4)} |
| 3 | E(4) | lowest h | {A(8), D(9), G(0)} |
| 4 | G(0) ✅ | lowest h → GOAL | — |

**Path: S → B → E → G.** Greedy never touched A or D — fast but reckless.
**Closing line:** *"Greedy is fast but not complete and not optimal, because it ignores path cost g(n)."*

### ⚠️ YOUR PERSONAL TRAPS (you did these live — watch for them in the exam):
- **Trap 1:** You once picked **D(9)** — the HIGHEST h — instead of lowest. Rule re-check: greedy = LOWEST h wins.
- **Trap 2:** You answered "g+h" for greedy's rule once. No — **greedy = h ONLY**. The g+h thing is A*.

---

## 4. A* — rule: expand LOWEST f = g + h

> **g = Gone** (real cost walked from S) · **h = Hope** (guess to G)

| Step | Expanded | Frontier (f = g+h) |
|---|---|---|
| 1 | S | A(4+8=12), D(2+9=11), B(4+7=11) |
| 2 | D(11) | A(12), B(11), C(5+5=10) |
| 3 | C(10) | A(12), B(11), G(9+0=9) |
| 4 | G(9) ✅ | — |

**Path: S → D → C → G, cost 9.** (Notice: A* kept A and D honestly in the frontier — that's why it's optimal while greedy isn't.)
**Closing line:** *"A* is complete and optimal provided h is admissible (never overestimates), because f = g+h always selects the node on the cheapest promising path."*

---

## 5. THE MASTER TABLE (memorize with the "one dial" trick)

> **Three algorithms, one dial:  UCS = g only · Greedy = h only · A* = g + h**

| Algorithm | Complete? | Optimal? | Picks by |
|---|---|---|---|
| BFS | ✅ | ✅ equal costs | depth (queue) |
| DFS | ❌ | ❌ | depth (stack) |
| DLS | ❌ if l < d | ❌ | depth + limit |
| IDS | ✅ | ✅ equal costs | depth, restarting |
| UCS | ✅ | ✅ | **g(n)** |
| **Greedy** | ❌ | ❌ | **h(n)** |
| **A*** | ✅ adm. h | ✅ adm. h | **g + h** |
| Hill climb | ❌ | ❌ | best neighbor |

---

## 6. POCKET RECAP (the whole hour in 5 lines)

```
FRONTIER = waiting list. Every search = frontier + picking rule.
UCS=g · Greedy=h · A*=g+h.   g=Gone, h=Hope.
Greedy: fast/reckless → incomplete, not optimal.
A*: optimal IFF h admissible (never overestimates).
HC: no frontier, best neighbor only → stuck at local max
    → fixes: 🚁 random restart or 🌡️ simulated annealing e^(ΔE/T).
```

---

## 7. Your self-test record (from the live session)

| Question | You said | Verdict |
|---|---|---|
| h(D,C,B,A) vs goal | +4 | ✅ |
| HC's move from −4 state | Move A to end | ✅ |
| Greedy expands lowest h? | B(7) from {A8,D9,B7} | ✅ |
| Greedy next from {A8,D9,E4} | D (9) | ❌ → it's E(4), LOWEST h |
| Greedy picks by? | g+h | ❌ → h(n) only |
| A* final expand {A12,B11,G9} | G(9) | ✅ |
| A* optimal condition | if h admissible | ✅ |
| Stuck on bump fixes | random restart / annealing | ✅✅ |

**Pattern:** you're strong on HC and A*; your wobble is greedy's "h only" rule. Re-read section 3 once more tonight. 🎯
