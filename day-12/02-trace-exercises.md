# Day 12 — AI Trace Exercises & Problem-Solving (Exam-Style)

## Set 1: Agent & AI Definition Trace

### Problem 1 — Agent vs Environment
A self-driving car uses cameras (sensors) to perceive the road, then turns the steering wheel (actuator) to stay in lane.
a) What is the agent? b) What is the environment? c) What are the sensors? d) What are the actuators?

**Solution:**
a) The self-driving car system (agent)
b) The road, traffic, weather (environment)
c) Cameras, LIDAR, radar (sensors)
d) Steering wheel, brakes, accelerator (actuators)

---

### Problem 2 — Agent Type Classification
Identify the agent type:
a) A chess AI that evaluates future moves → _________
b) A thermostat that turns heat on/off at 18°C → _________
c) A robot vacuum that maps rooms and remembers locations → _________
d) A stock trading bot that maximizes portfolio value → _________

**Solution:**
a) Goal-based (or learning)  b) Simple reflex (current percept only)  c) Model-based (internal map)  d) Utility-based (maximizes utility)

---

## Set 2: Search Algorithm Trace

### Problem 3 — Informed vs Uninformed
Classify: a) BFS b) A* c) DFS d) Greedy Best-First e) UCS f) Iterative Deepening

**Solution:**
a) Uninformed  b) **Informed** (heuristic)  c) Uninformed  d) **Informed** (heuristic h(n))  e) Uninformed (no heuristic, only actual cost)  f) Uninformed

---

### Problem 4 — A* f(n) Calculation
Start → Node A (g=5, h=8) → Goal. Start → Node B (g=3, h=12) → Goal. Which node does A* expand first?

**Solution:** f(A)=5+8=13, f(B)=3+12=15. A* expands **Node A** first (lower f-value).

---

### Problem 5 — Admissible Heuristic
h(A)=10 (true cost=8), h(B)=5 (true cost=6), h(C)=3 (true cost=3). Which are admissible?

**Solution:** h(A)=10 > 8 → **NOT admissible**. h(B)=5 ≤ 6 → **Admissible**. h(C)=3 ≤ 3 → **Admissible**.

---

### Problem 6 — UCS vs Dijkstra
How does UCS explore nodes differently from Dijkstra?

**Solution:** UCS **collects nodes in queue first**, then discovers. Dijkstra **discovers nodes as they come**.

---

## Set 3: Local Search Trace

### Problem 7 — Hill Climbing
Starting from point A to reach global maximum B. Will hill-climbing succeed?

**Solution:** **Not necessarily** — depends on the starting point and neighborhood function. May get stuck at local maxima.

---

### Problem 8 — LSA Statement
Which is TRUE about Local Search Algorithms?
a) For convex optimization  b) Time independent of size  c) **Quality depends on starting point** ✓  d) Always globally optimal

**Solution:** c) — quality heavily depends on starting point and neighborhood function choice

---

## Set 4: Knowledge & Expert Systems

### Problem 9 — Forward vs Backward Chaining
An expert system starts with symptoms (fever, cough) and concludes a disease (flu). What type of chaining?

**Solution:** **Forward chaining** — data-driven: facts → conclusion

---

### Problem 10 — Expert System Components
What are the three main components of an expert system?

**Solution:** 1) **Knowledge Base** (facts + rules), 2) **Inference Engine** (applies rules), 3) **User Interface**

---

## Set 5: Game Playing & CSP

### Problem 11 — Minimax Trace
```
        MAX
        /  \
     MIN    MIN
     / \    /  \
    3   5  2    9
```
Optimal value at root?

**Solution:** MIN chooses min: left=min(3,5)=3, right=min(2,9)=2. MAX chooses max(3,2)=**3**.

---

### Problem 12 — Alpha-Beta Benefit
Which branch can be pruned in the tree above?

**Solution:** In the right subtree, once MIN sees 2 (< 3 from left), MAX would never choose it. The 9 branch is **pruned**.

---

## Set 6: ML & Data Mining

### Problem 13 — Overfitting vs Underfitting
a) 99% train, 55% test → b) 60% both → c) 95% both

**Solution:** a) Overfitting  b) Underfitting  c) Good fit

---

### Problem 14 — Model Development
A team has 10,000 labeled images. How to split?

**Solution:** 70-80% training (7,000-8,000), 10-15% validation, 10-15% test. Larger training set = better performance. No overlap.

---

### Problem 15 — ML Type
Identify: a) Predict house prices from labeled data b) Group customers without labels c) Robot navigating with rewards

**Solution:** a) Supervised (regression)  b) Unsupervised (clustering)  c) Reinforcement learning

---

### Problem 16 — Data Mining Sequence
Order: Model Testing, Deployment, Training, Evaluation

**Solution:** Training → Testing → Evaluation → Deployment

---

### Problem 17 — Association Rule
Bread & butter bought together 80% of the time. Which analytics technique?

**Solution:** **Association rule mining** (market basket analysis)

---

### Problem 18 — Automatic Planning
What technique generates plans with conditionals/loops from logical specs?

**Solution:** **Automatic programming**

---

## Common Exam Traps — AI

| Trap | Explanation |
|------|-------------|
| **Informed = admissible** | Informed search described as **admissible** (uses admissible heuristics) |
| **Local search quality** | Depends on **starting point** and **neighborhood function** |
| **UCS vs Dijkstra** | UCS **collects in queue first**; Dijkstra **discovers as they come** |
| **AI definition** | Tasks requiring **human intelligence**, not physical/simple/lab-only |
| **Agent** | Anything that **perceives** (sensors) and **acts** (effectors) |
| **A\* properties** | Informed, complete, optimal (admissible heuristic), exponential worst-case |
| **Overfitting** | Works on training, **poor on new data** |
| **Model development** | **Large dataset boosts performance** |
| **Data mining order** | Training → Testing → Evaluation → Deployment |
| **Automatic programming** | Plans with conditionals/loops from logical specs |
| **Unsupervised** | No labels — clustering, association |
| **AI components** | Agent + Environment, not data+info or device+network |
