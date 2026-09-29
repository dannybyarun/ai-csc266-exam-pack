# 🎯 AI (CSC266) — 5-Hour Exam War Pack
*BSc CSIT 4th Sem · Tribhuvan University · Compiled from HamroCSIT question banks*

---

## 📋 Exam Format (60 marks theory)
- **Section A:** Answer 2 of 3 LONG questions (10 marks each) → 20
- **Section B:** Answer 8 of ~9-10 SHORT questions (5 marks each) → 40
- 3 hours. Section A = your search/logic/ANN questions. Section B = theory blitz.

---

## 🔥 TOPIC FREQUENCY (out of 7 papers: 2076, 2078, 2079, 2080, 2081, 2082, Model)

| Topic | Freq | Where it appeared |
|---|---|---|
| **Search algorithms (trace practice)** | 7/7 ⭐ | Every Section A. Hill climbing, Greedy, A*, DLS/IDS, UCS, Minimax, Alpha-beta |
| **FOPL conversion + CNF + Resolution proof** | 7/7 ⭐ | Every paper. Full 10-mark proof questions |
| **ANN (math model, Hebb, Perceptron, Backprop)** | 6/7 | 2076Q3, 2078Q3, 2080Q3, 2081Q1, Model Q3, 2082Q8 |
| **Bayes: prior/posterior, Bayes rule numerical, belief nets** | 5/7 | 2076Q10, 2078Q12, Model Q7, 2082Q2, 2082Q7 |
| **NLP 5 steps (lexical→syntactic→semantic→pragmatic)** | 5/7 | 2076Q12, 2078Q9, 2079Q4, 2080Q11, Model Q6 |
| **GA operators (selection/crossover/mutation)** | 5/7 | 2076Q9, 2078Q7, 2079Q10, 2080Q8, 2082Q3 |
| **Agents: PEAS, rationality, types, environments** | 5/7 | Short questions in nearly every paper |
| **Semantic nets / frames / scripts** | 5/7 | 2076Q7, 2078Q6, Model Q10, 2081Q7, 2082Q7 |
| **Expert systems (components + development phases)** | 4/7 | 2078Q8, 2079Q3, 2080Q10, 2082Q10 |
| **Minimax / Alpha-beta (draw tree)** | 4/7 | 2078Q11, 2080Q6, 2081Q11, 2082Q1 |
| **Supervised/Unsupervised/RL + Naive Bayes** | 4/7 | Model Q9, 2079Q11, 2081Q5, 2082Q3 |
| **Fuzzy sets & rulebase** | 3/7 | 2076Q8, 2079Q10, 2081Q10 |
| **UCS trace** | 2/7 | 2076Q6, 2081Q6 |
| **Machine vision & robotics** | 2/7 | 2076Q11, 2081Q9 |
| **Turing test** | 4/7 | 2078Q4, 2079Q12c, 2080Q4, Model Q4 |
| **Full joint distribution inference** | 2/7 | 2076Q10, 2082Q2 |

**⭐ = If you master only 3 things: (1) search traces, (2) FOPL→resolution, (3) ANN. That's both Section A slots secured.**

---

## 📜 ALL PAST QUESTIONS (grouped by year)

### 2082 (latest)
**Section A:**
1. Problems of depth limited search. Use Alpha-Beta pruning on given game tree (left→right). Show final α, β at root, each internal node, and top of pruned branches.
2. How to infer knowledge from a semantic net? Given Bayesian network with A, B, C, D — if A is true, find P(D).
3. Model-free reinforcement learning? Active vs passive RL. GA operators.

**Section B:**
4. Define rational. Can AI choose right vs wrong?
5. PEAS description + example
6. Hill climbing: blocks A,D,C,B → D,C,B,A with h(n)=+1 correct, −1 wrong
7. Why posterior probability? Semantic net: Dogs hate cats. Tom is a cat. Puppy is a dog. Cats chase rats. Rats are clever.
8. Design Hebb net for logical OR
9. Premises: living things are animal or plant; plants need sunlight; mustard is living, not animal → does mustard need sunlight? (resolution)
10. Phases of expert system development
11. Why machines need NLP? Challenges?
12. Static vs dynamic environment example. When prefer rule-based systems?

### 2081
**Section A:**
1. Relate synapse/dendrite/axon to ANN. Multi-layer ANN + one iteration of backpropagation.
2. Skolem constant? Skolemization in resolution. FOPL: movies/hit/Sarangi statements.
3. Informed vs uninformed. Hill climbing trace + modify heuristics to show incompleteness.

**Section B:**
4. Intelligence? Foundations of AI
5. RL? Configure ANN neuron for OR gate
6. UCS with example
7. Scripts + create a knowledge base using script
8. (repeat of 5)
9. Robotics? Machine vision in robotics?
10. Fuzzy logic + fuzzy rulebase expert system
11. Minimax on given tree (H..N utilities: 1,3,2,6,3,4,1)
12. Environment types for: fixed-6-state 2-player game / Tesla on changing roads / prediction independent of past

### 2080
**Section A:**
1. State space graph for puzzle, label states, greedy best-first with misplaced-cells heuristic
2. CNF conversion rules. FOPL: BSc CSIT students/Rojina/Laxmi. Resolution → "Laxmi is smart"
3. Activation function role. Sigmoid. Perceptron learning

**Section B:**
4. Turing Test + properties to pass it
5. Intelligent agent properties. Simple reflex agents + example
6. Why alpha-beta pruning? Illustrate
7. Frames: Ram/HR department/TU knowledge
8. Selection, crossover, mutation in GA
9. PEAS: (a) Covid-19 prediction (b) Vaccine recommender
10. Expert system components
11. Why pragmatic analysis in NLP? How done?
12. IDS with example

### 2079
**Section A:**
1. Admissible heuristic + example. Hill climbing: mechanism + limitations
2. Problem definition criteria. CSP vs Real-world problem comparison
3. Expert system definition + development stages

**Section B:**
4. Syntactic & semantic analysis in NLP
5. Rational agent. Utility-based vs model-based
6. State space representation + example
7. Forward chaining + example
8. FOPL: (a) all barking animals are dogs (b) someone firing a gun (c) all tigers are not fierce
9. Game. Benefits/limitations of depth limited search
10. Fuzzy logic. GA operators
11. RL example. Types of ANN
12. Short notes (any 2): Pragmatic analysis / Unification & lifting / Turing test

### 2078
**Section A:**
1. Informed vs uninformed. DLS + IDS trace (A→K)
2. Traffic/driver facts → FOPL → resolution: "if all drivers horn, all traffics are frustrated"
3. Math model of NN. Training meaning. Perceptron learning algorithm

**Section B:**
4. Turing test to measure machine intelligence
5. PEAS configuration + example
6. Semantic net: Ram/person/human/nose/mammal/60kg/Sita
7. Crossover: one-point & two-point on C1=01100010, C2=10101100
8. Expert system + inference engine role
9. Semantic & pragmatic analysis
10. Philosophy, sociology, economics influence on AI
11. Alpha-beta cutoffs on given search space
12. Posterior probability: P(liver disease)=15%, P(alcoholic)=5%, P(alcoholic|disease)=7% → P(disease|alcoholic)?

### 2076
**Section A:**
1. State space + heuristics: show Greedy is not complete, A* is complete & optimal
2. FOPL: Pugu/hero/Anmol/rehearse → resolution: "If Anmol doesn't work, Pugu doesn't love Anmol"
3. Math model of ANN. Hebbian learning + example

**Section B:**
4. AI from thought-process perspective
5. Environment types for agents
6. UCS example
7. Frames + knowledge encoding example
8. Fuzzy membership. X={10..70} construct fuzzy set
9. Genetic algorithm learning algorithm
10. Full joint distribution: P(length=130 | width=15)
11. Machine vision in robot sensors
12. Syntactic & semantic analysis with example

### MODEL QUESTION
**Section A:**
1. Heuristic search. Greedy + A* trace (h: S=12, A=8, D=9, B=7, E=4, C=5, F=2, G=0)
2. Resolution in predicate logic. FOPL: over-smart/stupid/naughty/Roney/Harry → prove "Roney is naughty"
3. ANN math model + backpropagation training

**Section B:**
4. Turing test (acting humanly)
5. Model-based vs simple reflex agent
6. NLP steps
7. Belief network: P(cloudy)=0.5, P(rain|cloudy,winter)=0.3, P(winter)=0.5, P(sunny)=0.7
8. Expert system components
9. Supervised learning + Naive Bayes
10. Semantic net: Ram/person/nose/mammal/weight facts
11. Minimax path for two players
12. PEAS: (a) Internet shopping assistant (b) English language tutor

---

## ⏱️ THE 5-HOUR BATTLE PLAN

### 🕐 Hour 1 (H+0 → H+1): SEARCH — the guaranteed 10-marker
**Goal:** Be able to TRACE any search algorithm by hand.
- Learn the trace pattern for: BFS, DFS, **DLS, IDS, UCS, Greedy, A\***, Hill Climbing, Simulated Annealing (concept), Minimax, Alpha-Beta.
- **Memorize the comparison table** (Completeness / Optimality / Time / Space):

  | Algorithm | Complete? | Optimal? | Space |
  |---|---|---|---|
  | BFS | ✅ (b finite) | ✅ (equal costs) | O(b^d) ❌ big |
  | DFS | ❌ (infinite) | ❌ | O(bm) ✅ small |
  | DLS | ❌ (if l<d) | ❌ | O(bl) |
  | IDS | ✅ | ✅ (equal costs) | O(bd) ✅ — *best of both* |
  | UCS | ✅ (cost≥0) | ✅ | O(b^(1+⌊C*/ε⌋)) |
  | Greedy | ❌ (loops) | ❌ | O(b^m) |
  | A* | ✅ (admissible h) | ✅ (admissible) | exponential ❌ |

- **Practice these 3 traces on paper** (they repeat almost verbatim):
  1. Hill climbing on blocks A,D,C,B→D,C,B,A (2082 Q6)
  2. Greedy + A* on Model Q1 state space
  3. Alpha-beta on a 4-level tree, left to right (2082 Q1, 2081 Q11)
- Memory hook: **"IDS = BFS in DFS clothing"** — re-expands but cheap memory.
- A* f(n) = g(n) + h(n): "**g = Gone (past), h = Hope (future)**". Admissible = h never overestimates → optimality.

### 🕑 Hour 2 (H+1 → H+2): FOPL + RESOLUTION — the other guaranteed 10-marker
**The 5-step CNF recipe (memorize cold):**
1. Eliminate ↔ and → (A→B becomes ¬A∨B)
2. Move ¬ inward (De Morgan, ¬∀x = ∃x¬, ¬∃x = ∀x¬)
3. Standardize variables apart (rename so each quantifier unique)
4. Skolemize (drop ∃: no preceding ∀ → Skolem constant; inside ∀ → Skolem function)
5. Drop ∀, distribute ∨ over ∧ → set of clauses

**Conversion patterns (memorize!):**
- "All X are Y" → ∀x (X(x) → Y(x))
- "No X are Y" → ∀x (X(x) → ¬Y(x))
- "Some X are Y" → ∃x (X(x) ∧ Y(x))
- "All X are not Y" (ambiguous, usually ∀x X(x) → ¬Y(x))

**Practice 3 full proofs on paper:** Model Q2 (Roney naughty), 2080 Q2 (Laxmi smart), 2078 Q2 (traffic/driver).
**Then 15 min:** Forward vs backward chaining (data-driven vs goal-driven + one example), unification & lifting (short note).

### 🕒 Hour 3 (H+2 → H+3): ANN + ML + GA
- **Math model of neuron** (draw it!): y = f(Σ wᵢxᵢ + b). Inputs→weights→summer→activation.
- **Hebb net for OR** (asked 2082!): memorize rule Δw = xᵢ·t. Table: (0,0)→0, (0,1)→1, (1,0)→1, (1,1)→1.
- **Perceptron learning:** w_new = w_old + η(t−y)x, repeat until no error.
- **Backprop:** forward pass → compute error at output → backpropagate error (gradient descent) → update weights → repeat. One labeled diagram.
- **GA operators:** Selection (fitness-based survival), Crossover (swap parents' genes — one-point & two-point), Mutation (random bit flip). Practice 2078 Q7 crossover on 01100010/10101100.
- **ML trio:** Supervised (labeled), Unsupervised (unlabeled clustering), Reinforcement (reward/penalty, active vs passive, model-free).
- **Naive Bayes:** P(C|X) ∝ P(C)·ΠP(xᵢ|C) — "naive = assumes feature independence".

### 🕓 Hour 4 (H+3 → H+4): KR light + Bayes + Fuzzy + Semantic nets
- **Semantic nets:** nodes + labeled edges (is-a, instance-of, has). Practice 2 diagrams: Ram/human (Model Q10) + animals (2082 Q7).
- **Frames:** slot-filler structure; practice 2080 Q7 (Ram employee frame).
- **Scripts:** restaurant-style slot sequence (props, roles, scenes) — 2081 Q7.
- **Bayes rule numerical (memorize the pattern):** P(D|A) = P(A|D)·P(D) / P(A).
  2078 answer: P(disease|alcoholic) = (0.07×0.15)/(0.05) = 0.21 → 21%.
- **Belief/Bayesian network:** DAG + CPTs; practice Model Q7 (cloudy→rain, winter).
- **Full joint:** P(query | evidence) = sum matching cells / sum evidence cells (2076 Q10).
- **Fuzzy:** membership μ∈[0,1], operators (min/max/complement), construct fuzzy set like "TALL" over X.

### 🕔 Hour 5 (H+4 → H+5): THEORY BLITZ + BLURT
**First 30 min — rapid-fire theory (mnemonics below):**
- Expert system components: **K.I.U.W.E** — **K**nowledge base, **I**nference engine, **U**ser interface, **W**orking memory, **E**xplanation module. Development phases: **P**roblem **A**cquisition → **K**nowledge **E**licitation → **D**esign → **I**mplementation → **T**esting → **D**eployment (A-KED-IT-D).
- NLP 5 steps: **"Lazy Students See Pragmatic Discourse"** — **L**exical → **S**yntactic → **S**emantic → **P**ragmatic → **D**iscourse.
- Agent types: **"Some Monkeys Goal Utility Learn"** — Simple reflex, Model-based, Goal-based, Utility-based, Learning.
- Environment types: **D**eterministic/**S**tochastic, **S**tatic/**D**ynamic, **O**bservable/**S**emi, **S**ingle/**M**ulti-agent.
- Rationality = doing the right thing given percept sequence + built-in knowledge. AI morality (2082 Q4): rational ≠ moral; AI optimizes given utility function.
- Machine vision components: lighting, camera/sensor, processor, decision output. Robotics: sensors (proprioceptive/exteroceptive) + effectors.
- Turing test: interrogator can't distinguish machine from human → needs NLP, knowledge repr., reasoning, learning.

**Last 30 min — BLURT DRILL (the memory sealer):**
- Take a BLANK sheet. Per chapter, write everything you remember (algorithms names, formulas, diagrams from memory).
- Compare with this pack. Whatever you missed → that's your 10-min final revision before entering the hall.

---

## 🧠 MEMORY SYSTEM (how to actually retain this in 5 hrs)

1. **One diagram per topic rule** — for every 5-marker, you get marks for: definition → diagram → steps → example. Even if you forget text, redraw the diagram from muscle memory. You'll draw search trees, neuron model, expert system boxes, semantic nets ~10 times today.
2. **Trace, don't read.** For every algorithm, your hand must have drawn it once today. Motor memory survives panic better than reading memory.
3. **Answer skeleton for every 5-marker (memorize this ONE template):**
   `Definition (1 line) → Diagram → 4-5 bullet steps/points → 1 example → 1 line of applications/limitations`
4. **Chunk the syllabus into 3 buckets** so it feels small:
   - 🧭 **Search** (ch 2-3): agents + all algorithms
   - 🧮 **Logic & Uncertainty** (ch 4): FOPL, resolution, Bayes, fuzzy, semantic nets
   - 🤖 **Learning & Apps** (ch 5-6): ANN, GA, ML, expert systems, NLP, robotics
5. **2-minute spaced recall:** after each hour, close everything and say the 3 key items of that hour out loud. Forgetting curve reset in 2 minutes.
6. **Section A strategy in the exam:** pick Search + (Resolution OR ANN) — they're the most predictable. Write the algorithm in numbered steps, then trace.
7. **Sleep ≥5.5 hrs.** A tired brain loses recall of exactly the things you crammed. If you must cut study, cut Hour 4, never the sleep.

## 🎲 Predicted high-probability questions for your exam (based on repetition)
1. A* / Greedy trace or Hill climbing with heuristics (Section A) — appeared 7/7
2. FOPL conversion + resolution proof (Section A) — 7/7
3. ANN math model / backprop / Hebb net OR (Section A or B) — 6/7
4. Alpha-beta or minimax tree trace — 4/7
5. Bayes rule numerical — 5/7
6. GA operators + crossover example — 5/7
7. NLP steps / pragmatic analysis — 5/7
8. PEAS design (COVID predictor, shopping assistant style) — 4/7
9. Expert system components/phases — 4/7
10. Semantic net construction — 5/7

---
*Sources: hamrocsit.com question banks (2076–2082 + model), easycsit.com syllabus (CSC266).*
