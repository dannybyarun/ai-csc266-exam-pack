# 📝 MOCK EXAM 1 — Artificial Intelligence (CSC266)

**Full Marks: 60 · Time: 3 hrs · Attempt like the real thing: printed/blank paper, no notes, 3-hour timer (or compressed: 90 min).**

*TU format: Section A — attempt any TWO (2×10=20). Section B — attempt any EIGHT (8×5=40).*

---

## SECTION A — Attempt any TWO questions (2 × 10 = 20)

**1.** How is informed search different from uninformed search? Given the state space below, show how Greedy Best-First search and A* search find the goal state. State all assumptions. **[10]**

```
        S(h=8)
       /      \
    A(6)      B(4)
     |         |
    C(2)      D(3)
       \      /
        G(0)
```
Edge costs: S→A=3, S→B=2, A→C=2, B→D=4, C→G=5, D→G=3

**2.** Convert the following sentences into FOPL and use the resolution algorithm to prove that "Gita is studious": **[10]**
- All readers are studious.
- All students are readers.
- Sita is a student.
- Gita is a friend of Sita.
- All friends of students are students.

**3.** What is the mathematical model of an artificial neural network? Design a Hebb net to implement the logical OR function, showing all weight updates. Then explain in what situation a single-layer perceptron fails and why. **[10]**

---

## SECTION B — Attempt any EIGHT questions (8 × 5 = 40)

**4.** What is a rational agent? Can AI choose between right and wrong? Justify. **[5]**

**5.** Design a PEAS framework for (a) a Kathmandu traffic-monitoring drone, (b) an online fake-news detector. **[5]**

**6.** Apply hill climbing to: Initial `C, A, B` → Goal `A, B, C`, with h = +1 per correctly positioned block, −1 otherwise (list reads top→bottom; move = take one block, reinsert elsewhere). Show h for every candidate move. Does hill climbing get stuck here? **[5]**

**7.** Why do we need posterior probability? A disease affects 20% of a population. A test detects the disease in 90% of the sick people. Overall, 34% of the population test positive. Find the probability that a person who tests positive actually has the disease. **[5]**

**8.** Construct a semantic network for: Ram is a person. Persons are humans. All humans have a brain. Ram is intelligent. Sita is a person. Ram is taller than Sita. **[5]**

**9.** Define selection, crossover and mutation in genetic algorithms. Perform one-point crossover (after bit 5) on C1 = 10110011, C2 = 01001100. **[5]**

**10.** What are the phases of expert system development? Explain the role of the knowledge engineer. **[5]**

**11.** Why is pragmatic analysis necessary in NLP? Differentiate syntactic and semantic analysis with one example sentence each. **[5]**

**12.** How does iterative deepening search combine the strengths of DFS and BFS? Illustrate with a depth-3 example where the goal is at depth 2. **[5]**

**13.** Use minimax on this tree (root = MAX, children = MIN): MIN-node P has leaves {3, 5}, MIN-node Q has leaves {2, 9}. Which move does MAX choose, and what is the game value? Then state which leaf would be pruned under alpha-beta and why. **[5]**

**14.** What is model-free reinforcement learning? Differentiate supervised, unsupervised and reinforcement learning with one example each. **[5]**

**15.** Construct a fuzzy set "HIGH temperature" over X = {15, 20, 25, 30, 35, 40} with your own membership values, then compute the union and intersection with "COLD" = {15:1.0, 20:0.8, 25:0.4, 30:0.1, 35:0, 40:0}. **[5]**

---
---

# 📋 MARKING SCHEME + MODEL ANSWER POINTERS

*(Mark yourself strictly: half marks only where a real step is shown. 35+ = on track for an A.)*

**Q1 (10):** informed vs uninformed = uses h(n) vs blind [2]. **Greedy:** expand S → frontier {A(6), B(4)} → expand B(4) → D(3) joins {A(6), D(3)} → expand D(3) → G(0) → GOAL. Path S-B-D-G cost 9. [4: table 2, path 2] **A\*:** A: 3+6=9, B: 2+4=6 → expand B(6) → D: g=6, f=6+3=9; frontier {A(9), D(9)} → expand A(9) → C: g=5, f=5+2=7 → expand C(7) → G: g=10, f=10 → frontier {D(9), G(10)} → expand D(9) → G via D: g=6+3=9, f=9 → frontier {G(9)} → expand **G(9)** ✅ Path S-B-D-G cost 9. [4: f-values per node 2, correct order incl. the D-after-C backtrack 2 — note A* kept D alive instead of stopping at the pricier C-route: that's optimality in action]

**Q2 (10):** FOPL conversions [3]: ∀x(Reader(x)→Studious(x)) · ∀x(Student(x)→Reader(x)) · Student(Sita) · Friend(Gita,Sita) · ∀x∀y(Student(y)∧Friend(x,y)→Student(x)). CNF clauses [2]: ¬Reader(y)∨Studious(y); ¬Student(y)∨Reader(y); ¬Student(y2)∨¬Friend(x,y2)∨Student(x); Student(Sita); Friend(Gita,Sita); ¬Studious(Gita). Resolution [5]: Student(Sita)+clause2 {y/Sita} → Reader(Sita); +clause1 → Studious(Sita)... hmm — Gita path: Friend(Gita,Sita)+clause3 {x/Gita, y2/Sita} → Student(Gita); +clause2 → Reader(Gita); +clause1 → Studious(Gita); + ¬Studious(Gita) → **□ proved ∎** [3 for chain, 1 substitutions, 1 closing line]

**Q3 (10):** model y=f(Σwx+b) + diagram [3]; Hebb OR table → w₁=2, w₂=2, b=2 + verification [4]; perceptron fails XOR — not linearly separable, single line can't split [3]

**Q4 (5):** rational = max expected performance given percepts + knowledge [2]; rationality ≠ morality; AI chooses only within the utility function humans encode [2-3]

**Q5 (5):** any 2 correct PEAS rows per agent with all 4 letters

**Q6 (5):** h(C,A,B): C❌A❌B❌ = −3. Moves: C to end → A,B,C = **+3 GOAL** ✓ (also A to end → C,A,B = −3; B to end → C,A,B = −3). HC reaches goal in one move — no stuck. [table 3, verdict 2]

**Q7 (5):** posterior needed because decisions must update with evidence [1-2]. P(Disease|Positive) = P(Positive|Disease)·P(Disease)/P(Positive) = (0.90×0.20)/0.34 = **0.529** [3-4]

**Q8 (5):** nodes Ram, Sita, Person, Human, Brain + edges instance-of/is-a/has/property + taller-than between Ram-Sita. Any reasonable graph with correct edge labels = full

**Q9 (5):** definitions [3]; one-point after bit 5: C1 = 10110|011, C2 = 01001|100 → Child1 = 10110100, Child2 = 01001011 [2]

**Q10 (5):** identify → acquire → represent → implement → test → deploy [3]; knowledge engineer = extracts knowledge from human expert and encodes it [2]

**Q11 (5):** pragmatic = intent in real-world context [2]; syntactic = grammar/parse tree (rejects "girl the go school") [1.5]; semantic = literal meaning (rejects "colorless green ideas sleep furiously") [1.5]

**Q12 (5):** DLS with limit 0,1,2... [2]; example: tree A→B,C→D,E,F,G; goal E at depth 2: limits 0,1 fail, limit 2 finds A-B-E [3]

**Q13 (5):** P = min(3,5) = 3; Q = min(2,9) = 2; MAX picks P, value **3** [3]; alpha-beta: expanding Q after P=3, first leaf 2 ≤ 3 → prune the second leaf (9) — β-cutoff since MIN's β ≤ α [2]

**Q14 (5):** model-free = learns from rewards without learning environment transition model (Q-learning) [2]; supervised = labeled (spam filter), unsupervised = unlabeled clusters (segmentation), RL = reward signal (robot walk) [3]

**Q15 (5):** any valid HIGH with μ rising 0→1 [2]; union = max per element [1.5]; intersection = min per element [1.5]

---

## After the mock:
- **Score 35+?** You're exam-ready; just drill the cheat sheet + your traps.
- **25-35?** Re-read the session notes for whatever unit you dropped most marks in, re-attempt those questions tomorrow morning.
- **<25?** Don't panic — redo the answer bank with recall cycles for 2 hrs, then Mock 2 (make one by mixing unused past questions: 2080 Q1 puzzle state space, 2078 traffic proof, 2081 backprop, 2079 CSP comparison).
