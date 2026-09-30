# 🧠 UNDERSTAND RESOLUTION — nothing else in this file

*Forget exam format for a moment. By the end of this file you will know WHY resolution works — and once you know why, you can never forget how.*

---

## 1. The one sentence

**Resolution is a machine that proves things by finding contradictions.**

That's the whole idea. Everything else is mechanics.

---

## 2. Why contradiction proves anything (the core trick)

You want to prove: *"Roney is naughty."*

Trick: **temporarily assume the opposite** — "Roney is NOT naughty" — and add it to your facts. Then push the facts around. Two things can happen:

- The facts live together peacefully → your proof failed (for now)
- The facts **crash into each other** → the world can't be like this → the crash happened *because* of your added assumption → the assumption is WRONG → **"Roney IS naughty" is true.**

> 🕵️ Detective version: to prove the suspect guilty, assume he's innocent. But then his alibi contradicts the camera footage. Contradiction. So "innocent" is impossible → guilty.

That is **refutation** — proof by refuting the opposite. Resolution is just the mechanical procedure for finding that crash.

---

## 3. What the machine eats: clauses

A **clause** is a line of facts joined by **OR (∨)**, where some may be negated (¬ = "not"):

```
¬OverSmart(y) ∨ Stupid(y)
meaning: "y is not over-smart, OR y is stupid"
        (in practice: IF y is over-smart THEN y is stupid — same thing!)
```

⭐ Key insight: **¬A ∨ B is secretly the IF-THEN.** "Not over-smart OR stupid" = "if over-smart, then stupid." That's why we convert all sentences to clause form — the machine only understands this one shape.

Every exam sentence collapses to clauses:
```
All readers are studious        →  ¬Reader(y) ∨ Studious(y)
Roney is child of Harry         →  Child(Roney, Harry)   (already a clause)
Gita is studious (the goal)     →  Studious(Gita)
     and the negated goal       →  ¬Studious(Gita)
```

---

## 4. The single move: cancel A with ¬A

The machine knows exactly one move:

> If two clauses contain **the same thing, one positive and one negative**, that pair destroys itself, and the leftovers merge into a new clause.

```
Clause 1:  ¬OverSmart(Harry) ∨ Stupid(Harry)
Clause 2:  OverSmart(Harry)
                ↓  OverSmart(Harry) and ¬OverSmart(Harry) cancel
Result:    Stupid(Harry)
```

That's it. That's resolution. Cancel a +/− pair, merge what survives.

---

## 5. Substitution: when names don't match yet

Clauses have placeholder variables (x, y) instead of real names:

```
C1: ¬OverSmart(y) ∨ Stupid(y)      "any y that's over-smart is stupid"
C4: OverSmart(Harry)               (Harry is a real name)
```

y and Harry don't literally match — so **set y = Harry** and write it: **{y/Harry}**.
Now the pair matches, cancellation fires:

```
C1 {y/Harry}: ¬OverSmart(Harry) ∨ Stupid(Harry)
C4:           OverSmart(Harry)
    → cancel → Stupid(Harry) ✓
```

**What just happened, in plain words:** C4 is a fact, C1 is a rule. The fact fed the rule's condition, and the rule produced a NEW fact. That's all a substitution is: matching the placeholder to the real name so a fact can enter a rule.

---

## 6. The crash: the empty clause □

Keep going. Eventually you produce a clause against the negated goal:

```
C9: Studious(Gita)                (derived from the facts)
C6: ¬Studious(Gita)               (the assumption you added)
    → cancel → nothing left → you wrote the EMPTY clause: □
```

A clause with nothing in it says... **nothing. Falsehood. "A and not-A" at the same time.** The set of facts is now contradictory — impossible. Since the ONLY thing you added was the negated goal, the blame falls on it: **the negated goal is false, so the goal is TRUE.**

□ = the crash = proved. Write: *"Since negation of the goal led to an empty clause (contradiction), the goal is proved." ∎*

---

## 7. The full machine, assembled (Roney, slowly)

**Facts:**
1. All over-smart persons are stupid → `¬OverSmart(y) ∨ Stupid(y)`
2. Children of stupid persons are naughty → `¬Stupid(y) ∨ ¬Child(x,y) ∨ Naughty(x)`
3. Roney is child of Harry → `Child(Roney, Harry)`
4. Harry is over-smart → `OverSmart(Harry)`

**Assume the opposite of the goal:** `¬Naughty(Roney)` ← clause C5

**Now just feed facts into rules until something crashes:**

```
C4 (fact: OverSmart(Harry)) enters rule 1 via {y/Harry}
    → new fact: Stupid(Harry)

Stupid(Harry) enters rule 2 via {y/Harry, x/Roney}
    (rule 2 needs a stupid PARENT y and a CHILD x of that parent —
     we have Harry as parent, Roney as the child — both match!)
    → new fact: Naughty(Roney)

Naughty(Roney) vs C5 ¬Naughty(Roney)
    → cancel → □ CRASH!
```

**The story in one breath:** Harry is over-smart; over-smart people are stupid, so Harry is stupid; stupid people's children are naughty, and Roney is Harry's child, so Roney is naughty — which contradicts our assumption, so Roney IS naughty.

See it? You just *understood* resolution. It's feeding facts through rules until the assumption gets squashed.

---

## 8. FAQ (the confusions that cost marks)

**Why negate the goal first?**
Because resolution can only find contradictions — it can't build positive proofs. So we force one: add the opposite of what we want, and let the contradiction prove it.

**Why ∨ (OR) and not →?**
The machine's only move (canceling A/¬A) needs everything as flat OR-lists. ¬A ∨ B *is* A→B in disguise, so nothing is lost.

**What if a fact never gets used?**
Normal! In the Roney proof, "Child(Roney, Harry)"… wait, that one IS used. But in the Gita proof, "Sita is a student" was never needed. Papers plant decoy facts on purpose. Don't force them in.

**Skolem constant?**
When a sentence says "someone/some thing exists" (∃) with no variable to tie it to, give the mystery thing a name — that name is a Skolem constant. It only matters when sentences use "some" — most exam proofs just use "all" + facts.

**What is unification / lifting (the theory words)?**
Unification = finding the substitution ({y/Harry}) that makes two literals match. Lifting = using this trick to run resolution on predicate logic instead of plain propositional logic. Name-drop both when explaining steps — instant theory marks.

---

## 9. Prove you got it (60-second self-test)

Without scrolling up:

1. What do you add to the facts before resolving, and why?
2. C1: ¬Reader(y) ∨ Studious(y) and C: Reader(Gita) — what's the substitution and the output clause?
3. What does □ mean physically, and what does it prove?

<details>
<summary>Answers</summary>

1. The negated goal — because resolution proves by contradiction (refutation).
2. {y/Gita} → output: Studious(Gita).
3. A clause with nothing in it = contradiction = the added negation is false = the original goal is true.
</details>

**If you answered all three: you understand resolution. Now go do the Roney proof once on paper — understanding + one practice run = your 10 marks.** 🎯
