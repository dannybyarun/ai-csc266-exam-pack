# 🎯 THE OTHER 2 TEN-MARKERS — Search Trace + ANN (all patterns, full marks)

*Pair with `the-10-marks.md` (resolution). These 3 patterns = every Section A since 2076. Master 2 of 3 → your pick of the easiest two → 20/20.*

---

## SECTION A PATTERN MAP (what the examiner can actually ask)

| Pattern | Seen in | Your choice? |
|---|---|---|
| **1. Resolution proof** | 2076, 2078, 2080, 2081, Model (+2082 variant) | ✅ always offered |
| **2. Search trace/explain** | 2076, 2078, 2079, 2080, 2081, Model (+2082 alpha-beta) | ✅ always offered |
| **3. ANN** | 2076, 2078, 2080, 2081, Model | ✅ almost always offered |
| Rare: Expert system stages | 2079 only | insurance ⬇ |
| Rare: CSP vs real-world | 2079 only | insurance ⬇ |
| Rare: RL + GA operators | 2082 only | insurance ⬇ |
| Rare: Semantic net + belief net | 2082 only | insurance ⬇ |

**Strategy:** the paper offers 3 long questions, you answer 2. Two of {1, 2, 3} ALWAYS appear. Pick those two. The rare ones are backup — 5-line skeletons at the bottom.

---

# PATTERN 2 — THE SEARCH 10-MARKER

### The 5 variants seen so far:
| Year | Variant |
|---|---|
| 2076, 2080, Model | Greedy + A* trace on a graph |
| 2081, 2079 | Hill climbing: explain + trace + show when it fails |
| 2078 | DLS + IDS trace |
| 2082 | Alpha-beta pruning trace on a game tree |
| 2076 | Prove Greedy incomplete but A* complete (mini-graph) |

### Universal skeleton (same 4 moves every time = 10/10):
```
MOVE 1 [2-3 m]  Definitions: informed vs uninformed, h(n), admissible
                "Informed search uses h(n)= estimated cost to goal; uninformed
                doesn't. Admissible h never overestimates → A* optimal."
MOVE 2 [1 m]    State the algorithm's RULE in one line before tracing:
                Greedy: expand lowest h · A*: lowest f=g+h · α-β: prune when α≥β
                · HC: move to best neighbor, stop when none better
MOVE 3 [4-5 m]  THE TRACE TABLE: Step | Expanded | Frontier(with values)
MOVE 4 [1 m]    Path + closing line:
                "Path S→…→G cost __. Greedy incomplete; A* complete/optimal
                since h admissible."
```

### The trace table (works for ALL graph variants):
| Step | Expanded | Frontier (values) |
|---|---|---|
| 1 | S | neighbors of S with h (greedy) or g+h (A*) |
| 2..n | lowest-value node | remove it, add its successors |
| last | G | — GOAL, path = the chain of expansions |

**Marks discipline:** write the value INSIDE the frontier at every step. Half the marks live in those numbers. Tie? Say "tie, choose left/first" — stating the assumption = safe.

### Variant switches (only MOVE 2-3 change):
- **Hill climbing:** no frontier! Table = | Move candidates | their h | best |. Score EVERY candidate move (that's where marks sit). Then limitations paragraph: local max/plateau/ridge + fixes (random restart, annealing e^(ΔE/T)).
- **DLS/IDS:** table = | Limit | Visits | Result |. IDS = DLS rerun with limit 0,1,2,… Closing: "combines DFS memory O(bd) with BFS completeness/optimality."
- **Alpha-beta:** tree with leaves given. Rules: MAX layers take max, MIN take min; α = MAX's best so far (−∞), β = MIN's best (+∞); **prune the moment α ≥ β**; mark pruned edges with ✂ and write (α,β) beside every node; closing: "same result as minimax, fewer nodes explored."
- **"Show Greedy fails, A* works":** tiny graph with a dead end that has tempting low h. Trace both. Closing: "Greedy chased the lowest h into a dead end — not complete. A* kept f=g+h honest and backtracked via the frontier — complete and optimal."

---

# PATTERN 3 — THE ANN 10-MARKER

### The 4 variants seen:
| Year | Variant |
|---|---|
| Model, 2081 | Math model + backpropagation (+ one worked iteration in 2081) |
| 2082 | Hebb net for OR |
| 2078 | Math model + "what is training" + perceptron algorithm |
| 2080, 2076 | Activation functions + perceptron / Hebbian learning |

### Universal skeleton:
```
MOVE 1 [2 m]  Bio mapping table: dendrite→inputs, synapse→weights,
              soma→summer+bias, axon→output
MOVE 2 [3 m]  Math model: y = f(Σwᵢxᵢ + b) + DIAGRAM (funnel: x's → Σ+b
              → f → y) + activation note: "sigmoid 1/(1+e⁻ˣ) squashes to
              (0,1), differentiable → enables gradient learning"
MOVE 3 [4 m]  THE ASKED RULE, with its worked table/numbers (below)
MOVE 4 [1 m]  Closing comparison: "Hebb = unsupervised, Perceptron =
              supervised single-layer (fails XOR), Backprop = supervised
              multi-layer gradient descent"
```

### MOVE 3 — the three rules (whichever they ask):

**(a) Hebb → show the OR table (asked verbatim 2082):**
Rule: **Δw = xᵢ·t**, start w₁=w₂=b=0, bipolar inputs:
| x₁ | x₂ | t | w₁ | w₂ | b |
|---|---|---|---|---|---|
| −1 | −1 | −1 | 1 | 1 | −1 |
| −1 | +1 | +1 | 0 | 2 | 0 |
| +1 | −1 | +1 | 1 | 1 | 1 |
| +1 | +1 | +1 | **2** | **2** | **2** |
Final: **w₁=2, w₂=2, b=2** + verify (−1,−1)→0 ✓ (1,1)→1 ✓.

**(b) Perceptron → the rule + algorithm:**
**w_new = w + η(t−y)x** — correct (t=y) → no change; wrong → nudge toward target. Steps: initialize → compute y → update all weights → repeat until zero error. Limitation: linearly separable only, fails XOR.

**(c) Backprop → the 5-step loop + one worked iteration:**
```
Forward y=f(Σwx+b) → Error E=½(t−o)² → Backward δₒ=(t−o)o(1−o),
δₕ=h(1−h)Σδₒw → Update Δw=η·δ·input → repeat
```
Worked iteration (memorize these numbers, they're 2081-style):
x₁=1, x₂=0, w₁₁=0.2, w₂₁=0.4, w_h=0.7, t=1, η=0.5:
h=σ(0.2)=0.55 → o=σ(0.385)=0.595 → δₒ=0.098 → w_h: 0.7→0.727, w₁₁: 0.2→0.208. Error fell. ∎

---

# INSURANCE — rare 10-markers (5-line skeletons)

**Expert system stages (2079):** define ES + MYCIN → 6 stages: Identify → Acquire (knowledge engineer interviews expert) → Represent → Implement → Test → Deploy → one-line each.

**CSP vs real-world (2079):** define problem criteria (initial/goal/actions/cost) → comparison table: well-defined variables vs dynamic uncertainty · Sudoku vs traffic · constraint satisfaction vs approximate good-enough decisions.

**RL + GA (2082):** model-free RL = learn from rewards without environment model (Q-learning); active vs passive (choose own actions vs judge fixed policy) → GA operators: selection (fitness-proportional), crossover (swap segments), mutation (bit flip), fitness function drives it.

**Semantic net + belief net numerical (2082):** draw the net (instance-of/is-a/property edges) → belief net: DAG + CPTs, **joint = Π P(node|parents)** → plug the given probabilities and multiply along one path; marginalize (sum) over unknowns if asked P(D|A).

---

### THE FINAL WORD
Section A = 3 questions offered, you answer 2, and {Resolution, Search, ANN} always supplies ≥2. skeletons above are complete scripts — practice each ONCE on paper tonight (30 min total) and the 20 marks are structural, not lucky. 💪
