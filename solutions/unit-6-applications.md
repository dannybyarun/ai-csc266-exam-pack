# Unit 6 — Applications: Expert Systems, NLP, Machine Vision, Robotics

## Q: What is expert system? Components (2080 Q10, Model Q8, 2078 Q8)

**Expert system:** a program that emulates the **decision-making of a human expert** in a narrow domain, using a knowledge base + inference rules. Examples: MYCIN (medical diagnosis), DENDRAL (chemical structures), XCON (computer configuration).

**Components (draw the boxes — KIUWE):**
```
                 ┌──────────────────────┐
 User ──────>    │  User Interface      │
                 └─────────┬────────────┘
                 ┌─────────▼────────────┐
                 │  Inference Engine    │◄────┐
                 └───┬──────────────┬───┘     │ rules fire
                 ┌───▼─────┐  ┌─────▼──────┐  │
                 │ Working │  │ Knowledge  │──┘
                 │ Memory  │  │ Base       │
                 └─────────┘  │ (facts+    │
  Expert ──knowledge──> [KB]  │  rules)    │
  Engineer ──updates──> [KB]  └────────────┘
                 ┌──────────────────────┐
                 │ Explanation Module   │ "WHY did you ask that?"
                 └──────────────────────┘
```
1. **Knowledge Base:** domain facts + IF-THEN rules (from human expert)
2. **Inference Engine:** applies rules to facts to derive conclusions — **forward chaining** (data-driven) or **backward chaining** (goal-driven). *Role (2078 Q8): it is the "brain" — selects and fires rules, matches facts against rule conditions, controls the reasoning process.*
3. **Working Memory (blackboard):** holds current facts of the ongoing case
4. **User Interface:** converses with user, takes inputs, shows conclusions
5. **Explanation Module:** justifies reasoning ("why asked / how concluded") — builds user trust

## Q: Phases of expert system development (2079 Q3, 2082 Q10)

1. **Problem identification / selection:** choose suitable narrow domain (clear, well-bounded, expert available)
2. **Knowledge acquisition:** extract knowledge from human expert via knowledge engineer — interviews, rules, cases
3. **Knowledge representation / design:** choose structure (rules, frames), design inference strategy
4. **Implementation / prototype:** build the knowledge base + inference engine
5. **Testing & evaluation:** compare with expert's decisions on test cases; measure accuracy
6. **Deployment & maintenance:** field use, monitor, update knowledge as domain evolves
(Mnemonic: **I**dentify, **A**cquire, **R**epresent, **I**mplement, **T**est, **D**eploy → "I AIR the TD")

## Q: NLP — why, what, and the 5 steps (Model Q6, 2079 Q4, 2076 Q12, 2078 Q9, 2080 Q11, 2082 Q11)

**NLU vs NLG:** **Natural Language Understanding** = machine extracts meaning from human language (ambiguity resolution); **Natural Language Generation** = machine produces fluent language from internal representation (text planning → sentence planning → realization).

**Why machines need NL (2082 Q11):** humans communicate in natural language — for machines to be useful interfaces (assistants, translation, search, summarization), they must parse and produce it. **Challenges:** ambiguity (lexical "bank", syntactic "old men and women", semantic "Flying planes can be dangerous"), context dependence, synonyms, slang/idioms, different grammar rules across languages, sarcasm.

**The 5 steps (Lazy Students See Pragmatic Discourse):**
1. **Lexical analysis:** split text into tokens (segmentation), analyze word forms (morphological analysis: "running" → run + -ing)
2. **Syntactic analysis (parsing):** check grammar; build parse tree. Rejects ill-formed sentences: "the girl goes to the school" ✅ vs "girl the go school" ❌
3. **Semantic analysis:** extract literal meaning; map to meaning representation. Rejects: "colorless green ideas sleep furiously" (grammatical but meaningless)
4. **Discourse integration:** meaning depends on preceding sentences — resolve references ("Ram went home. **He** was tired." → he = Ram)
5. **Pragmatic analysis:** interpret intended meaning with real-world context. **Why needed (2080 Q11):** same words mean different things by context/speaker intent. "Can you pass the salt?" — semantic: asking about ability; pragmatic: a REQUEST. Done via: speech act theory, context models, world knowledge, anaphora resolution.

**Machine translation:** converting text from one natural language to another automatically (rule-based → statistical → neural, e.g., translating Nepali↔English).

## Q: Machine vision (2076 Q11, 2081 Q9)

**Machine vision:** computer automatically gains understanding from digital images/video — capture → process → analyze → decide.

**Components of machine vision system:**
1. **Lighting/illumination** — makes features visible
2. **Camera/sensor** — captures image
3. **Frame grabber/image processor** — digitizes & processes (filtering, edge detection)
4. **Feature extraction / analysis software** — patterns, measurements
5. **Decision/output unit** — actuator/display/verdict (pass/fail)

**Applications:** industrial inspection (defect detection), object recognition, face recognition, OCR, medical imaging, autonomous vehicle perception.

## Q: Robotics (2081 Q9, 2076 Q11)

**Robot:** programmable machine that senses, plans, and acts in the physical world. **Robotics:** engineering field designing robots.

**Robot hardware:**
- **Sensors (perception):**
  - *Proprioceptive* (robot's own state): joint angle encoders, gyroscope, accelerometer, battery level
  - *Exteroceptive* (world state): cameras, LiDAR, sonar/ultrasonic, infrared, tactile/touch sensors, GPS, microphones
- **Effectors/actuators (action):** motors, hydraulic/pneumatic actuators, grippers, wheels/tracks/legs, speakers

**Robotic perception:** converting raw sensor data into internal world model — sensor fusion, localization (where am I), mapping, object detection. **Machine vision is the robot's primary exteroceptive sense (2081 Q9):** cameras + vision algorithms let robots recognize obstacles, navigate, grasp objects, identify targets — e.g., vision supplies the object position and distance that drive the gripper's motion plan.

---

### ⚡ 30-second recall
> Expert system = KB + Inference engine + UI + Working memory + Explanation (KIUWE). Development: Identify→Acquire→Represent→Implement→Test→Deploy. NLP: Lexical→Syntactic→Semantic→Discourse→Pragmatic (Lazy Students See Pragmatic Discourse). Vision: light→camera→processor→features→decision. Robot: sensors (own vs world) + effectors.
