# ⚡ The Answer Bank — Learn the ANSWER, not the topic

**The trick:** TU repeats ~80% of its paper from a pool of ~20 questions. You don't need to "understand AI" — you need to be able to *reproduce* 20 pre-built answers. This file IS those answers, written the way you'd write them in the exam.

**How to use (2–3 hrs):**
1. Read one answer → close the file → rewrite it from memory → check. (That's it. No topic digging.)
2. One revision pass = ~15 min per unit of this file.
3. In the exam, find the matching question → dump the memorized answer → add one example if you remember more.

**Universal 5-mark skeleton** (if you blank out, ANY question survives with this):
`Definition (1-2 lines) → Diagram (always draw one) → 4-5 bullets → 1 example`

---

# SECTION A FRAMES (the two 10-markers)

## 🔵 FRAME 1: Search trace question (A*, Greedy, Hill Climbing, Minimax, Alpha-Beta)

**Opening lines (write these ALWAYS, 2 marks free):**
> "Search strategies are evaluated on 4 parameters: Completeness (guarantees a solution if one exists), Optimality (guarantees the best solution), Time complexity and Space complexity. Informed search uses a heuristic h(n) = estimated cost from node n to goal, while uninformed search uses no such knowledge."

**Then the trace — one table per algorithm, this exact format:**
| Step | Node Expanded | Frontier (with f/g/h values) |
|---|---|---|
| 1 | S | A, B, C... |
| 2 | ... | ... |

**Closing line:** "Hence the path found is S→...→G with total cost __, which is (optimal / not optimal)."

- **Greedy:** order frontier by **h(n)** only → fast, not complete, not optimal
- **A\*:** order frontier by **f(n) = g(n) + h(n)** (g = cost so far, h = estimate left) → optimal if h is **admissible** (never overestimates)
- **Hill Climbing:** expand ONLY the best neighbor; stop when no neighbor improves h; problems: local maximum, plateau, ridge → fixes: random-restart, simulated annealing
- **Minimax:** alternate MAX/MIN layers, back values up from leaves, MAX takes max, MIN takes min, root chooses best child
- **Alpha-Beta:** minimax + pruning; α = best for MAX so far (−∞ start), β = best for MIN so far (+∞ start); **stop expanding a node when α ≥ β**; same answer as minimax, faster
- **UCS:** order frontier by g(n) → optimal with any non-negative costs
- **IDS:** run DLS with limit 0, 1, 2... → complete + optimal (equal costs) + memory O(bd) = "BFS in DFS clothing"

## 🔵 FRAME 2: FOPL + Resolution proof (10 marks, appears EVERY year)

**Step 1 — Convert each English sentence (use the pattern table):**
| English | FOPL |
|---|---|
| All X are Y | ∀x (X(x) → Y(x)) |
| No X are Y | ∀x (X(x) → ¬Y(x)) |
| Some X are Y | ∃x (X(x) ∧ Y(x)) |
| Names (Laxmi, Harry) | constants: laxmi, harry |

**Step 2 — Write the 5 CNF steps by name (examiner gives marks for naming them):**
> 1. Eliminate → and ↔  2. Move ¬ inward (De Morgan, quantifier negation)  3. Standardize variables  4. Skolemize (remove ∃ by inventing constants/functions)  5. Drop ∀ and distribute → clauses

**Step 3 — Resolution by refutation (always this script):**
> "To prove the goal by resolution, we negate the goal: ¬Goal. Now resolve clauses pairwise, each time removing a complementary pair:"
> - Clause 1 + Clause 2 with substitution {x/…} → new clause
> - ... → ... → empty clause □
>
> "Since we derived a contradiction (empty clause), the negated goal is false, hence **the goal is proved.** ∎"

**Worked template (Model Q2 — reuse the shape for any names):**
Facts: over-smart→stupid; stupid person's children→naughty; Roney child of Harry; Harry over-smart. Prove Naughty(Roney).
```
C1: ¬OverSmart(y) ∨ Stupid(y)
C2: ¬Stupid(y) ∨ ¬Child(x,y) ∨ Naughty(x)
C3: Child(Roney, Harry)      C4: OverSmart(Harry)
C5: ¬Naughty(Roney)          (negated goal)
C4 + C1 {y/Harry} → Stupid(Harry)          [C6]
C6 + C2 {y/Harry, x/Roney} → Naughty(Roney) [C7]
C7 + C5 → □  ⇒ proved ∎
```

## 🔵 FRAME 3: ANN question (backprop / Hebb / perceptron — 10 marks)

**Opening (always):**
> "An ANN is a computing system inspired by biological neurons. Mathematical model: y = f(Σ wᵢxᵢ + b) — inputs x are multiplied by weights w, summed with bias b, passed through activation function f. Biological mapping: dendrite→inputs, synapse→weights, soma→summer, axon→output."

**If Hebb net (e.g., OR gate) asked — write this:**
> "Hebb rule: Δw = xᵢ·t (neurons that fire together wire together). Start w₁=w₂=b=0, bipolar inputs:"
> Table: (−1,−1)→t=−1: w₁=1,w₂=1,b=−1 · (−1,1)→t=1: w₁=0,w₂=2,b=0 · (1,−1)→t=1: w₁=1,w₂=1,b=1 · (1,1)→t=1: w₁=2,w₂=2,b=2
> **Final: w₁=2, w₂=2, b=2.** Test: y=sign(2x₁+2x₂+2) gives 0,1,1,1 = OR ✓. Draw: 2 inputs → weights 2,2 → bias 2 → step function → output.

**If backprop asked:**
> "Backprop = gradient descent on error. Passes: (1) Forward: compute outputs y=f(Σwx+b) layer by layer. (2) Error: E = ½(t−o)². (3) Backward: output delta δₒ=(t−o)·o(1−o); hidden delta δₕ = h(1−h)·Σδₒw. (4) Update: Δw = η·δ·input. (5) Repeat until error small."
> Then draw: input layer → hidden layer → output layer with arrows, label one worked iteration like: net_h=0.2, h=0.55, o=0.595, δₒ=0.098, w_h: 0.7→0.727.

**If perceptron asked:**
> "w_new = w_old + η(t−y)x; b_new = b + η(t−y). If correct (t=y) no change; else weights shift toward target. Repeat until zero error. Limitation: only linearly separable problems (fails XOR)."

---

# SECTION B BANK (the 5-markers — memorize these verbatim-ish)

## 1. Turing Test ⭐ (4/7 papers)
> "The Turing Test (Alan Turing, 1950) tests machine intelligence: a human interrogator chats by text with a hidden human and a hidden machine; if the interrogator cannot reliably identify the machine, the machine is intelligent. Properties needed to pass: (1) Natural Language Processing, (2) Knowledge Representation, (3) Automated Reasoning, (4) Machine Learning — plus Computer Vision and Robotics for the Total Turing Test. It measures intelligence through observable behavior rather than internal mechanisms." + [DRAW: interrogator box → arrows → human box & computer box]

## 2. PEAS + example ⭐
> "PEAS = Performance measure, Environment, Actuators, Sensors — the framework for specifying an agent's task environment. Example — self-driving taxi: P: safe, fast, legal, comfortable, profit; E: roads, traffic, pedestrians, weather; A: steering, accelerator, brake, horn, display; S: cameras, LiDAR, GPS, speedometer." (For COVID predictor / shopping assistant / tutor — swap in the rows from solutions/unit-1-2.)

## 3. Agent types ⭐
> "An agent perceives via sensors and acts via actuators. Five types: (1) **Simple reflex** — acts on current percept only via condition-action rules (vacuum cleaner). (2) **Model-based** — keeps internal state to handle partial observability. (3) **Goal-based** — chooses actions that reach a goal state. (4) **Utility-based** — chooses the action maximizing a utility function; handles trade-offs (fast vs safe). (5) **Learning agent** — improves with experience." + [DRAW: 4-box chain Sensors→(What the world is like now)→What it will be like→(Condition-Action/Utility)→Actuators]

## 4. Environment types ⭐
> "Task environments are classified in pairs: Fully vs Partially observable (chess vs taxi); Deterministic vs Stochastic (chess vs traffic); Static vs Dynamic (crossword vs driving — environment changes while agent thinks); Discrete vs Continuous (chess moves vs robot arm angles); Single vs Multi-agent (crossword vs football robots). A taxi agent is: partially observable, stochastic, dynamic, continuous, multi-agent."

## 5. Hill Climbing ⭐
> "Hill climbing is a local search that keeps moving to the neighbor with the best heuristic value and stops when no neighbor improves it — like climbing in fog. Limitations: (1) Local maximum — stuck on a small peak, (2) Plateau — flat region gives no direction, (3) Ridge — diagonal slope defeats single moves. Remedies: backtracking, random restarts, simulated annealing (accept worse moves with probability e^(ΔE/T) while temperature T cools). No frontier is kept — memory O(1), but incomplete and not optimal."

## 6. Frames / Semantic nets / Scripts (one answer covers 3 questions)
> **Frames:** "A frame is a data structure with slots (attributes) and fillers (values), organized in inheritance hierarchies. E.g. EMPLOYEE: name Ram, age 27, dept HR-DEPT; HR-DEPT (is-a DEPARTMENT): 110 employees, salary 45000; DEPARTMENT (is-a TU); TU: type Educational." + [DRAW: nested boxes]
> **Semantic net:** "A graph where nodes = concepts, labeled edges = relations (is-a, instance-of, has). E.g. Puppy→instance-of→Dogs→hate→Cats; Tom→instance-of→Cats; Cats→chase→Rats. Inference = follow edges / inherit properties from classes." + [DRAW bubbles]
> **Scripts:** "A script is a frame-like structure for stereotyped event sequences: entry conditions, props, roles, scenes. E.g. RESTAURANT: enter→order→eat→pay→exit. It lets the system predict unstated events."

## 7. Bayes rule numerical ⭐ (same pattern every year)
> "Prior probability P(H) is the initial belief before evidence; posterior P(H|E) is the updated belief after evidence — needed because rational decisions must incorporate new information. Bayes' rule: P(H|E) = P(E|H)·P(H)/P(E)."
> Then plug in the paper's numbers exactly like: "P(Disease|Alcoholic) = (0.07×0.15)/0.05 = 0.21."
> **Rule for the exam:** whatever two conditional probabilities are given, multiply them for the numerator; the denominator is the given marginal. (If full-joint table given: P(Q|E) = sum of matching cells ÷ sum of evidence cells.)

## 8. Bayesian network ⭐
> "A Bayesian (belief) network is a DAG where nodes are random variables, edges are causal influences, and each node stores a CPT P(X|Parents). The joint distribution factorizes: P(X₁…Xₙ) = Π P(Xᵢ|Parents(Xᵢ)). Reasoning types: causal (top-down), diagnostic (bottom-up), intercausal (explaining away)." + [DRAW: Cloudy(0.5), Winter(0.5) → Rain(CPT 0.3) → Sunny(0.7)]

## 9. GA operators ⭐
> "Genetic algorithms evolve a population of chromosomes toward better solutions. Operators: (1) **Selection** — fitter chromosomes are chosen as parents (roulette wheel: probability ∝ fitness). (2) **Crossover** — two parents swap gene segments at crossover point(s): one-point 0110|0010 + 1010|1100 → 01101100, 10100010; two-point swaps the middle segment. (3) **Mutation** — random bit flip with small probability, maintains diversity, escapes local optima. Fitness function scores each chromosome. Steps: initialize population → evaluate fitness → select → crossover → mutate → repeat." + [DRAW: two bars swapping a chunk, one bit flipping]

## 10. NLP steps ⭐
> "NLP enables machines to understand (NLU) and generate (NLG) human language. Steps: (1) **Lexical** — tokenize text, morphological analysis (running → run+ing). (2) **Syntactic** — parse grammar, build parse tree, reject ill-formed sentences. (3) **Semantic** — extract literal meaning, reject grammatical-but-meaningless sentences. (4) **Discourse** — resolve references across sentences (he = Ram). (5) **Pragmatic** — interpret intended meaning using real-world context: 'Can you pass the salt?' is a request, not an ability question. Challenges: lexical/syntactic/semantic ambiguity, idioms, context."

## 11. Expert systems ⭐
> "An expert system emulates a human expert's decision-making in a narrow domain (MYCIN — medical diagnosis). Components: (1) **Knowledge Base** — facts + IF-THEN rules from the expert; (2) **Inference Engine** — the brain: matches facts against rules, fires rules via forward (data-driven) or backward (goal-driven) chaining; (3) **Working Memory** — holds current case facts; (4) **User Interface** — dialog with user; (5) **Explanation Module** — justifies 'why/how' to build trust. Development phases: problem identification → knowledge acquisition → representation/design → implementation → testing → deployment & maintenance." + [DRAW the KIUWE boxes]

## 12. Reinforcement learning
> "In RL an agent learns by acting in an environment and receiving rewards/penalties, maximizing cumulative reward — e.g. a robot learning to walk. Supervised learning uses labeled data; unsupervised finds structure in unlabeled data (clustering). **Passive RL** evaluates a fixed given policy; **active RL** chooses its own actions and explores to find the optimal policy. **Model-free** RL learns directly from experience without learning environment transition probabilities (e.g. Q-learning)."

## 13. Naive Bayes
> "Naive Bayes is a statistical supervised classifier using Bayes' theorem with the 'naive' assumption that features are independent given the class: P(C|X) ∝ P(C)·ΠP(xᵢ|C). Training counts frequencies to estimate P(C) and P(xᵢ|C); classification computes this product per class and picks the maximum — e.g. spam filtering with word frequencies."

## 14. Fuzzy logic
> "Fuzzy logic handles degrees of truth: unlike crisp sets (membership 0 or 1), fuzzy sets allow membership μ(x) ∈ [0,1] — e.g. 'TALL' with μ(170cm)=0.4. Operators: union = max, intersection = min, complement = 1−μ. A fuzzy rulebase system: fuzzify crisp inputs → evaluate IF-THEN rules (IF temp HIGH THEN fan FAST) → aggregate → defuzzify (centroid) to crisp output. Used in washing machines, ACs, brake control."

## 15. Rationality + can AI choose right/wrong
> "A rational agent, for each possible percept sequence, selects the action that maximizes its expected performance measure, given the evidence from its percepts and its built-in knowledge. Rationality ≠ morality: AI maximizes the utility function humans give it. It can distinguish right from wrong only to the extent its designers encoded ethics into that utility function — it has no consciousness or intention of its own."

## 16. UCS / IDS (if the trace question is these instead)
> **UCS:** "expands the node with lowest path cost g(n) using a priority queue; optimal for non-negative costs." → trace table.
> **IDS:** "runs depth-limited search with limits 0,1,2,… combining DFS memory O(bd) with BFS completeness/optimality; upper levels are re-expanded but overhead is small." → trace table + "benefits of DLS: bounded memory, avoids infinite paths; limitation: incomplete if limit < goal depth."

## 17. Machine vision & robotics
> "Machine vision lets a computer extract understanding from images. Components: lighting → camera/sensor → frame grabber/processor (filtering, edge detection) → feature extraction → decision unit. Applications: defect inspection, face recognition, OCR, medical imaging, self-driving. In robotics, vision is the main exteroceptive sense: it supplies obstacle positions and object locations used for navigation and grasping. Robot hardware: **proprioceptive** sensors (encoders, gyro) sense its own state; **exteroceptive** (camera, LiDAR, sonar, touch) sense the world; **effectors**: motors, grippers, wheels."

---

# 🎴 THE FINAL CHEAT CARD (read this in the morning, nothing else)

1. **Search:** compare by COTS. Greedy=h only, incomplete. A*=g+h, optimal if admissible. Alpha-beta: prune when α≥β. Hill climbing: local max/plateau/ridge.
2. **Resolution:** negate goal → CNF (EMSSD) → resolve complementary pairs → □ = proved.
3. **FOPL:** All X are Y = ∀x(X→Y) · Some = ∃x(X∧Y) · No = ∀x(X→¬Y)
4. **ANN:** y=f(Σwx+b). Hebb Δw=x·t. Perceptron w+=η(t−y)x. Backprop: forward→error→δ back→Δw=η·δ·input.
5. **Bayes:** posterior = P(E|H)·P(H)/P(E).
6. **GA:** select → crossover → mutate.
7. **NLP:** Lexical→Syntactic→Semantic→Discourse→Pragmatic.
8. **ES:** KIUWE; build: Identify→Acquire→Represent→Implement→Test→Deploy.
9. **Agents:** Some Monkeys Grab Unripe Lemons; env pairs: observable/deterministic/static/discrete/single-multi.
10. **Every 5-marker:** definition → diagram → 4-5 bullets → example. **Never leave a question blank.**

---

*Exam-day flow: Section A first (both are Frame 1/2/3 questions) → then Section B from this bank → end with short notes you half-remember (write the definition + 3 bullets minimum).*
