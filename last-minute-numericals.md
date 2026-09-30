# 🧮 LAST-MINUTE NUMERICALS — 5 recipes, ~15 minutes, 10-15 marks

*2-3 of these appear every single year. All mechanical — plug and chug. Learn #1 and #3 minimum.*

## #1 BAYES FORMULA ⭐⭐ (5/7 papers in some form — 5 marks)
```
P(H|E) = P(E|H) × P(H) ÷ P(E)
```
- H = hypothesis (what you WANT), E = evidence (what you KNOW)
- Steps: identify H & E from the story → write the formula → plug the 3 given numbers
- **2078 solved:** P(Disease|Alcoholic) = (0.07 × 0.15) / 0.05 = **0.21**
- **Mock solved:** (0.90 × 0.20) / 0.34 = **0.529**
- Vocabulary marks: prior = P(H) before evidence · posterior = P(H|E) after evidence · "why needed": decisions must update with new evidence
- If P(E) not given: P(E) = P(E|H)P(H) + P(E|¬H)P(¬H)

## #2 FULL JOINT TABLE (2076 — 5 marks)
```
P(query | evidence) = (cells matching query AND evidence) ÷ (all cells matching evidence)
```
**Solved:** P(len=130 | width=15) = 0.42 / (0.12+0.42+0.06) = 0.42/0.60 = **0.7**

## #3 HEBB NET FOR OR ⭐⭐ (2081 & 2082 both — 5 marks) — FIXED ANSWER
Rule: **Δwᵢ = xᵢ·t, Δb = t** — start w₁=w₂=b=0, bipolar inputs:
| x₁ | x₂ | t | w₁ | w₂ | b |
|---|---|---|---|---|---|
| −1 | −1 | −1 | 1 | 1 | −1 |
| −1 | +1 | +1 | 0 | 2 | 0 |
| +1 | −1 | +1 | 1 | 1 | 1 |
| +1 | +1 | +1 | **2** | **2** | **2** |
**Final: w₁=2, w₂=2, b=2** → y = sign(2x₁+2x₂+2) → 0,1,1,1 = OR ✓

## #4 GA CROSSOVER (2078 — 5 marks)
```
One-point (after bit k): exchange the TAILS of the two parents
Two-point (bits k,l): exchange only the MIDDLE segment
```
2078: C1=0110|0010, C2=1010|1100 → Child1=01101100, Child2=10100010
Mutation = flip one random bit. That's the whole question.

## #5 FUZZY + MINIMAX (fillers)
```
Fuzzy: union = max(μ) · intersection = min(μ) · complement = 1−μ — element-wise
Minimax: leaves given → MIN nodes take min of children, MAX take max, climb to root
Alpha-beta: prune the moment α ≥ β
```

## Mark expectation
Bayes (5) + Hebb (5) = 10 marks for ~10 minutes of memorizing. Add crossover/fuzzy when they appear = up to 15. These + the two 10-mark skeletons = 30+ marks from pure recipes.
