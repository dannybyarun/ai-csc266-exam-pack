# Unit 3 — Problem Solving by Searching ⭐ (appeared in 7/7 papers)

## Core vocabulary (use these words, they carry marks)

- **State space representation:** a problem described as a graph of states. 4 components: **(1) initial state, (2) actions/successor function, (3) goal test, (4) path cost**. (2079 Q2: "criteria for defining problem")
- **State space example — Water Jug (2079 Q6):** state = (x, y) = water in 4-gal, 3-gal jug. Start (0,0), goal (2, n). Rules: fill x, fill y, empty x, empty y, pour x→y, pour y→x. Path: (0,0)→(4,0)→(1,3)→(1,0)→(0,1)→(4,1)→(2,3) ✓ goal.
- **Search strategy evaluation (COTS):** **C**ompleteness (finds solution if exists?), **O**ptimality (finds best?), **T**ime complexity, **S**pace complexity. Notation: b = branching factor, d = depth of shallowest goal, m = max depth, l = limit.

## Master comparison table (MEMORIZE — asked directly in 2079/2081/2082)

| Algorithm | Complete? | Optimal? | Time | Space |
|---|---|---|---|---|
| BFS | ✅ (b finite) | ✅ (equal step costs) | O(b^d) | O(b^d) ❌ |
| DFS | ❌ (infinite paths) | ❌ | O(b^m) | O(bm) ✅ |
| DLS | ❌ (if l < d) | ❌ | O(b^l) | O(bl) |
| IDS | ✅ | ✅ (equal costs) | O(b^d) | O(bd) ✅ |
| UCS | ✅ (costs > 0) | ✅ | O(b^(1+⌊C*/ε⌋)) | same |
| Bidirectional | ✅ | ✅ (equal costs) | O(b^(d/2)) | O(b^(d/2)) |
| Greedy BFGS | ❌ (loops) | ❌ | O(b^m) worst | O(b^m) |
| A* | ✅ (admissible h) | ✅ (admissible h) | exponential | exponential ❌ |

**IDS = "BFS in DFS clothing"** — repeats upper levels but re-expansion cost is small; preferred when depth unknown.

---

## Q: Informed vs uninformed search (2078 Q1, 2081 Q3, 2079 implicitly)

| | Uninformed (blind) | Informed (heuristic) |
|---|---|---|
| Knowledge of goal direction | none — only branching | uses **heuristic h(n)** = estimated cost to goal |
| Examples | BFS, DFS, DLS, IDS, UCS, Bidirectional | Greedy, A*, Hill Climbing, Best-first |
| Efficiency | explores blindly, often more nodes | guided, usually fewer nodes |
| Guaranteed optimal? | only BFS/IDS/UCS | A* (if h admissible) |

**Heuristic function** h(n) = estimated cost from n to goal. **Admissible** = never overestimates the true cost: `h(n) ≤ h*(n)`. Example: straight-line distance in route finding. Admissibility ⇒ A* optimality.

---

## Q: Greedy Best-First & A* trace (Model Q1, 2080 Q1, 2076 Q1)

- **Greedy:** expand node with smallest **h(n)** only. Fast, not complete, not optimal.
- **A\*:** expand node with smallest **f(n) = g(n) + h(n)** (g = cost so far, h = estimate remaining). "g = Gone, h = Hope."

**Model Q1 h-values:** h(S)=12, h(A)=8, h(D)=9, h(B)=7, h(E)=4, h(C)=5, h(F)=2, h(G)=0.

*(The paper's figure wasn't extractable — the table format below is what earns the marks; redo it with the actual edges on your paper. Worked example with assumed edges S→A(4), S→D(2), S→B(4), D→C(3), B→E(2), A→E(4), C→G(4), E→G(5):)*

**Greedy trace:**
| Step | Expanded | Frontier (by h) |
|---|---|---|
| 1 | S | A(8), D(9), B(7) |
| 2 | B(h=7 lowest) | A(8), D(9), E(4), C(5) |
| 3 | E(h=4) | A(8), D(9), C(5), G(0) |
| 4 | G → **GOAL**. Path S-B-E-G | |

**A\* trace (f = g + h):**
| Step | Expanded | Frontier (by f) |
|---|---|---|
| 1 | S (f=12) | A(4+8=12), D(2+9=11), B(4+7=11) |
| 2 | D (f=11) | A(12), B(11), C(5+5=10) |
| 3 | C (f=10) | A(12), B(11), G(9+0=9) |
| 4 | G (f=9) → **GOAL**. Path S-D-C-G, cost 9 |

**2076 Q1 — show Greedy NOT complete, A* complete (construct your own space):**
States: S(h=3), A(h=1, **dead end**), B(h=2), G(h=0). Edges: S→A(1), S→B(1), B→G(1).
- Greedy: expand S → picks A (h=1 < h=2) → A has **no successors → dead end** → must backtrack; naive greedy loops/fails ⇒ **not complete**.
- A*: expand S → A(f=1+1=2), B(f=1+2=3) → expand A (no children) → expand B → G(f=2) → goal. Found S-B-G cost 2, optimal ⇒ **complete & optimal** (h admissible).

---

## Q: Hill Climbing — mechanism, limitations, blocks trace (2079 Q1, 2081 Q3, 2082 Q6)

**Idea:** like climbing in fog — repeatedly move to the best neighbor if it improves h; stop when no neighbor is better. = local greedy search, keeps **no frontier**.

**Limitations (draw the 4 pictures!):**
1. **Local maximum** — a peak lower than the global peak; stuck
2. **Plateau** — flat area; no direction looks better
3. **Ridge** — diagonal peak; single moves all look worse
4. (Fixes: random-restart, simulated annealing)

**2082 Q6 blocks trace** (Initial: A,D,C,B → Goal: D,C,B,A; h = +1 per correctly-positioned block, −1 otherwise; sequence = top→bottom):
- h(initial): A,D,C,B — every block in wrong slot ⇒ **h = −4**
- Possible moves (move top block to bottom of stack):
  - Move A: D,C,B,A → all 4 correct ⇒ **h = +4** ✅ improvement!
  - Move D: A,C,B,D → h = −4
  - Move C: A,D,B,C → h = −4
- Greedy choice: **move A to bottom** → state D,C,B,A = **GOAL reached**, h = +4. One step. ✅

**2081 Q3 — modify heuristics to break hill climbing:** make the goal path pass "downhill": S→A(h=6), A→B(h=8, local max), B→C(h=4), C→G(h=0). Hill climbing from S: S→A→B, at B all neighbors (C, h=4) look worse ⇒ **stuck at local max B**, never reaches G. ⇒ incomplete.

---

## Q: Simulated Annealing (in syllabus, ask-able)

Hill climbing + randomness: sometimes accept a **worse** move with probability `P = e^(ΔE/T)` where T = temperature (starts high, cools down). High T ⇒ explores wildly; T→0 ⇒ becomes plain hill climbing. Escapes local maxima early; freezes into good solution. Analogy: cooling molten metal.

---

## Q: Depth Limited Search & Iterative Deepening (2079 Q9, 2078 Q1, 2080 Q12)

**DLS:** DFS with a depth cutoff l. Treats nodes at depth l as if they have no successors.
- **Benefits:** avoids DFS's infinite descent; bounded memory O(bl); good when you know roughly where the goal is
- **Limitations:** **incomplete if l < d** (goal deeper than limit — may never find it); not optimal; choosing l is guesswork

**IDS trace (2078 Q1)** — assume tree: A→B,C; B→D,E; C→F,G; E→J,K (K = goal, depth 3):
| Limit | Order of visits | Result |
|---|---|---|
| l=0 | A | not found |
| l=1 | A, B, C | not found |
| l=2 | A, B, D, E, C, F, G | not found (K at depth 3) |
| l=3 | A, B, D, H, I, E, **J, K** ✅ | path A-B-E-K |

Re-expansion happens but overhead is small (upper levels are tiny) — that's why IDS is the **best general uninformed strategy**.

---

## Q: Uniform Cost Search (2076 Q6, 2081 Q6)

BFS ordered by **path cost g(n)** instead of depth (priority queue). Optimal for any non-negative costs.

**Trace example:** S→A(1), S→B(4), A→B(2), A→G(12), B→C(2), C→G(3).
| Step | Expanded | Frontier (by g) |
|---|---|---|
| 1 | S(0) | A(1), B(4) |
| 2 | A(1) | B(3 via A), G(13), |
| 3 | B(3) | C(5), G(13) |
| 4 | C(5) | G(8 via C) |
| 5 | G(8) → GOAL: S-A-B-C-G, cost 8 ✅ (beats direct S-A-G = 13) |

---

## Q: Game playing — Minimax (2081 Q11, Model Q11)

Two players: **MAX** maximizes utility, **MIN** minimizes. Recursively evaluate tree bottom-up: leaves get utility values; MIN layers take minimum of children; MAX layers take maximum. Choose move at root with best value.

**2081 Q11 worked (utilities H=1, I=3, J=2, K=6, L=3, M=4, N=1):**
Tree from the pairs: A→B,C; B→D; D→E,H,I; E→J; C→F,G; F→K,L; G→M,N.
Assume A = MAX (root), depth-1 (B,C) = MIN, depth-2 (D,E,F,G) = MAX, leaves = values.

| Node | Calculation | Value |
|---|---|---|
| E (MAX) | max(J=2) | 2 |
| D (MAX) | max(H=1, I=3, E=2) | 3 |
| F (MAX) | max(K=6, L=3) | 6 |
| G (MAX) | max(M=4, N=1) | 4 |
| B (MIN) | min(D=3) | 3 |
| C (MIN) | min(F=6, G=4) | 4 |
| **A (MAX)** | **max(3, 4)** | **4** |

**Answer: A plays to C; optimal path A→C→G→M.**

*(Model Q11: same procedure — label root MAX, alternate layers, back up values, state the chosen path.)*

---

## Q: Alpha-Beta Pruning (2082 Q1, 2080 Q6, 2078 Q11)

**Why:** minimax explores the whole tree — wasteful. Alpha-beta prunes branches that **cannot change the root decision**, giving the SAME answer, faster (with good ordering, explores ~O(b^(d/2)) — doubles searchable depth).
- **α** = best value MAX has guaranteed so far (starts −∞)
- **β** = best value MIN has guaranteed so far (starts +∞)
- **Prune when α ≥ β** ("alpha cutoff" at MIN node whose value ≤ α; "beta cutoff" at MAX node whose value ≥ β)

**Worked example (children left→right; leaves under MIN nodes B, C, D):** B: 3,5,6 · C: 9,1,2 · D: 0,−1,4
1. B (MIN): min(3,5,6) = **3**. Root: α = 3.
2. C (MIN): after 9 → β=9; after 1 → β=1; after 2 → C = **2**. Root: α = max(3,2) = 3.
3. D (MIN): first leaf 0 → D's β = 0 ≤ α(3) ⇒ **PRUNE remaining leaves of D** (β-cutoff) — they can't raise D above 0, and root already has 3.
4. Root = **3**, best move = B. ✅

For 2082 Q1's actual tree: visit children left→right, keep updating (α, β) at every node, write them beside each node, mark pruned branches with a slash, and report final α, β at the root.

---

## Q: Constraint Satisfaction Problems (2079 Q2, syllabus)

**CSP:** problem where states = assignments of values to **variables**; goal = assignment satisfying all **constraints**.
- Components: **variables X, domains D (possible values), constraints C**
- Examples: map coloring (no adjacent same color), 8-queens (no two queens attack), Sudoku, cryptarithmetic (SEND+MORE=MONEY)
- Solving: **backtracking search** — assign one variable at a time, backtrack when a constraint is violated; improve with forward checking / MRV heuristic.

**CSP vs Real-world problem (2079 Q2):**

| | CSP | Real-world (e.g., taxi driving) |
|---|---|---|
| State | assignment of values to variables | continuous, dynamic situations |
| Environment | static, fully observable, discrete | dynamic, partially observable |
| Goal test | all constraints satisfied | complex, changing |
| Solution | any valid assignment | a good course of action over time |
| Example | Sudoku, map coloring | driving, medical diagnosis |

---

### ⚡ 30-second recall
> Uninformed = blind (BFS DFS DLS IDS UCS Bi). Informed = h(n). Greedy = h only (incomplete). A* = g+h (optimal if h admissible). Hill climbing = greedy neighbor, stuck at local max/plateau/ridge. Minimax: MAX/MIN alternate. Alpha-beta: prune when α ≥ β. CSP = variables + domains + constraints.
