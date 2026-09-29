# 🎓 Hour 2 Session Notes — FOPL → RESOLUTION (the other guaranteed 10-marker)

*Same style as Hour 1: concept first, YOUR-voice analogies, worked trace, traps flagged. This topic appears in 7/7 past papers — master this and Section A is 2/2 secured.*

**Progress checklist:**
```
⬜ FOPL conversion (English → symbols)
⬜ CNF in 5 steps (EMSSD)
⬜ Resolution proof by refutation
⬜ Full proof walked through
⬜ Self-test
```

---

## 1. THE BIG PICTURE (30 seconds)

The computer can't reason with English. Two-phase machine:

```
PHASE 1: TRANSLATE          PHASE 2: PROVE
English sentences   ──▶     FOPL symbols  ──▶  push symbols around
                            (CNF clauses)      until contradiction
```
Phase 1 = FOPL conversion. Phase 2 = resolution. The exam gives you facts in English + a conclusion. You translate, then *mechanically* prove it. **No intuition needed — it's symbol pushing.**

---

## 2. FOPL CONVERSION — 4 patterns cover 95% of exams

| English | FOPL | Memory hook |
|---|---|---|
| All X are Y | ∀x (X(x) → Y(x)) | "all" = IF…THEN (→) |
| Some X are Y | ∃x (X(x) ∧ Y(x)) | "some" = there IS one doing BOTH (∧) |
| No X are Y | ∀x (X(x) → ¬Y(x)) | all X's are non-Y |
| Names (Laxmi, Harry) | constants: laxmi, harry | proper nouns never get quantifiers |

**Why → for "all" but ∧ for "some"?** (understand once, never mix up again)
- "All dogs are animals": you can't say ∀x(Dog ∧ Animal) — that claims EVERYTHING is a dog! You mean: *IF* something is a dog, *THEN* it's an animal.
- "Some dogs are pets": you CAN say ∃x(Dog ∧ Pet) — you're claiming one specific thing is both. "∃ Dog → Pet" would be vacuous nonsense (it's true even if no dogs exist).

**Multi-word sentences:** "Children of stupid people are naughty" = a relation:
∀x∀y ( Stupid(y) ∧ Child(x,y) → Naughty(x) )
Read it out loud: "for all x, for all y: IF y is stupid AND x is y's child THEN x is naughty." Always: quantifiers → IF-part with ∧ → THEN-part single fact.

---

## 3. CNF — the 5 steps (EMSSD)

Resolution needs clauses (things joined only by ∨). Convert everything:

1. **E — Eliminate** → and ↔ : A→B becomes ¬A∨B
2. **M — Move ¬ inward**: De Morgan ¬(A∧B) = ¬A∨¬B; quantifier flips ¬∀x φ = ∃x¬φ, ¬∃x φ = ∀x¬φ
3. **S — Standardize variables**: rename so each quantifier has its own variable (two ∀x's → make one ∀y)
4. **S — Skolemize**: remove ∃. If ∃ has no ∀ above it → replace with a **Skolem constant** (invented name, e.g., THE-one); if ∃ sits inside ∀x → **Skolem function** of x (e.g., Salary(x))
5. **D — Distribute / drop ∀**: drop the universal quantifiers, distribute ∨ over ∧ → bag of clauses

> **Skolem constant exam-definition (2079 asked it directly):** *"A Skolem constant is a newly invented constant introduced during Skolemization to replace an existential variable — it names 'the unknown thing that must exist' for the statement to be true."*

---

## 4. RESOLUTION — proof by refutation (the script)

**The idea (detective analogy):** to prove the suspect guilty, assume he's INNOCENT, then collect facts until the story contradicts itself. Contradiction = your assumption was wrong = he's guilty.

**The mechanical script (write this structure every time):**
1. Convert all facts to clauses (CNF)
2. **Negate the conclusion**, add it as a clause
3. Resolve: pick two clauses sharing a complementary pair (A and ¬A), apply the substitution, cancel the pair, write the new clause
4. Repeat until you derive the **empty clause □**
5. Closing line: *"Since the negation of the goal led to an empty clause (contradiction), the goal is proved."* ∎

---

## 5. ✅ FULL WORKED PROOF (Model Q2 — "Roney is naughty")

**Given:**
1. All over-smart persons are stupid
2. Children of all stupid persons are naughty
3. Roney is child of Harry
4. Harry is over-smart
**Prove: Naughty(Roney)**

**Step A — FOPL:**
- ∀x (OverSmart(x) → Stupid(x))
- ∀x∀y (Stupid(y) ∧ Child(x,y) → Naughty(x))
- Child(Roney, Harry)
- OverSmart(Harry)

**Step B — CNF clauses (after EMSSD):**
```
C1: ¬OverSmart(y) ∨ Stupid(y)
C2: ¬Stupid(y) ∨ ¬Child(x,y) ∨ Naughty(x)
C3: Child(Roney, Harry)
C4: OverSmart(Harry)
C5: ¬Naughty(Roney)        ← negated goal, ADDED by us
```

**Step C — resolve:**
```
C4 + C1  {y/Harry}            →  Stupid(Harry)            [C6]
C6 + C2  {y/Harry, x/Roney}   →  Naughty(Roney)           [C7]
C7 + C5                       →  □  EMPTY CLAUSE
```
**Closing:** contradiction ⇒ ¬Naughty(Roney) is false ⇒ **Naughty(Roney) proved** ∎

*(Notice C3 was never used — that's fine, extra facts are decoys. And in 2080 Q2, facts "Laxmi beautiful / Rojina smart" were decoys too. Don't force every fact into the proof.)*

**The 4 other proofs are solved step-by-step in `solutions/unit-4-knowledge-representation.md`** (Laxmi, mustard, Anmol/Pugu, traffic/driver). Same skeleton every time.

---

## 6. ⚠️ COMMON TRAPS (check yourself on each)

1. **Forgetting to negate the goal** — without ¬Goal in the clause list, you're not doing refutation. Always show that step; it carries marks.
2. **Mixing → and ∧** — "all X are Y" with ∧ is the #1 error. All = →, Some = ∧.
3. **Substitution not written** — write {y/Harry} beside every resolution step. It's "unification" — naming it earns theory marks (unification = finding substitution making two expressions identical; lifting = applying resolution to FOL via unification — 2079 short note!).
4. **Skipping the closing line** — "hence proved by contradiction ∎" = the last mark.
5. **Skolem function vs constant** — ∃ inside ∀ → function of that variable (Salary(x)); plain ∃ → constant.

---

## 7. Also in this hour (15 min each, from solutions/unit-4):
- **Forward vs backward chaining:** forward = facts→goal (data-driven, monitoring); backward = goal→facts (goal-driven, diagnosis/ES)
- **Full-joint numerical:** P(query|evidence) = matching cells ÷ evidence cells → 2076 answer 0.42/0.60 = 0.7
- **Bayes numerical recipe:** posterior = P(E|H)·P(H) ÷ P(E) → 2078 answer (0.07×0.15)/0.05 = 0.21

---

## 8. POCKET RECAP (whole hour in 6 lines)

```
All X are Y = ∀x(X→Y)  ·  Some X are Y = ∃x(X∧Y)
CNF = EMSSD: Eliminate→, Move¬, Standardize, Skolemize, Distribute
PROOF = negate goal → add clause → cancel A/¬A pairs → □ = proved
Always write substitutions {y/Harry} + closing line ∎
Unification = substitution making terms identical; lifting = FOL resolution
Bayes: posterior = P(E|H)·P(H)/P(E);  full joint: matching ÷ evidence
```

## 9. SELF-TEST (do on paper, then check solutions/unit-4)
1. Convert: "Some students are intelligent" + "All intelligent students pass"
2. Name the 5 CNF steps
3. What is a Skolem constant?
4. Run the full resolution proof for #1's conclusion "Some students pass"
