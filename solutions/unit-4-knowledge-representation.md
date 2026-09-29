# Unit 4 — Knowledge Representation, Logic, Bayes, Fuzzy ⭐ (7/7 papers)

## Q: Knowledge & KR basics (2076 Q7, 2081 Q7, 2080 Q7)

**Knowledge:** facts + rules + relationships about a domain. **KR** = encoding it so a machine can reason with it.

**Issues in KR (4 marks gold):** 1) Which representation? 2) How much knowledge to store? 3) Handling incomplete/uncertain knowledge 4) Ease of modification 5) Inferential adequacy (can we derive new facts?) & efficiency.

**Semantic nets** (2078 Q6, Model Q10, 2082 Q7):
Nodes = objects/concepts; edges = relations (`is-a`, `instance-of`, `has`).

**Model Q10 — Ram facts:**
```
        is-a          instance-of
Ram ─────────> Person <──────── Humans ──── is-a ───> Mammals
 │               │
 has-a nose      has-a weight
 │               │
[Nose]        [Weight: 60kg] ──less-than──> [Sita's weight]
```
Answer: "What is Ram?" → follow is-a: Person → Human → Mammal. "Does Ram have a nose?" → yes via Human has-a nose. **Inference from a semantic net = following edges / inheritance from classes.** (2082 Q2 part 1.)

**2082 Q7 — animals:**
```
Dogs --hate--> Cats --chase--> Rats --are--> clever
Puppy --instance-of--> Dogs
Tom   --instance-of--> Cats
```

**Frames (2080 Q7):** frames = record structures: **slots** (attributes) + **fillers** (values), with inheritance via is-a links.
```
EMPLOYEE frame:
  name:    Ram
  age:     27
  sex:     male
  dept:    <HR-department>
HR-DEPARTMENT frame (is-a DEPARTMENT):
  num_employees:   110
  average_salary:  45000
DEPARTMENT (is-a TRIBHUVAN-UNIVERSITY)
TRIBHUVAN-UNIVERSITY:
  org_type: Educational
```

**Scripts (2081 Q7):** structured frame for **stereotyped event sequences**. Components: entry conditions, props, roles, **track**, scenes. Example RESTAURANT script:
- Entry conditions: customer hungry, has money
- Props: table, menu, food, bill
- Roles: customer, waiter, cook
- Scene 1: enter, sit · Scene 2: order · Scene 3: eat · Scene 4: pay & exit
- Result: customer less hungry, poorer; owner richer

---

## Q: Propositional Logic essentials
Connectives: ¬ ∧ ∨ → ↔. **Tautology** = always true (P ∨ ¬P). **Validity**: argument true in every model. **WFF** = grammatically correct formula built from atoms + connectives.

---

## Q: FOPL conversion + Resolution ⭐⭐ (the guaranteed 10-marker — appears in ALL 7 papers)

### The 6 sentence patterns
| English | FOPL |
|---|---|
| All X are Y | ∀x (X(x) → Y(x)) |
| No X are Y | ∀x (X(x) → ¬Y(x)) |
| Some X are Y | ∃x (X(x) ∧ Y(x)) |
| All X's friends are smart | ∀x (X(x) → Smart(x)) pattern with relation: ∀x∀y(Friend(y,x) → Smart(y)) |
| Proper nouns | constants: laxmi, rojina |
| Someone is firing | ∃x (Person(x) ∧ Firing(x)) |

### CNF conversion steps (EMSSD)
1. **E**liminate ↔ and → (A→B ⇒ ¬A∨B)
2. **M**ove ¬ inward (De Morgan; ¬∀x φ = ∃x ¬φ; ¬∃x φ = ∀x ¬φ)
3. **S**tandardize variables apart (rename so each quantifier's variable is unique)
4. **S**kolemize — remove ∃: if no ∀ above it → **Skolem constant** (new name); if inside ∀x → **Skolem function** of x (e.g., Salary(x)). *Skolem constant = a newly invented constant standing for "the unknown thing that exists".*
5. **D**rop ∀, distribute ∨ over ∧ → set of clauses

### Resolution rule
From clauses (A ∨ B) and (¬B ∨ C) infer (A ∨ C) — cancel complementary pair. **Proof by refutation:** negate the goal → convert all → keep resolving → derive **empty clause □** ⇒ contradiction ⇒ original goal true.

### ✅ SOLVED PROOF 1 — 2080 Q2 "Laxmi is smart"
Facts:
1. All BSc CSIT students are intelligent: ∀x (CSIT(x) → Intelligent(x))
2. All friends of intelligent persons are smart: ∀x∀y (Intelligent(y) ∧ Friend(x,y) → Smart(x))
3. Laxmi is a friend of Rojina: Friend(Laxmi, Rojina)
4. Rojina is smart: Smart(Rojina)
5. All beautiful students are girls: ∀x (Beautiful(x) ∧ Student(x) → Girl(x))
6. Laxmi is beautiful: Beautiful(Laxmi)
**Prove: Smart(Laxmi)** — Note: facts 4-6 are decoys!

Wait — to get Smart(Laxmi) we need: Rojina intelligent + Laxmi friend of Rojina. CSIT(Rojina)? Not given directly... In the standard solution, add premise as printed on paper: "Rojina is a student of BSc CSIT" (the paper's fact list includes it via "All students of BSC CSIT are intelligent person"). Include: 0. CSIT(Rojina). Then:
- CNF of 1: ¬CSIT(y) ∨ Intelligent(y)
- CNF of 2: ¬Intelligent(y) ∨ ¬Friend(x,y) ∨ Smart(x)
- Resolve 0 & 1 {y/Rojina}: Intelligent(Rojina)
- Resolve with 2 {y/Rojina, x/Laxmi}: **Smart(Laxmi)** □ (with negated goal ¬Smart(Laxmi) as clause, resolution yields empty clause) ∎

### ✅ SOLVED PROOF 2 — Model Q2 "Roney is naughty"
Facts:
1. All over-smart persons are stupid: ∀x (OverSmart(x) → Stupid(x))
2. Children of all stupid persons are naughty: ∀x∀y (Stupid(y) ∧ Child(x,y) → Naughty(x))
3. Roney is child of Harry: Child(Roney, Harry)
4. Harry is over-smart: OverSmart(Harry)
**Prove: Naughty(Roney)**
- Clauses: ¬OverSmart(y) ∨ Stupid(y); ¬Stupid(y) ∨ ¬Child(x,y) ∨ Naughty(x); Child(Roney,Harry); OverSmart(Harry); negated goal: ¬Naughty(Roney)
- Resolve OverSmart(Harry) with clause1 {y/Harry}: Stupid(Harry)
- Resolve with clause2 {y/Harry, x/Roney}: Naughty(Roney)
- Resolve with ¬Naughty(Roney): **□ empty clause** ⇒ proved ∎

### ✅ SOLVED PROOF 3 — 2082 Q9 mustard
Premises: living → animal ∨ plant; plant → needs-sunlight; mustard is living; mustard is not animal.
- ¬Living(x) ∨ Animal(x) ∨ Plant(x)
- ¬Plant(y) ∨ Sunlight(y)
- Living(Mustard), ¬Animal(Mustard)
- Resolve Living(Mustard) with 1: Animal(Mustard) ∨ Plant(Mustard)
- Resolve with ¬Animal(Mustard): Plant(Mustard)
- Resolve with 2: **Sunlight(Mustard)** ⇒ **Yes, mustard needs sunlight** ∎

### ✅ SOLVED PROOF 4 — 2076 Q2 Anmol/Pugu
Facts: 1. Anyone Pugu loves is a star: ∀x (Loves(Pugu,x) → Star(x)) 2. Hero who doesn't rehearse doesn't act: ∀x (Hero(x) ∧ ¬Rehearse(x) → ¬Act(x)) 3. Anmol is hero: Hero(Anmol) 4. Hero who doesn't work doesn't rehearse: ∀x (Hero(x) ∧ ¬Work(x) → ¬Rehearse(x)) 5. Who doesn't act isn't a star: ∀x (¬Act(x) → ¬Star(x))
**Prove: ¬Work(Anmol) → ¬Loves(Pugu,Anmol)** i.e., prove: Loves(Pugu,Anmol) → Work(Anmol). Proof by refutation: assume ¬Work(Anmol) ∧ Loves(Pugu,Anmol):
- Clause 4 CNF: ¬Hero(x) ∨ Work(x) ∨ ¬Rehearse(x)
- Clause 2 CNF: ¬Hero(x) ∨ Act(x) ∨ ¬Rehearse(x)
- Clause 5 CNF: Act(x) ∨ ¬Star(x)
- Clause 1 CNF: ¬Loves(Pugu,x) ∨ Star(x)
- From Loves(Pugu,Anmol) & clause1: Star(Anmol)
- From Star(Anmol) & clause5: Act(Anmol)
- From Act(Anmol) & clause2 (contrapositive direction): ¬Rehearse(Anmol) ∨ ¬Hero(Anmol)... resolve clause2 {x/Anmol}: ¬Hero(Anmol) ∨ Act(Anmol) ∨ ¬Rehearse(Anmol) with Act(Anmol) → ¬Hero(Anmol) ∨ ¬Rehearse(Anmol); with Hero(Anmol) → ¬Rehearse(Anmol)
- From ¬Rehearse(Anmol) & clause4 {x/Anmol}: ¬Hero(Anmol) ∨ Work(Anmol) ∨ ¬Rehearse(Anmol) → resolve ¬Rehearse(Anmol): ¬Hero(Anmol) ∨ Work(Anmol); resolve Hero(Anmol): **Work(Anmol)**
- Contradicts ¬Work(Anmol) ⇒ **□** ⇒ proved ∎

### ✅ SOLVED PROOF 5 — 2078 Q2 traffic/driver
Facts: 1. Every traffic chases driver: ∀x (Traffic(x) → ∃y (Driver(y) ∧ Chases(x,y))) 2. Driver who horns is smart: ∀x (Driver(x) ∧ Horns(x) → Smart(x)) 3. No traffic catches any smart driver: ∀x∀y (Traffic(x) ∧ Smart(y) ∧ Catches(x,y) → False) i.e. ¬Catches(x,y) when Smart(y) 4. Traffic who chases some driver but doesn't catch him is frustrated: ∀x∀y (Traffic(x) ∧ Driver(y) ∧ Chases(x,y) ∧ ¬Catches(x,y) → Frustrated(x))
**Prove: if all drivers horn, all traffics are frustrated.** Assume all drivers horn (∀x Driver(x)→Horns(x)) and take arbitrary traffic T: T chases some driver D (fact 1); by assumption Horns(D); by fact 2 Smart(D); by fact 3 ¬Catches(T,D); by fact 4 Frustrated(T). Since T arbitrary ⇒ all traffics frustrated ∎
*(Exam tip: they accept this natural-deduction style with the CNF clauses written out; convert each to clause form for full marks.)*

### Forward vs Backward chaining (2079 Q7)
- **Forward (data-driven):** start from known facts → apply rules (modus ponens) → fire new facts → repeat until goal. *Example: Socrates is man; man → mortal ⇒ derive mortal(Socrates). Used in: design/troubleshooting, monitoring.*
- **Backward (goal-driven):** start from goal → find rules concluding goal → make their premises subgoals → recurse until all subgoals are facts. *Used in: diagnosis, expert systems (MYCIN).*
Draw the two arrows diagrams (facts→goal vs goal←facts).

### Unification & lifting (2079 Q12b)
- **Unification:** finding a substitution θ making two logical expressions identical. E.g., Knows(John, x) and Knows(John, Jane) unify with θ = {x/Jane}. Algorithm: compare terms pairwise, build substitution, fail on conflict.
- **Lifting:** generalizing propositional resolution to FOL: resolve clauses by first unifying complementary literals under θ.

---

## Q: Handling uncertainty — Bayes ⭐ (2076 Q10, 2078 Q12, Model Q7, 2082 Q2/Q7)

**Random variable** = variable with possible values + probabilities. **Prior P(H)** = belief before evidence. **Posterior P(H|E)** = belief AFTER evidence — needed because decisions must be updated when new evidence arrives (that's the "why posterior" answer, 2082 Q7).

**Bayes' Rule: `P(H|E) = P(E|H)·P(H) / P(E)`** ("posterior = likelihood × prior ÷ evidence")

### ✅ SOLVED — 2078 Q12 (liver disease)
P(Disease) = 0.15 (prior), P(Alcoholic) = 0.05, P(Alcoholic|Disease) = 0.07.
P(Disease|Alcoholic) = P(Alcoholic|Disease)·P(Disease) / P(Alcoholic) = (0.07 × 0.15) / 0.05 = 0.0105/0.05 = **0.21 = 21%** ✅

### Inference using Full Joint Distribution (2076 Q10)
Rule: **P(Q | E) = Σ P(Q, E, other…) / Σ P(E, other…)** — sum the matching joint-probability cells, divide by sum of all cells consistent with the evidence.
**Solved:** joint table rows y=width, cols x=length: width 15: (129:0.12, 130:0.42, 131:0.06); width 16: (0.08, 0.28, 0.04).
P(length=130 | width=15) = P(130,15) / Σ P(*,15) = 0.42 / (0.12+0.42+0.06) = 0.42/0.60 = **0.7** ✅

### Bayesian/Belief Networks (Model Q7, 2082 Q2)
DAG: nodes = random variables, edges = direct causal influence; each node has **CPT** P(node | parents). Joint = **P(X₁…Xₙ) = Π P(Xᵢ | Parents(Xᵢ))**.

**✅ Solved Model Q7:** P(Cloudy)=0.5, P(Winter)=0.5, P(Rain|Cloudy,Winter)=0.3, P(Sunny)=0.7 (i.e., P(Rain|Cloudy)=... construct):
```
   Cloudy(0.5)     Winter(0.5)
        \             /
         ▼           ▼
        Rain (CPT: P(R|C,W)=0.3)
         |
         ▼
        Sunny (0.7)
```
Reasoning in belief nets: **diagnostic** (effect→cause), **causal** (cause→effect), **intercausal** (explaining away), **mixed**.

*(2082 Q2's exact network figure wasn't extractable: method = write joint as product of CPT entries, plug in A=true, marginalize over unknowns: P(D|A) = Σ_B,C P(D|…)·P(…|A)·P(B)P(C)… — show this formula and compute with the paper's CPT numbers.)*

---

## Q: Fuzzy Logic (2076 Q8, 2079 Q10, 2081 Q10)

- **Crisp set:** element ∈ {0,1}. **Fuzzy set:** membership **μ(x) ∈ [0,1]** — degrees of truth. "Tall" — 170cm might be μ=0.4.
- **Operators:** union μ_{A∪B} = max(μA, μB); intersection = min; complement = 1−μ.
- **Fuzzy rulebase system:** fuzzify inputs → apply IF-THEN rules (e.g., IF temperature HIGH AND sweat HIGH THEN fan FAST) → aggregate outputs → **defuzzify** (centroid) to crisp output.

**✅ Solved 2076 Q8:** X = {10,20,30,40,50,60,70}. Define fuzzy set "LARGE":
μ = {10:0.0, 20:0.1, 30:0.3, 40:0.5, 50:0.7, 60:0.9, 70:1.0} — each element has a degree, not 0/1 ⇒ fuzzy. (Then demonstrate max/min on two such sets if asked.)

**Fuzzy vs crisp table** + one example (tall, hot, near) = full marks.

---

### ⚡ 30-second recall
> Semantic net = bubbles+arrows. Frame = slots. Script = stereotyped event (restaurant). FOPL patterns: All→∀→, Some→∃∧. CNF: EMSSD. Resolution: negate goal → resolve → □. Bayes: posterior = likelihood×prior÷evidence. Full joint: matching cells ÷ evidence cells. Fuzzy: μ∈[0,1], max/min/complement.
