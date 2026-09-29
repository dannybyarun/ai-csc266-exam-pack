# 🎓 Hour 3 Session Notes — ANN + GA + ML (the 3rd guaranteed topic)

*ANN appeared in 6/7 papers — often as the third 10-marker. This hour = 3 formulas, 1 big diagram, 1 solved table, 1 crossover trick.*

**Progress checklist:**
```
⬜ The neuron + math model
⬜ Hebb net for OR (solved table)
⬜ Perceptron rule
⬜ Backpropagation (5-step loop + worked numbers)
⬜ GA operators + crossover
⬜ ML types + Naive Bayes
⬜ Self-test
```

---

## 1. THE NEURON — one diagram to rule them all

```
x₁ ──w₁──┐
x₂ ──w₂──┤    ┌─────────┐      ┌──────────────┐
  ...     ├──>│ Σ wᵢxᵢ+b │ ───> │ activation f │ ───> y
xₙ ──wₙ──┘    └─────────┘      └──────────────┘
```
**y = f(Σ wᵢxᵢ + b)** — that's the entire math model.

**Bio mapping (1 free mark every time):**
| Biological | Artificial |
|---|---|
| Dendrite (receives) | inputs x |
| Synapse (signal strength) | weights w |
| Soma (sums signals) | summer Σ + bias b |
| Axon (sends output) | activation output y |

**Activation function:** the squash. **Sigmoid σ(x) = 1/(1+e⁻ˣ)** → squashes any number into (0,1), smooth & differentiable → that's WHY gradient learning (backprop) works. Also: step (1 if x≥θ else 0), linear, tanh, ReLU.

---

## 2. HEBB RULE — "fire together, wire together"

**Δw = x·t** (weight grows when input and target are both active). Unsupervised, no error term.

### ✅ Solved: Hebb net for OR (2082 Q8 — memorize this table)
Bipolar inputs, bias input = 1, targets t from OR truth table. Start w₁=w₂=b=0:

| Step | x₁ | x₂ | t | Δw₁ = x₁t | Δw₂ = x₂t | Δb = t | w₁ | w₂ | b |
|---|---|---|---|---|---|---|---|---|---|
| 1 | −1 | −1 | −1 | +1 | +1 | −1 | 1 | 1 | −1 |
| 2 | −1 | +1 | +1 | −1 | +1 | +1 | 0 | 2 | 0 |
| 3 | +1 | −1 | +1 | +1 | −1 | +1 | 1 | 1 | 1 |
| 4 | +1 | +1 | +1 | +1 | +1 | +1 | **2** | **2** | **2** |

**Final: w₁ = 2, w₂ = 2, b = 2** → y = sign(2x₁ + 2x₂ + 2): (0,0)→0 ✓ (0,1)→1 ✓ (1,0)→1 ✓ (1,1)→1 ✓ — OR works.

**Exam format:** rule → table → final network drawing (2 inputs → weights 2,2 → bias 2 → step → out) → verification line. Full marks.

---

## 3. PERCEPTRON — supervised error-correction

**w_new = w_old + η(t−y)x** and **b_new = b + η(t−y)** (η = learning rate).
- If prediction correct (t = y): no change. If wrong: weights nudge toward target.
- Algorithm: initialize → for each sample compute y → update → repeat until zero error.
- **Limitation (the trap):** only **linearly separable** problems — draws one straight line; **fails XOR**. XOR needs multi-layer + backprop. That last sentence bridges to the big question.

---

## 4. BACKPROPAGATION — the 10-mark answer

**Training a NN** = adjusting weights to minimize error between outputs and targets (supervised). Backprop = **gradient descent on the error**: roll the ball downhill on the error surface.

**The 5-step loop (draw as a cycle):**
```
1. FORWARD pass:   y = f(Σwx+b) layer by layer
2. ERROR:          E = ½(t − o)²
3. BACKWARD pass:  δₒ = (t−o)·o·(1−o)          (output layer, sigmoid)
                   δₕ = h(1−h)·Σ(δₒ·w_out)     (hidden layers — blame flows back)
4. UPDATE:         Δw = η·δ·input
5. Repeat over epochs until error small
```

### ✅ Worked one iteration (2081 Q1 asks exactly this):
Net: x₁=1, x₂=0 → hidden h → output o, target t=1, η=0.5, sigmoid.
Weights: w₁₁=0.2, w₂₁=0.4 (x→h), w_h=0.7 (h→o), biases 0.

```
FORWARD:  net_h = 1(0.2)+0(0.4) = 0.20  →  h = σ(0.2)  = 0.55
          net_o = 0.55×0.7 = 0.385      →  o = σ(0.385) = 0.595
ERROR:    E = ½(1−0.595)² = 0.082
DELTAS:   δₒ = (0.405)(0.595)(0.405) = 0.0976
          δₕ = (0.55×0.45)×(0.0976×0.7) = 0.0169
UPDATE:   w_h = 0.7 + 0.5×0.0976×0.55 = 0.727
          w₁₁ = 0.2 + 0.5×0.0169×1 = 0.208
          w₂₁ = 0.4 + 0.5×0.0169×0 = 0.4
→ error decreased; repeat for more epochs
```

**Comparison line (3 points = 3 marks):** Hebb = unsupervised Δw=x·t · Perceptron = supervised single-layer, linearly-separable only · Backprop = supervised multi-layer gradient descent, solves XOR.

**ANN types (bonus 2 marks):** feed-forward (no loops) vs recurrent (loops); single-layer vs multi-layer (hidden layers). Applications: OCR, speech, medical diagnosis, stock prediction.

---

## 5. GENETIC ALGORITHM — evolution as optimization

Population of chromosomes → **fitness** scores → survivors breed → repeat.

**Algorithm (7 steps):** initialize population → evaluate fitness → **selection** (fitter chosen; roulette wheel) → **crossover** (swap gene segments) → **mutation** (rare random bit flip) → replace population → repeat until termination.

**✅ Crossover solved (2078 Q7):** C1 = 01100010, C2 = 10101100
```
One-point (after bit 4):   Child1 = 0110|1100 = 01101100   Child2 = 1010|0010 = 10100010
Two-point (after bits 2,6):Child1 = 01|1001|10 = 01100110   Child2 = 10|1000|00 = 10100000
Mutation example:          01101100 → 01111100 (one bit flips)
```
**Operator definitions in one line each:** fitness = scores chromosomes · selection = survival of fittest · crossover = recombine parents · mutation = diversity + escape local optima.

**RL context if the question wraps GA in learning:** supervised (labels) / unsupervised (clusters) / reinforcement (rewards; passive = judge fixed policy, active = explore, model-free = no environment model, e.g. Q-learning). **Naive Bayes:** P(C|X) ∝ P(C)·ΠP(xᵢ|C), "naive" = feature independence given class, used for spam filtering.

---

## 6. ⚠️ COMMON TRAPS
1. Hebb uses **x·t** (no error term!) — don't mix with perceptron's (t−y).
2. Backprop **δ for output vs hidden differ** — hidden multiplies by incoming weights again (h(1−h)Σδw).
3. Crossover: **two-point swaps the MIDDLE segment**, not the outside pieces.
4. Sigmoid's job: **non-linearity + differentiability** — say both.
5. XOR = the reason multilayer exists. Mention it; examiners love the storyline.

## 7. POCKET RECAP
```
Neuron: y = f(Σwx+b). Dendrite→input, synapse→weight, soma→Σ, axon→out.
Hebb: Δw = x·t.        OR-net result: w₁=2, w₂=2, b=2.
Perceptron: w += η(t−y)x — linearly separable only, fails XOR.
Backprop: forward → error → δ back → Δw = η·δ·input → repeat.
GA: select → crossover → mutate, driven by fitness.
```

## 8. SELF-TEST
1. Write the neuron formula + bio mapping table (2 min, no peeking)
2. Redo the Hebb OR table from a blank page
3. Compute one backprop iteration with weights w₁₁=0.3, w_h=0.6, same inputs (t=1) — answers: h=0.549, o=0.574, δₒ≈0.092, w_h→0.625
4. One-point AND two-point crossover on C1=11001010, C2=00110101
