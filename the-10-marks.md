# 🎯 THE 10 MARKS — the only thing you must UNDERSTAND (not memorize)

**Why this one:** "Convert to FOPL + prove by resolution" appeared in ALL 7 papers (2076, 2078, 2079-Q8, 2080-Q2, 2081-Q2, Model-Q2, +2082 variants) — almost always as a Section A 10-marker. It's mechanical: no intuition, no luck. Understand the 5 items below → guaranteed 10 marks, every year.

---

## The 5 understandings (that's all)

### 1. Three sentence patterns = the entire conversion
```
All  X are Y  →  ∀x (X(x) → Y(x))      "all" = IF-THEN
Some X are Y  →  ∃x (X(x) ∧ Y(x))      "some" = one thing is BOTH
Names (Gita, Harry)  →  constants      gita, harry — never quantified
```
**Understand why:** "All dogs are animals" can't be ∀(Dog ∧ Animal) — that says everything is a dog! It's a conditional: IF dog THEN animal. "Some dogs are pets" asserts one thing is BOTH — that's why ∧.

### 2. Negate the goal (this IS the method)
To prove G, add **¬G** as a clause, then derive a contradiction.
**Why:** refutation — like a detective assuming the suspect is innocent, then showing the evidence contradicts it. Contradiction ⇒ the assumption (¬G) was false ⇒ G true.

### 3. Cancellation rule
Two clauses cancel on a complementary pair: **A and ¬A disappear**, everything else merges into a new clause. If variables don't literally match (y vs Harry), write the substitution **{y/Harry}** — that's unification, and writing it = marks.

### 4. □ = proved
Keep canceling until a clause has **nothing left** (empty clause). Empty = contradiction = "hence the goal is proved ∎". Write that closing line — it's a mark.

### 5. CNF = just get rid of → and ¬( )
For exam sentences, the 5 formal steps (Eliminate→, Move¬, Standardize, Skolemize, Distribute) reduce to: replace A→B with ¬A∨B, push ¬ inside, name the "someone" (Skolem constant), drop ∀. Name the 5 steps in your answer for theory marks.

---

## The skeleton (runs on every exam proof — this shape = 10/10)

```
STEP 1  Convert each sentence to FOPL          [3 marks]
STEP 2  List CNF clauses, ADD negated goal      [2 marks]
STEP 3  Resolve chain with substitutions        [4 marks]
STEP 4  "Empty clause ⇒ proved ∎"               [1 mark]
```

**Live example (Model Q2 — "Roney is naughty"):**
Facts: over-smart→stupid · stupid's children→naughty · Roney child of Harry · Harry over-smart.
```
C1: ¬OverSmart(y) ∨ Stupid(y)
C2: ¬Stupid(y) ∨ ¬Child(x,y) ∨ Naughty(x)
C3: Child(Roney, Harry)          (unused — decoys are normal!)
C4: OverSmart(Harry)
C5: ¬Naughty(Roney)              ← negated goal

C4 + C1 {y/Harry}          → C6: Stupid(Harry)
C6 + C2 {y/Harry, x/Roney} → C7: Naughty(Roney)
C7 + C5                    → □   ⇒ proved ∎
```

**Self-check you UNDERSTAND (not memorized):** can you answer — *why* did C4+C1 produce Stupid(Harry) and not something else? (Answer: C4 is OverSmart(**Harry**); C1 says ¬OverSmart(y)∨Stupid(y); setting y=Harry makes OverSmart(Harry) cancel its negation, leaving Stupid(Harry). The fact feeds the rule, the rule outputs a new fact.) If yes — you own 10 marks. 🎯
