# 🖼️ The Diagram Bank — Every Figure You Must Draw in the Exam

*GitHub renders the Mermaid diagrams below live. Practice rule: redraw each diagram 2× on paper from memory during Hour 5. Diagrams = easy marks even when text escapes you.*

---

## UNIT 2 — AGENTS

### 1. Agent structure (draw for ANY "what is an agent" question)
```mermaid
flowchart LR
    E["Environment"] -->|"percepts"| S["Sensors"]
    S --> P["Agent Program<br/>(the brain)"]
    P --> A["Actuators"]
    A -->|"actions"| E
```
> Exam label: `agent = architecture + program`

### 2. Simple reflex agent
```mermaid
flowchart LR
    S["Current percept"] --> R{"Condition-Action<br/>Rules<br/>(if dirty → suck)"}
    R --> A["Action to Actuators"]
```

### 3. Model-based agent (has MEMORY)
```mermaid
flowchart LR
    S["Percept"] --> M["State<br/>(how world evolves)"]
    M --> W["What the world is<br/>like now"]
    W --> R["Condition-Action Rules"]
    R --> A["Action"]
```

### 4. Goal-based agent (adds GOAL box)
```mermaid
flowchart LR
    S["Percept"] --> M["State"] --> W["World model now"]
    W --> G["GOAL?<br/>what it will be like"]
    G --> R["Choose action that<br/>reaches goal"]
    R --> A["Action"]
```

### 5. Utility-based agent (replaces GOAL with UTILITY)
```mermaid
flowchart LR
    S["Percept"] --> M["State"] --> W["World now"]
    W --> U["UTILITY<br/>(how good is each outcome?)"]
    U --> R["Pick action with<br/>max expected utility"]
    R --> A["Action"]
```

---

## UNIT 3 — SEARCH

### 6. The state-space graph (label every trace question like this)
```mermaid
flowchart TD
    S(("S")) --> A(("A"))
    S --> B(("B"))
    A --> D(("D"))
    A --> E(("E"))
    B --> E
    B --> F(("F"))
    E --> G(("GOAL"))
    F --> G
```
> In the exam: write g, h, f values BESIDE each node as you expand.

### 7. A* formula box (write this at the top of every A* answer)
```
┌─────────────────────────────────────┐
│  f(n) = g(n) + h(n)                 │
│  g = Gone  (real cost from START)   │
│  h = Hope  (estimated cost to GOAL) │
│  Admissible: h(n) ≤ true cost       │
│  → A* optimal if h is admissible    │
└─────────────────────────────────────┘
```

### 8. Hill Climbing problems (THE classic figure — draw all 4 arrows)
```mermaid
flowchart LR
    subgraph Landscape["h-value landscape"]
        LM["🔺 LOCAL MAX<br/>stuck on small peak<br/>(goal = bigger peak behind)"]
        PL["⬛ PLATEAU<br/>flat: no direction<br/>looks better"]
        RG["〰️ RIDGE<br/>diagonal slope:<br/>single steps all worse"]
        GM["🏔️ GLOBAL MAX<br/>where you WANT to be"]
    end
```
> Hand-drawn version: draw mountains, mark ⭕ where the climber stands stuck. Fixes: **random-restart, simulated annealing**.

### 9. Minimax tree (back up values from leaves)
```mermaid
flowchart TD
    A["A (MAX)=4"] --- B["B (MIN)=3"]
    A --- C["C (MIN)=4"]
    B --- D["D (MAX)=3<br/>=min(1,3,2)"]
    B --- E["E (MAX)=2"]
    C --- F["F (MAX)=6<br/>=max(6,3)"]
    C --- G["G (MAX)=4<br/>=max(4,1)"]
    D --- H["1"]
    D --- I["3"]
    D --- J["2"]
    E --- K["2"]
    F --- L["6"]
    F --- M["3"]
    G --- N["4"]
    G --- O["1"]
```
> 2081 Q11 pattern: leaves 1,3,2,6,3,4,1 → answer **4 via C→G→M**. Draw triangles: MAX layers ▽ pick biggest, MIN layers △ pick smallest.

### 10. Alpha-Beta pruning (mark ✂ pruned branches)
```mermaid
flowchart TD
    R["ROOT (MAX) α=3"] --- B["B (MIN)=3"]
    R --- C["C (MIN)=2"]
    R --- D["D (MIN) ✂ PRUNED<br/>after first leaf: β=0 ≤ α=3"]
    B --- B1["3"]
    B --- B2["5"]
    B --- B3["6"]
    C --- C1["9"]
    C --- C2["1"]
    C --- C3["2"]
    D --- D1["0"]
    D --- D2["✂"]
    D --- D3["✂"]
```
> **Prune when α ≥ β.** In exam: write current (α, β) beside EVERY node, slash pruned edges, state root's final α.

---

## UNIT 4 — KNOWLEDGE REPRESENTATION

### 11. Semantic net (2082 Q7 — animals)
```mermaid
flowchart TD
    PUPPY["Puppy"] -->|"instance-of"| DOGS["Dogs"]
    TOM["Tom"] -->|"instance-of"| CATS["Cats"]
    DOGS -->|"hate"| CATS
    CATS -->|"chase"| RATS["Rats"]
    RATS -->|"are"| CLEVER["clever"]
```
> Inference = follow arrows: "What does Tom hate?" → Tom is-instance-of Cats; Dogs hate Cats... → chase chain etc.

### 12. Semantic net (Model Q10 — Ram)
```mermaid
flowchart TD
    RAM["Ram"] -->|"instance-of"| PERSON["Person"]
    PERSON -->|"is-a"| HUMAN["Humans"]
    HUMAN -->|"is-a"| MAMMAL["Mammals"]
    HUMAN -->|"has-part"| NOSE["Nose"]
    RAM -->|"has"| W["Weight: 60kg"]
    W -->|"less-than"| WS["Sita's weight"]
```

### 13. Frame (nested boxes — draw as boxes-in-boxes)
```
┌─────────────────────────────────────────────┐
│ ORGANIZATION: Tribhuvan University          │
│   org_type: Educational                     │
│  ┌───────────────────────────────────────┐  │
│  │ DEPARTMENT (is-a TU)                  │  │
│  │  ┌─────────────────────────────────┐  │  │
│  │  │ HR-DEPARTMENT (is-a DEPARTMENT) │  │  │
│  │  │   num_employees: 110            │  │  │
│  │  │   average_salary: 45000         │  │  │
│  │  │  ┌───────────────────────────┐  │  │  │
│  │  │  │ EMPLOYEE: Ram             │  │  │  │
│  │  │  │   age: 27  sex: male      │  │  │  │
│  │  │  │   dept: HR-DEPARTMENT     │  │  │  │
│  │  │  └───────────────────────────┘  │  │  │
│  │  └─────────────────────────────────┘  │  │
│  └───────────────────────────────────────┘  │
└─────────────────────────────────────────────┘
```

### 14. Script (RESTAURANT — draw as a scene strip)
```
[ENTRY: hungry + has money] → SCENE1: enter, sit → SCENE2: order
→ SCENE3: eat → SCENE4: pay, tip → [EXIT: less hungry, poorer]
Props: table menu food bill | Roles: customer waiter cook
```

### 15. Resolution flow (the proof machine)
```mermaid
flowchart TD
    A["Sentences in English"] --> B["FOPL: ∀x(X→Y), ∃x(X∧Y)"]
    B --> C["CNF: EMSSD<br/>Eliminate→, Move¬, Standardize,<br/>Skolemize, Distribute"]
    C --> D["NEGATE the goal → add as clause"]
    D --> E["Resolve pairs: A + ¬A cancel"]
    E --> F{"Empty clause □?"}
    F -->|No| E
    F -->|Yes| G["CONTRADICTION<br/>⇒ goal PROVED ∎"]
```

### 16. Forward vs Backward chaining
```mermaid
flowchart LR
    subgraph FWD["FORWARD (data-driven)"]
        direction LR
        F1["Facts"] -->|"apply rules →"| F2["New facts"] -->|"→ ... →"| F3["GOAL"]
    end
    subgraph BWD["BACKWARD (goal-driven)"]
        direction RL
        B1["GOAL"] -->|"what must be true?"| B2["Subgoals"] -->|"..."| B3["Facts"]
    end
```
> Forward = cooking with what's in the fridge. Backward = recipe-driven shopping. ES use: diagnosis.

### 17. Bayesian network (Model Q7)
```mermaid
flowchart TD
    C["Cloudy<br/>P=0.5"] --> R["Rain<br/>P=0.3 | C,W"]
    WI["Winter<br/>P=0.5"] --> R
    R --> SU["Sunny<br/>P=0.7"]
```
> Joint = Π P(node|parents): P(C,W,R,SU) = P(C)·P(W)·P(R|C,W)·P(SU|...). Label every node with its CPT.

### 18. Fuzzy set sketch
```
μ(x)
1.0 ┤                    ●━━━━━━━
0.5 ┤         ●━━━━━●
0.0 ━●━━━━●━━━━━━━━━━━━━━━━━━━▶ x
     10  20  30  40  50  60  70
     "LARGE": μ = {10:0, 20:.1, 30:.3, 40:.5, 50:.7, 60:.9, 70:1}
```
> Operators: union = **max**, intersection = **min**, complement = **1−μ**.

---

## UNIT 5 — MACHINE LEARNING

### 19. The neuron (mathematical model — MOST important diagram)
```mermaid
flowchart LR
    X1["x₁"] -->|w₁| SUM(("Σ + b"))
    X2["x₂"] -->|w₂| SUM
    X3["xₙ"] -->|wₙ| SUM
    SUM --> ACT["Activation f<br/>(step/sigmoid)"]
    ACT --> Y["output y"]
```
> Formula banner: **y = f(Σwᵢxᵢ + b)**. Bio mapping: dendrite→inputs, synapse→weights, soma→summer, axon→output.

### 20. Sigmoid (draw small graph beside activation answer)
```
σ(x)=1/(1+e⁻ˣ)
1.0 ┤              ╭───────
0.5 ┤         ╭────╯
0.0 ─────────╯─────────────▶ x
              0
```
> Squashes anything to (0,1); smooth & differentiable → enables backprop.

### 21. Multi-layer ANN (for backprop answer)
```mermaid
flowchart LR
    subgraph Input["Input layer"]
        I1["x₁"] 
        I2["x₂"]
    end
    subgraph Hidden["Hidden layer"]
        H1["h₁"]
        H2["h₂"]
    end
    subgraph Output["Output layer"]
        O1["y"]
    end
    I1 --> H1
    I1 --> H2
    I2 --> H1
    I2 --> H2
    H1 --> O1
    H2 --> O1
```
> Backprop arrows: forward ⇒, error flows backward ⇐ (draw dashed arrows back).

### 22. Backprop cycle (5-box loop)
```mermaid
flowchart LR
    A["1. FORWARD pass<br/>y = f(Σwx+b)"] --> B["2. ERROR<br/>E = ½(t−o)²"]
    B --> C["3. BACKWARD<br/>δₒ=(t−o)o(1−o)<br/>δₕ=h(1−h)Σδₒw"]
    C --> D["4. UPDATE<br/>Δw = η·δ·input"]
    D --> A
```

### 23. Hebb net for OR (final trained network)
```mermaid
flowchart LR
    X1["x₁"] -->|"w₁=2"| SUM(("Σ"))
    X2["x₂"] -->|"w₂=2"| SUM
    B["bias b=2"] --> SUM
    SUM --> F["f = step"]
    F --> Y["y (0/1)"]
```
> Show the 4-row training table (Δw = x·t) beside it — final: **w₁=2, w₂=2, b=2**.

### 24. GA crossover (2078 Q7)
```
One-point (after 4th bit):
  Parent1: 0110 │ 0010      Child1: 0110 1100
  Parent2: 1010 │ 1100      Child2: 1010 0010
Two-point (after bit 2 and 6):
  Parent1: 01 │ 1000 │ 10   Child1: 01 1001 10
  Parent2: 10 │ 1001 │ 00   Child2: 10 1000 00
Mutation:  01101100 → 01111100   (one random bit flips)
```

### 25. Supervised vs Unsupervised vs RL (3-panel sketch)
```
SUPERVISED:    [data + answer key] → learn mapping      (spam labels)
UNSUPERVISED:  [data, no labels]   → find clusters      ((•••)(••))
REINFORCEMENT: [agent ⇄ world]     → reward signal      (🎁 for good moves)
```

---

## UNIT 6 — APPLICATIONS

### 26. Expert system (KIUWE — draw for both ES questions)
```mermaid
flowchart TD
    U["USER"] -->|"queries"| UI["User Interface"]
    UI --> IE["INFERENCE ENGINE<br/>(match + fire rules)"]
    IE <--> KB["KNOWLEDGE BASE<br/>(facts + IF-THEN rules)"]
    IE <--> WM["WORKING MEMORY<br/>(current case facts)"]
    IE --> EX["Explanation Module<br/>'WHY did you ask that?'"]
    EX --> UI
    KE["Human Expert /<br/>Knowledge Engineer"] -->|"knowledge"| KB
```

### 27. NLP pipeline (draw as arrow strip)
```mermaid
flowchart LR
    T["Text"] --> LX["1. Lexical<br/>(tokens, running→run+ing)"]
    LX --> SY["2. Syntactic<br/>(parse tree, grammar)"]
    SY --> SE["3. Semantic<br/>(literal meaning)"]
    SE --> DI["4. Discourse<br/>(he = Ram?)"]
    DI --> PR["5. Pragmatic<br/>(intent: request?)"]
    PR --> O["Meaning"]
```
> Mnemonic: **L**azy **S**tudents **S**ee **P**ragmatic **D**iscourse. Example per box = full marks.

### 28. Machine vision system
```mermaid
flowchart LR
    L["Lighting"] --> CAM["Camera/Sensor"]
    CAM --> FG["Frame grabber<br/>(digitize + filter)"]
    FG --> FE["Feature extraction<br/>(edges, patterns)"]
    FE --> DEC["Decision unit<br/>(pass/fail, actuate)"]
```

### 29. Robot hardware
```mermaid
flowchart LR
    subgraph SENSES["Sensors"]
        P1["Proprioceptive:<br/>encoders, gyro,<br/>battery"]
        E1["Exteroceptive:<br/>camera, LiDAR,<br/>sonar, touch"]
    end
    SENSES --> BRAIN["Perception +<br/>Planning"]
    BRAIN --> EFF["EFFECTORS:<br/>motors, grippers,<br/>wheels"]
    EFF --> W["WORLD"]
    W --> SENSES
```

---

## 🎯 Diagram priority (if you only master 8)
1. **Neuron (19)** — appears 6/7 papers
2. **A\* formula box (7) + trace table**
3. **Minimax tree (9)** 
4. **Resolution flow (15)**
5. **Expert system KIUWE (26)**
6. **Agent structure (1)**
7. **NLP pipeline (27)**
8. **Bayesian network (17)**

*In the exam: draw FIRST, explain second. A labeled diagram + 4 bullets ≈ full marks even on a bad day.*
