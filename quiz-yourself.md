# 🧪 Quiz Yourself — 50 Questions (cover the answers below!)

*Rules: answer aloud or on paper, 20-30 seconds each. Score yourself: 40+ = exam ready, 30-40 = re-read session notes, <30 = re-read zero-to-hero. Do this quiz twice today (spaced repetition).*

---

## PART 1 — SEARCH (Q1-15)

1. What 4 things define a well-formed problem?
2. What is the frontier?
3. Complete sentence: "Every search algorithm = a ______ + a ______ for picking from it."
4. Name the 4 evaluation criteria (mnemonic COTS).
5. Greedy best-first picks the frontier node with the lowest ___?
6. A* picks the frontier node with the lowest ___?
7. UCS picks by ___?
8. Write the A* formula with the memory words for g and h.
9. What is an admissible heuristic?
10. Why is A* optimal only with admissibility?
11. Name the 3 states where hill climbing gets stuck.
12. Name the 2 fixes for hill climbing's local max problem.
13. Simulated annealing's probability formula?
14. Which search combines DFS memory with BFS completeness? What's the nickname?
15. Why does greedy fail (incomplete) — one sentence?

## PART 2 — LOGIC (Q16-27)

16. Convert: "All heroes are brave."
17. Convert: "Some students are intelligent."
18. Convert: "No traffic catches smart drivers."
19. Why does "some" use ∧ but "all" uses →?
20. Name the 5 CNF steps (EMSSD).
21. What is a Skolem constant? When do you use a Skolem FUNCTION instead?
22. What do you do to the goal in a resolution proof, and why?
23. What does the empty clause □ mean?
24. Define unification (one line) and lifting (one line).
25. Forward chaining direction vs backward — and one use case each?
26. Bayes rule formula?
27. P(H)=0.1, P(E|H)=0.9, P(E)=0.3 → P(H|E) = ?

## PART 3 — ANN/GA/ML (Q28-40)

28. Write the neuron math model + the 4 biological mappings.
29. What does an activation function do? Why is sigmoid special for learning?
30. Hebb rule formula?
31. Final weights of the Hebb net for OR?
32. Perceptron update rule?
33. Why does perceptron fail XOR (one phrase)?
34. Backprop's 4 passes in order?
35. Output-layer delta formula (sigmoid)?
36. What does "training" a network mean (one line)?
37. GA's 3 operators in order?
38. What is the fitness function?
39. One-point crossover on C1=11110000, C2=00001111 after 4 bits → children?
40. Passive vs active reinforcement learning — one line each?

## PART 4 — AGENTS & THEORY (Q41-50)

41. PEAS = ? Spell out all 4 for a self-driving taxi.
42. Name the 5 agent types (mnemonic?).
43. Model-based agent's advantage over simple reflex?
44. Utility-based agent's advantage over goal-based?
45. Name 5 environment type pairs.
46. Classify: chess (fully obs? deterministic? static? discrete? agents?)
47. Turing test — setup + the 4 capabilities needed to pass.
48. Expert system components (mnemonic KIUWE = ?) + role of inference engine?
49. NLP's 5 steps in order (mnemonic?) + what pragmatic analysis catches that semantic misses?
50. Machine vision system components in order + one robotic sensor example each for proprioceptive/exteroceptive.

---
---

# ✅ ANSWER KEY (no peeking before attempting!)

**1.** Initial state, actions/successor function, goal test, path cost
**2.** Waiting list of discovered-but-not-yet-expanded nodes
**3.** frontier + rule
**4.** Completeness, Optimality, Time, Space
**5.** h(n)
**6.** f(n) = g(n) + h(n)
**7.** g(n)
**8.** f = g + h; g = Gone (cost so far), h = Hope (estimated to go)
**9.** h(n) never overestimates the true cost to goal: h(n) ≤ h*(n)
**10.** With an overestimating h, A* may reach the goal via a non-cheapest path thinking it's best; admissible h guarantees the cheapest path is expanded first
**11.** Local maximum, plateau, ridge
**12.** Random-restart; simulated annealing
**13.** P = e^(ΔE/T), T = temperature (cools over time)
**14.** Iterative deepening search; "BFS in DFS clothing"
**15.** It ignores path cost g(n), so it can chase an apparently-closer-but-actually-worse path into dead ends/loops
**16.** ∀x (Hero(x) → Brave(x))
**17.** ∃x (Student(x) ∧ Intelligent(x))
**18.** ∀x∀y (Traffic(x) ∧ Smart(y) → ¬Catches(x,y))
**19.** "All" is conditional (IF dog THEN animal — doesn't assert everything is a dog); "some" asserts one thing is BOTH (∧)
**20.** Eliminate →/↔, Move ¬ inward, Standardize variables, Skolemize, Distribute/drop ∀
**21.** Newly invented constant replacing an existential variable (names "the thing that must exist"); FUNCTION when the ∃ sits inside a ∀ (depends on that variable)
**22.** Negate it and add as a clause — proof by refutation: contradiction with the negation proves the original
**23.** Contradiction — the negated goal is false, so the goal is PROVED
**24.** Unification = finding substitution θ making two expressions identical; Lifting = applying propositional resolution to FOL using unification
**25.** Forward: facts→goal (data-driven; monitoring/design). Backward: goal→facts (goal-driven; diagnosis/ES)
**26.** P(H|E) = P(E|H)·P(H)/P(E)
**27.** 0.9×0.1/0.3 = 0.09/0.3 = 0.3
**28.** y = f(Σwᵢxᵢ + b); dendrite→inputs, synapse→weights, soma→summer+bias, axon→output
**29.** Introduces non-linearity, decides firing strength; sigmoid is smooth/differentiable → enables gradient descent (backprop), squashes to (0,1)
**30.** Δw = x·t
**31.** w₁=2, w₂=2, b=2
**32.** w_new = w + η(t−y)x; b_new = b + η(t−y)
**33.** Not linearly separable — no single line can split XOR's classes
**34.** Forward pass → error computation → backward pass (deltas) → weight update (repeat)
**35.** δₒ = (t−o)·o·(1−o)
**36.** Adjusting weights to minimize the error between outputs and targets
**37.** Selection → crossover → mutation
**38.** Function scoring each chromosome's quality; drives selection probability
**39.** Child1 = 1111|1111 = 11111111; Child2 = 0000|0000 = 00000000
**40.** Passive = evaluate a given fixed policy; active = choose own actions + explore to find optimal policy
**41.** Performance, Environment, Actuators, Sensors; P: safe/fast/legal/profit · E: roads/traffic/pedestrians/weather · A: steering/accelerator/brake/horn · S: cameras/LiDAR/GPS/speedometer
**42.** Simple reflex, Model-based, Goal-based, Utility-based, Learning ("Some Monkeys Grab Unripe Lemons")
**43.** Keeps internal state + world model → handles partial observability
**44.** Compares degree of desirability → handles trade-offs and conflicting goals (speed vs safety), not just reach/not-reach
**45.** Fully/partially observable · deterministic/stochastic · static/dynamic · discrete/continuous · single/multi-agent
**46.** Fully observable ✓ deterministic ✓ static ✓ discrete ✓ two-agent (competitive)
**47.** Interrogator chats blind with human + machine; can't reliably tell = intelligent. Needs: NLP, knowledge representation, automated reasoning, machine learning
**48.** Knowledge base, Inference engine, User interface, Working memory, Explanation; inference engine = the brain that matches facts to rules and fires them (forward/backward chaining)
**49.** Lexical, Syntactic, Semantic, Discourse, Pragmatic ("Lazy Students See Pragmatic Discourse"); pragmatic catches speaker INTENT in context — "Can you pass the salt?" is a request, not an ability question
**50.** Lighting → camera/sensor → frame grabber/processor → feature extraction → decision unit; proprioceptive: joint encoder/gyro; exteroceptive: camera/LiDAR/sonar/touch
