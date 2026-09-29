# 🧠 Memory Mastery Strategy — How to Remember Everything in 5 Hours

*This is the "how to study" manual. Pair it with `ai-exam-pack.md` (the plan) and `solutions/` (the content).*

---

## Part 1: Why your brain will betray you (and how to stop it)

Your brain deletes ~70% of new information within 24 hours (Ebbinghaus forgetting curve). Cramming fails when you **only read**. It works when you **retrieve**. Every technique below is a form of *forced retrieval* — pulling information OUT of your head instead of pushing it in.

**The golden rule of today: For every 10 minutes of input, do 3 minutes of output.**
- Input = reading notes, watching solutions
- Output = writing from memory, saying it aloud, drawing diagrams blank-page

---

## Part 2: The 6 techniques you'll use today

### 1. Active Recall (your main weapon) ⭐
Never re-read a topic passively. Read once → close the file → write/say everything you remember → check → repeat what you missed.
```
Read topic (5 min) → BLANK PAGE recall (3 min) → check gaps (2 min) → next topic
```
One full recall cycle beats five re-reads. This is the single highest-leverage habit in existence for exams.

### 2. Spaced repetition within the day
Don't do Unit 1 fully, then Unit 2, and never return. Instead:
- **H1:** Search → **H2:** Logic → **H3:** ANN → **H4:** KR/Bayes → **H5:** Theory + final sweep
- At the start of every hour, spend **4 minutes** re-calling the *previous* hour's 3 key items aloud. This 4-minute habit doubles retention. (It's spaced repetition compressed into one day.)

### 3. The Feynman Technique (for concepts you keep forgetting)
If a topic won't stick (e.g., Skolemization, backprop), do this:
1. Explain it aloud as if teaching a 12-year-old: *"Skolemization = removing the 'there exists' by giving that mystery thing a name"*
2. Wherever you stumble or use jargon — that's your gap. Re-read ONLY that gap.
3. Re-explain. When you can say it smoothly in under 60 seconds, it's yours.

### 4. Dual coding — every concept gets a picture
Text memories are fragile; image memories are sticky. For EVERY major topic, draw ONE diagram and attach the concept to it:
| Topic | Your mental picture |
|---|---|
| A* | f = g + h → "Gone + Hope" walking toward the goal |
| Resolution | Two clauses crashing; contradictory pair cancels like +1 and −1 |
| ANN neuron | A funnel: inputs (x) × weights (w) → summer (+b) → squashing function → output |
| Expert system | Boxes: KB → Inference engine → User, with Working memory on the side |
| Semantic net | Bubble diagram with "is-a" arrows |
| Belief network | Family tree where parents cause children |
| Minimax | A tree where you alternate MAX (picking biggest) and MIN (picking smallest) layers |
| GA | Chromosomes mating: select parents → crossover swap → mutation flips a bit |

In the exam, you reproduce the drawing first — the words come back attached to the picture.

### 5. Mnemonics (pre-made, memorize these 8)
1. **NLP steps** — "**L**azy **S**tudents **S**ee **P**ragmatic **D**iscourse" → Lexical, Syntactic, Semantic, Pragmatic, Discourse
2. **Agent types** — "**S**ome **M**onkeys **G**rab **U**nripe **L**emons" → Simple reflex, Model, Goal, Utility, Learning
3. **Expert system components** — "**K**nowledge **I**nference **U**ser **W**orking **E**xplanation" (KIUWE)
4. **Uninformed searches** — "**B**ig **D**ogs **D**on't **I**gnore **U**gly **B**ones" → BFS, DFS, DLS, IDS, UCS, Bidirectional
5. **Search comparison** — remember 4 columns: **C**omplete? **O**ptimal? **T**ime **S**pace ("COTS")
6. **CNF conversion** — "**E**liminate **M**inus **S**tandardize **S**kolemize **D**istribute" (EMSSD)
7. **Bayes rule** — "Posterior = Likelihood × Prior ÷ Evidence" → P(H|E) = P(E|H)P(H)/P(E)
8. **A*** — "g = Gone (past cost), h = Hope (future estimate), f = Full picture"

### 6. Blurting (your final exam-simulation)
Last 30–40 min before you stop studying:
1. Take 5 blank sheets — one per unit
2. Timer 5 min per unit: dump EVERYTHING you remember (names, formulas, diagrams, mnemonics)
3. Compare against the exam pack
4. Whatever you missed goes on ONE final "cheat card" — review only that card tomorrow morning / before entering the hall

---

## Part 3: Unit-specific memory hacks

**Search algorithms** — don't memorize 8 separate algorithms; memorize ONE mental machine:
*"A priority queue of frontier nodes + a rule for ordering it."*
- BFS = order by depth (FIFO queue)
- DFS = order by depth (LIFO stack)
- UCS = order by g(n)
- Greedy = order by h(n)
- A* = order by g(n) + h(n)
One template, five algorithms. Hill climbing = A* with amnesia (only remembers current node). Alpha-beta = minimax that stops evaluating branches that can't change the answer ("prune when α ≥ β").

**FOPL/Resolution** — the 6 sentence patterns cover 95% of exam conversions:
| English | FOPL |
|---|---|
| All X are Y | ∀x(X(x) → Y(x)) |
| No X are Y | ∀x(X(x) → ¬Y(x)) |
| Some X are Y | ∃x(X(x) ∧ Y(x)) |
| X of all Y is Z | ∀x∀y(Y(y) → X(x,y) → ... pattern with two variables) |
| Proper nouns | constants: laxmi, rojina |
| "There exists..." | ∃x(...) — becomes Skolem constant |

Resolution = negate the conclusion → CNF everything → keep resolving pairs with complementary literals → empty clause = contradiction = conclusion proven. Write "thus contradiction, hence proved" at the end for full marks.

**ANN** — memorize 3 formulas only:
1. Neuron: `y = f(Σwᵢxᵢ + b)`
2. Hebb: `Δw = x·t` (weight grows when input and target fire together)
3. Perceptron: `w_new = w + η(t−y)x` — the (t−y) term is "error, push weights toward the target"

**Bayes numericals** — one recipe: identify H, identify E → write P(E|H), P(H), P(E) → plug into Bayes formula → compute. The exam always gives you 2 of the 3 needed values; the third is usually a complement or a sum.

**Theory units (ES, NLP, vision, robotics)** — these are pure mnemonics + diagram marks. Learn the mnemonic, draw the diagram, expand each item into one sentence. Never write a one-line answer for a 5-marker; the skeleton (definition → diagram → points → example) guarantees the full 5.

---

## Part 4: The night-before / morning-of protocol

**Night:**
- Study H1–H4, do the blur drill as your last activity (H5 can be tomorrow morning if you're out of time — sleep > extra hour)
- Sleep ≥ 5.5–6 hrs. Memory consolidation happens IN SLEEP — an all-nighter literally deletes what you crammed
- Put your cheat card next to your pillow/phone

**Morning (60 min before exam):**
- 20 min: read the cheat card + the 8 mnemonics
- 20 min: re-draw the 4 most important diagrams from memory (search tree, neuron, expert system, resolution flow)
- 20 min: skim the "Predicted high-probability questions" list in `ai-exam-pack.md` — mentally outline your answer for each

**In the hall:**
- First 3 min: on rough paper, dump the 8 mnemonics + Bayes formula + A* formula BEFORE solving anything (prevents "it was on the tip of my tongue" tragedy)
- Do Section A first while your mind is freshest (they're 10 marks each and need traces)
- For every algorithm question: numbered steps FIRST, then the trace. Traces earn the majority of marks.
- Never leave blanks — write the definition + diagram at minimum; partial marks are real

---

## Part 5: If you're behind schedule (triage rules)

Priority order — cut from the BOTTOM, never the top:
1. ⭐ Search traces (7/7 papers) — non-negotiable
2. ⭐ FOPL → resolution (7/7) — non-negotiable
3. ⭐ ANN math model + learning rules (6/7)
4. Bayes numerical + GA operators (5/7)
5. NLP steps + expert systems + agents/PEAS (4-5/7, pure mnemonics, fast to learn)
6. Semantic nets/frames/scripts diagrams (fast, visual)
7. Fuzzy, UCS, machine vision/robotics, Turing test notes — cut first if desperate

Even triaged to items 1–5 only, you can still target 40+/60.
