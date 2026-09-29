# Unit 5 — Machine Learning, ANN, Genetic Algorithms ⭐ (6/7 papers)

## Q: Concepts of learning; Supervised / Unsupervised / Reinforcement (Model Q9, 2079 Q11, 2081 Q5, 2082 Q3)

**Learning:** improving performance P on task T with experience E.

| Type | Data | How it works | Example |
|---|---|---|---|
| **Supervised** | labeled (input→correct output) | learn mapping f: X→Y; minimize error | spam filter, OR gate training |
| **Unsupervised** | unlabeled | find hidden structure/clusters | customer segmentation (K-means) |
| **Reinforcement** | reward signal from environment | agent acts → gets reward/penalty → updates policy | game-playing, robot navigation |

**Reinforcement learning extra points (2079 Q11, 2082 Q3):**
- **Example:** robot learning to walk — rewarded for distance moved, penalized for falling.
- **Passive RL:** agent learns value function of a **fixed policy** (just evaluates how good the given behavior is). **Active RL:** agent **decides its own actions** — explores to find optimal policy.
- **Model-free RL:** learns directly from rewards **without building a model** of environment transitions (e.g., Q-learning) — "model-based vs model-free" refers to whether transition probabilities are learned.

## Q: Naive Bayes model (Model Q9)

Statistical classifier under **supervised** learning. Bayes: `P(C|X) ∝ P(C) · Πᵢ P(xᵢ|C)`.
**"Naive" = assumes all features are independent given the class.**
- Training: count frequencies → P(C) and P(xᵢ|C) from data
- Classify: for each class compute P(C)·ΠP(xᵢ|C), pick the max
- Example: spam — P(spam)·P("free"|spam)·P("money"|spam)·… vs P(ham)·… — bigger wins.

## Q: Learning by Genetic Algorithms (2076 Q9, 2079 Q10, 2080 Q8, 2082 Q3, 2078 Q7)

**GA:** optimization/search inspired by natural evolution. Population of candidate solutions (chromosomes) evolves via fitness-based selection.

**Algorithm (write these 7 steps):**
1. Initialize random population of chromosomes
2. Evaluate **fitness** of each chromosome
3. **Selection** — choose parents (fitter = more likely; roulette wheel / tournament)
4. **Crossover** — combine two parents' genes
5. **Mutation** — flip random bits with small probability
6. Replace population with offspring
7. Repeat 2-6 until termination (generations / fitness threshold / no improvement)

**Operators defined:**
- **Fitness function:** scores how good each chromosome is (drives selection)
- **Selection:** survival of the fittest — probability of being chosen ∝ fitness
- **Crossover:** swap segments of two parent chromosomes at a crossover point
- **Mutation:** randomly flip a bit (0↔1) to maintain diversity & escape local optima

**✅ Solved 2078 Q7 — one-point & two-point crossover:** C1 = 01100010, C2 = 10101100.
Choose crossover point after 4th bit:
- **One-point (after position 4):** child1 = 0110 | 1100 = `01101100`; child2 = 1010 | 0010 = `10100010`
- **Two-point (after pos 2 and pos 6):** swap middle segments: child1 = 01 | 1001 | 10 = `01100110`; child2 = 10 | 1000 | 00 = `10100000`

## Q: Biological vs Artificial Neural Networks (2081 Q1)

| Biological | Artificial |
|---|---|
| **Dendrite** — receives signals | **inputs x₁…xₙ** |
| **Synapse** — connection strength between neurons | **weights w₁…wₙ** |
| **Cell body (soma)** — sums incoming signals | **summer Σ + bias b** |
| **Axon** — transmits output signal | **activation function output y** |
| Fires when potential exceeds threshold | fires when Σwx + b exceeds activation threshold |

## Q: Mathematical model of ANN (2076 Q3, 2078 Q3, Model Q3) — DRAW THIS

```
x₁ ──w₁──┐
x₂ ──w₂──┤    ┌─────────┐      ┌──────────────┐
  ...     ├──>│ Σ wᵢxᵢ+b │ ───> │ activation f │ ───> y
xₙ ──wₙ──┘    └─────────┘      └──────────────┘
```
**`y = f(Σᵢ wᵢxᵢ + b)`** — inputs weighted, summed with bias, passed through activation function.

**Activation function (2080 Q3):** introduces non-linearity; decides neuron firing. Types:
- **Linear:** f(x) = x
- **Step/binary:** f(x) = 1 if x ≥ θ else 0
- **Sigmoid:** σ(x) = 1/(1+e⁻ˣ) — squashes any input to (0,1); smooth, differentiable → enables gradient-based learning (backprop); large negative → 0, large positive → 1, at 0 → 0.5.
- (Also: tanh, ReLU — mention for bonus.)

## Q: Design Hebb net for logical OR (2082 Q8, 2081 Q5 "ANN neuron for OR")

**Hebb rule:** `Δwᵢ = xᵢ · t` — "neurons that fire together, wire together." Weights updated per training pair, bias: Δb = t.

OR truth table with bipolar inputs & targets (x₁, x₂ ∈ {−1,+1}):
| x₁ | x₂ | b | t |
|---|---|---|---|
| −1 | −1 | 1 | −1 |
| −1 | +1 | 1 | +1 |
| +1 | −1 | 1 | +1 |
| +1 | +1 | 1 | +1 |

**Weight calculations (start w₁=w₂=b=0):**
1. (−1,−1,t=−1): w₁ = 0+(−1)(−1)=1, w₂ = 1, b = −1
2. (−1,+1,t=+1): w₁ = 1+(−1)(1)=0, w₂ = 1+(1)(1)=2, b = −1+1 = 0
3. (+1,−1,t=+1): w₁ = 0+1 = 1, w₂ = 2−1 = 1, b = 1
4. (+1,+1,t=+1): w₁ = 1+1 = 2, w₂ = 1+1 = 2, b = 1+1 = 2

**Final Hebb net: w₁ = 2, w₂ = 2, b = 2** — test: y = sign(2x₁+2x₂+2): (−1,−1)→−2<0→0 ✓, (−1,1)→2>0→1 ✓, (1,−1)→2→1 ✓, (1,1)→6→1 ✓. **OR implemented.** Draw final network: two inputs ×2 weights each, bias 2, step activation.

## Q: Perceptron learning (2080 Q3, 2078 Q3)

**Perceptron:** single-layer ANN with step activation; learns linearly separable functions.
**Algorithm:**
1. Initialize weights (small random / 0), set learning rate η
2. For each training pair (X, t): compute y = f(Σwᵢxᵢ)
3. Update: **wᵢ(new) = wᵢ(old) + η(t−y)xᵢ**; b(new) = b + η(t−y)
4. Repeat until no weight changes (all correct) or epochs max

(t−y) = 0 when correct — no change; pushes weights toward correct classification. Limitation: **only linearly separable problems** (fails XOR → motivates multilayer + backprop).

## Q: Backpropagation (Model Q3, 2081 Q1) — the 10-mark answer

**ANN types first (1-2 marks):** **Feed-forward** (signals one way, no loops) vs **Recurrent** (has loops/feedback); **Single-layer** (one weight layer) vs **Multi-layer** (hidden layers). Applications: pattern recognition, OCR, speech, stock prediction, medical diagnosis.

**Training = adjusting weights to minimize error between output and target.** Supervised: present input → compute output → measure error → adjust weights → repeat.

**Backpropagation = gradient descent on error.** Two passes per example:

1. **Forward pass:** inputs flow through network, each neuron: y = f(Σwx+b); compute output o
2. **Error computation:** E = ½(t − o)²
3. **Backward pass:** send error backward from output to hidden layers:
   - Output layer delta: δₒ = (t − o)·o·(1−o)  [uses sigmoid derivative]
   - Hidden layer delta: δₕ = h(1−h) · Σ (δₒ·w_out)
4. **Weight update:** Δw = η · δ · input (η = learning rate)
5. Repeat over all training examples until error is acceptably small (epochs)

**✅ Worked mini-example (2081 Q1 asks for one iteration):**
Network: 2 inputs (x₁=1, x₂=0), one hidden neuron h, one output o. Targets t=1. η=0.5, sigmoid f.
Initial: w₁₁=0.2 (x₁→h), w₂₁=0.4 (x₂→h), w_h=0.7 (h→o), biases 0.

- **Forward:** net_h = 1(0.2)+0(0.4) = 0.2 → h = σ(0.2) = 0.55; net_o = 0.55×0.7 = 0.385 → o = σ(0.385) = 0.595
- **Error:** E = ½(1−0.595)² = 0.082
- **Output delta:** δₒ = (t−o)·o(1−o) = (0.405)(0.595)(0.405) = 0.0976
- **Hidden delta:** δₕ = h(1−h)·δₒ·w_h = (0.55×0.45)(0.0976×0.7) = 0.2475×0.0683 = 0.0169
- **Updates:** w_h = 0.7 + 0.5×0.0976×0.55 = **0.727**; w₁₁ = 0.2 + 0.5×0.0169×1 = **0.208**; w₂₁ = 0.4 + 0.5×0.0169×0 = 0.4
- Error decreased → repeat for more epochs.

**Hebbian vs Perceptron vs Backprop (1-line each for comparison marks):** Hebb = unsupervised correlation rule Δw=x·t; Perceptron = supervised single-layer, error-driven, linearly separable only; Backprop = supervised multilayer, gradient descent, handles non-linear (XOR-solvable).

---

### ⚡ 30-second recall
> Supervised=labeled, Unsupervised=clusters, RL=reward. Naive Bayes = P(C)·ΠP(xᵢ|C), independence assumption. GA = select→crossover→mutate. Neuron: y = f(Σwx+b). Hebb: Δw = x·t. Perceptron: w += η(t−y)x. Backprop = forward→error→deltas backward→Δw = η·δ·input. Sigmoid squashes to (0,1), differentiable.
