# Unit 1 & 2 — Introduction + Intelligent Agents

---

## Q: What is intelligence? Describe the foundation of AI. (2081 Q4)

**Intelligence** is the ability to learn from experience, reason, solve problems, perceive, understand language, and adapt to new situations.

**Foundations of AI** (one line each — remember ~6 of these):
| Field | Contribution to AI |
|---|---|
| **Philosophy** | Can machines think? Logic, reasoning, mind-body question (Aristotle → Descartes) |
| **Mathematics** | Formal logic, computability, probability, algorithms (Turing, Gödel) |
| **Economics** | Decision theory, utility maximization, game theory — acting rationally under scarcity |
| **Neuroscience** | How neurons work → artificial neural networks |
| **Psychology** | Behaviorism, cognitive modeling — "thinking humanly" |
| **Computer Engineering** | The hardware/software substrate that makes AI feasible |
| **Linguistics** | Natural language understanding, knowledge representation |
| **Sociology** | Multi-agent systems, social behavior of agents |
| **Control Theory** | Feedback, homeostatic systems — agents that act on environment to reach desired state |

---

## Q: What is AI? How can you define AI from the perspective of thought process? (2076 Q4)

AI = building systems that exhibit intelligent behavior.

**4 perspectives** (the 2×2 grid — draw it!):

| | **Human** | **Rational** |
|---|---|---|
| **Thinking** | Cognitive modeling (think humanly) | Laws of thought / logic (think rationally) |
| **Acting** | Turing Test approach (act humanly) | Rational agent approach (act rationally) ✅ modern AI |

- **Acting humanly:** Turing Test — interrogator can't tell machine from human. Needs: NLP, knowledge representation, automated reasoning, machine learning (+ vision & robotics for total test).
- **Thinking humanly:** cognitive science — model how humans actually think (introspection, experiments).
- **Thinking rationally:** syllogisms/formal logic — correct inference from premises.
- **Acting rationally:** rational agent — acts to achieve best (expected) outcome. Preferred textbook definition because it's measurable and engineering-friendly.

---

## Q: What is Turing test? How can it measure machine intelligence? / properties to pass (2078 Q4, 2080 Q4, Model Q4, 2079 Q12c)

**Turing Test (1950, Alan Turing):** A human interrogator chats via text with a hidden human and a hidden machine. If the interrogator cannot reliably tell which is the machine, the machine is intelligent.

```
[Interrogator] --text--> [Hidden Human] & [Hidden Machine]
                 "Which one is human?"
```

**Properties needed to pass:**
1. **Natural Language Processing** — communicate
2. **Knowledge Representation** — store what it knows
3. **Automated Reasoning** — answer questions, draw conclusions
4. **Machine Learning** — adapt to new patterns
5. (+ **Computer Vision** & **Robotics** for the *Total* Turing Test, which includes objects and movement)

**Why it measures intelligence:** it tests observable intelligent *behavior* rather than internal mechanisms — behavior is the only thing we can compare against humans.

---

## Q: How do you define rational? Can AI choose between right and wrong? Justify. (2082 Q4)

**Rationality:** doing the *right thing* — for each possible percept sequence, a rational agent selects the action that **maximizes its expected performance measure**, given (1) the percept sequence to date and (2) its built-in knowledge of the environment.

**Can AI choose right from wrong?**
- AI is rational ≠ AI is moral. Rationality = maximizing a **utility function**, and the morality lives *inside* that function, which humans design.
- If the utility function encodes ethics (e.g., penalize harm), the AI "chooses" ethically — but only within the values we gave it.
- AI has no consciousness/intention; it cannot *justify* choices morally. So: **AI can choose between right and wrong only as far as its programmer's values allow.** Example: a self-driving car brakes for pedestrians only if the designers made avoiding pedestrians a goal.

---

## Q: How do philosophy, sociology and economics influence AI? (2078 Q10)

- **Philosophy:** gave the *idea* that reasoning is a form of computation (Aristotle's syllogisms, Descartes' mind-body dualism, Hobbes' "reasoning is reckoning"). Asked the founding question "can a machine think?"
- **Sociology:** multi-agent systems, how intelligent agents interact/coordinate in societies, social choice, norms and cooperation — foundation for distributed AI.
- **Economics:** decision theory — maximize expected utility under uncertainty; game theory for adversarial settings (→ minimax); operations research for resource allocation. Directly shaped rational-agent design.

---

## Q: Agent — structure & properties. Properties of intelligent agent? How simple reflex agents work? (2080 Q5)

**Agent:** anything that **perceives** its environment through **sensors** and **acts** on it through **actuators**.

**Structure:**
```
Environment ──percepts──> [ Sensors → Agent Program (AI) → Actuators ] ──actions──> Environment
```
`agent = architecture + program`

**Properties of an intelligent agent:**
1. **Autonomy** — operates without direct human intervention
2. **Reactivity** — perceives and responds timely to changes
3. **Pro-activeness** — goal-directed, takes initiative
4. **Social ability** — interacts with other agents/humans
5. **Adaptivity/Learning** — improves with experience
6. **Rationality** — acts to maximize expected performance

**Simple reflex agent:** chooses action based ONLY on the current percept, using **condition–action rules** (if-then). Ignores percept history.
```
percept → [rule: if dirty then suck] → action
```
**Example:** vacuum cleaner — `if [square] dirty → SUCK else → MOVE RIGHT`. Works only when environment is **fully observable** and each percept is enough to decide.

---

## Q: Differentiate model-based vs simple reflex agent (Model Q5) / utility-based vs model-based (2079 Q5)

| Feature | Simple Reflex | Model-Based | Utility-Based |
|---|---|---|---|
| Uses history? | ❌ current percept only | ✅ internal state | ✅ internal state |
| Model of world? | ❌ | ✅ "how the world evolves" | ✅ |
| Decision basis | condition–action rules | rules + world model | **degree of happiness (utility)** |
| Handles partial observability? | ❌ | ✅ | ✅ |
| Best outcome vs just any goal | any matching rule | predicted outcomes | **best** outcome |
| Example | vacuum cleaner | taxi that remembers cars it can't see | taxi choosing fastest *and* safest route |

**Utility-based > goal-based:** a goal only says "reach state X"; utility says *how desirable* each state is — it handles trade-offs (speed vs safety vs cost) and conflicting goals.

---

## Q: What do you mean by PEAS description? Give example (2082 Q5) / design PEAS for: COVID-19 predictor, vaccine recommender (2080 Q9), internet shopping assistant, English tutor (Model Q12) / taxi (2078 Q5)

**PEAS = Performance measure, Environment, Actuators, Sensors** — the task environment specification of an agent.

**Self-driving taxi (classic):**
- **P:** safe, fast, legal, comfortable, max profit
- **E:** roads, traffic, pedestrians, weather, customers
- **A:** steering, accelerator, brake, horn, display
- **S:** cameras, sonar/LiDAR, GPS, speedometer, keyboard/mic

**COVID-19 prediction system:**
- **P:** prediction accuracy, early detection rate, low false negatives
- **E:** patient data, test results, hospital records, symptoms database
- **A:** risk report, alert to health workers, diagnosis recommendation
- **S:** symptom inputs, lab test feeds (PCR), X-ray/CT images, temperature sensors

**Vaccine recommender system:**
- **P:** recommendation accuracy, patient health improvement, minimal side effects
- **E:** patient medical history, age, allergies, vaccine inventory, epidemic data
- **A:** vaccine suggestion, dosage plan, notification
- **S:** patient records, health questionnaire, allergy database

**Internet shopping assistant:**
- **P:** relevant suggestions, best price found, user satisfaction, purchase success rate
- **E:** e-commerce sites, product catalogs, prices, reviews, user profile
- **A:** product display, comparison table, cart actions
- **S:** user queries, browsing history, clickstream, wishlist

**English language tutor:**
- **P:** student score improvement, error correction rate, engagement
- **E:** student, exercises, grammar corpus, test set
- **A:** lessons, corrections, feedback, hints
- **S:** typed/spoken answers, test scores, keystrokes

---

## Q: Types of environments where an agent can work (2076 Q5) / which environment resembles these agents (2081 Q12) / static & dynamic example, when to prefer rule-based systems (2082 Q12)

**Environment types (pairs):**
| Type | Meaning | Example |
|---|---|---|
| **Fully observable** | sensors see complete state | chess board |
| **Partially / Semi-observable** | only parts visible | taxi (other drivers' minds hidden) |
| **Deterministic** | next state fully determined by current state + action | chess |
| **Stochastic** | outcomes have uncertainty | dice games, real traffic |
| **Static** | environment doesn't change while agent thinks | crossword puzzle |
| **Dynamic** | keeps changing → agent must keep acting | autonomous driving, stock trading |
| **Discrete** | finite distinct states/actions | chess moves |
| **Continuous** | values change continuously | robot arm angles, driving speed |
| **Single-agent** | one agent alone | crossword solver |
| **Multi-agent** | others present — competitive or cooperative | chess (competitive), robots football (cooperative+competitive) |

**2081 Q12 answers:**
1. **Mission game, fixed 6 states, two players** → *discrete, deterministic, static, fully observable, multi-agent (competitive)*
2. **Tesla Driverless Robovan, changing road conditions** → *continuous, stochastic, dynamic, partially observable, single-agent*
3. **Game result predictor, current prediction independent of previous state** → *discrete, stochastic, static (episodic), single-agent*

**Static example:** crossword solving. **Dynamic example:** self-driving in traffic.

**When to prefer rule-based systems:** when the domain has **well-understood, stable, explicitly-stated rules** (legal/tax rules, medical protocols, equipment fault diagnosis), full knowledge is available from human experts, explainability of each decision is required, and learning data is scarce. They're transparent, easy to verify and update — unlike learned models.

---

## Q: List any one example... rule based systems preference (2082 Q12) — see above. 
## Q: Rational agent? (2079 Q5) — see rationality answer + comparison table above.

---

### ⚡ 30-second recall for this unit
> Agent = sensors + program + actuators. PEAS = task spec. 5 agent types (Some Monkeys Grab Unripe Lemons). 10 environment pairs. Rational = max expected utility given percepts + knowledge.
