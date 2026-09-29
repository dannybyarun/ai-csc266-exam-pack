# 🎴 ONE-PAGE CHEAT SHEET (print me — read morning-of, nothing else)

## SEARCH
```
FRONTIER = waiting list. Every search = frontier + picking rule.
ONE DIAL:  UCS = g only · Greedy = h only · A* = g + h
g = Gone (cost walked) · h = Hope (guess to goal)
A* optimal ⟺ h admissible (never overestimates)
HC = no frontier, best neighbor → local max/plateau/ridge
     fixes: 🚁 random restart · 🌡️ annealing P=e^(ΔE/T)
```
| Algo | Complete | Optimal | Picks by |
|---|---|---|---|
| BFS | ✅ | ✅ eq | queue |
| DFS | ❌ | ❌ | stack |
| DLS | ❌ l<d | ❌ | depth+limit |
| IDS | ✅ | ✅ eq | restart deeper |
| UCS | ✅ | ✅ | g |
| Greedy | ❌ | ❌ | h |
| A* | ✅ adm | ✅ adm | g+h |

**Trace format:** Step | Expanded | Frontier(values) — 4 rows + path + closing line.

## RESOLUTION (10-mark script)
```
All X are Y = ∀x(X→Y) · Some = ∃x(X∧Y) · No = ∀x(X→¬Y)
CNF = EMSSD: Eliminate→ · Move¬ · Standardize · Skolemize · Distribute
PROOF: negate goal → add clause → cancel A/¬A {y/Harry} → □ = proved ∎
Skolem: ∃ plain → constant; ∃ inside ∀ → function of that var
Unification = substitution making terms identical · Lifting = FOL resolution
Forward chain: facts→goal (data) · Backward: goal→facts (diagnosis)
```

## ANN / GA
```
Neuron: y = f(Σwx+b)  dendrite→in · synapse→w · soma→Σ · axon→out
Sigmoid σ(x)=1/(1+e⁻ˣ): squashes (0,1), differentiable → learning
Hebb: Δw = x·t          OR-net: w₁=2, w₂=2, b=2
Perceptron: w += η(t−y)x  — linearly separable only, FAILS XOR
Backprop: forward → E=½(t−o)² → δₒ=(t−o)o(1−o), δₕ=h(1−h)Σδw
          → Δw = η·δ·input → repeat
GA: select → crossover (swap segments) → mutate (bit flip) · fitness drives
```

## BAYES / UNCERTAINTY
```
Posterior = P(E|H)·P(H) / P(E)     [prior=before, posterior=after evidence]
2078: (0.07×0.15)/0.05 = 0.21     Full joint: matching ÷ evidence cells
Belief net: DAG + CPTs, joint = Π P(node|parents)
Fuzzy: μ∈[0,1] · union=max · intersection=min · complement=1−μ
```

## THEORY MNEMONICS
```
NLP steps:      L-S-S-P-D  "Lazy Students See Pragmatic Discourse"
                Lexical→Syntactic→Semantic→Pragmatic→Discourse
Agent types:    "Some Monkeys Grab Unripe Lemons"
                Simple reflex · Model · Goal · Utility · Learning
Expert system:  K-I-U-W-E = Knowledge base · Inference engine · User
                interface · Working memory · Explanation
ES phases:      Identify → Acquire → Represent → Implement → Test → Deploy
Turing test:    judge can't tell machine from human
                needs: NLP + KR + reasoning + learning
Searches:       "Big Dogs Don't Ignore Ugly Bones" BFS DFS DLS IDS UCS Bi
Env pairs:      static/dynamic · deterministic/stochastic ·
                full/partial observable · discrete/continuous ·
                single/multi-agent
PEAS:           Performance · Environment · Actuators · Sensors
```

## EXAM MECHANICS
```
5-marker skeleton: Definition → DIAGRAM → 4-5 bullets → Example
Section A FIRST (10-markers, need traces)
Hall: dump mnemonics + Bayes + f=g+h on rough page BEFORE solving
Never blank: definition + diagram = partial marks
Diagrams to draw blind: neuron · KIUWE · NLP pipeline · minimax tree
                        · agent loop · semantic net · belief net
```
