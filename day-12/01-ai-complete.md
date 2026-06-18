# Day 12 — Fundamentals of AI Complete Theory (6 Items)

## LO1: Intelligent Agents & AI Systems

### 1.1 What is AI?
- **AI**: development of machines that can perform tasks that typically **require human intelligence**
- NOT: physical tasks only, simple/repetitive tasks only, or controlled-laboratory-only tasks

### 1.2 AI System Components
- AI system composed of: **Agent** and **Environment**
- **Agent**: anything that **perceives** environment through **sensors** and **acts** through **effectors/actuators**
- **Environment**: external context where agent operates

### 1.3 Agent Types
| Type | Description | Example |
|------|-------------|---------|
| **Simple Reflex** | Responds to current percept only | Thermostat |
| **Model-Based** | Maintains internal state/model | Robot with memory |
| **Goal-Based** | Acts to achieve goals | Route planner |
| **Utility-Based** | Maximizes utility function | Stock trader |
| **Learning** | Improves over time | Game AI |

### 1.4 PEAS
- **P**erformance, **E**nvironment, **A**ctuators, **S**ensors

---

## LO2: Search Strategies

### 2.1 Uninformed vs Informed
| Aspect | Uninformed (Blind) | Informed (Heuristic) |
|--------|-------------------|---------------------|
| Knowledge | No problem-specific info | Uses heuristic h(n) |
| Example algorithms | BFS, DFS, UCS, Iterative Deepening | A*, Greedy Best-First |
| Optimality | Varies | With admissible heuristic |

### 2.2 A* Search (Exam Priority!)
- f(n) = **g(n) + h(n)**
  - g(n) = cost from start to n
  - h(n) = heuristic estimate from n to goal
- **Informed** search algorithm
- **Complete** — finds solution if one exists
- **Optimal** — guarantees optimality with **admissible** heuristic
- **Exponential time** complexity in worst case

### 2.3 Heuristic Properties
- **Admissible**: never overestimates (h(n) ≤ true cost)
- **Consistent**: h(n) ≤ c(n,n') + h(n')
- Informed search algorithms described as **admissible**

### 2.4 Uniform Cost Search vs Dijkstra
| UCS | Dijkstra |
|-----|----------|
| **Collects nodes in Queue first, then discovers** | Discovers nodes as they come |
| Single goal detection | All shortest paths from source |

### 2.5 Local Search Algorithms
- For optimization problems
- **Quality depends heavily on starting point and neighborhood function**
- NOT guaranteed globally optimal
- E.g., Hill-climbing, Simulated Annealing, Genetic Algorithms

---

## LO3: Knowledge Representation & Expert Systems

### 3.1 Knowledge Representation
| Method | Description |
|--------|-------------|
| **Propositional Logic** | Facts with connectives (AND, OR, NOT) |
| **First-Order Logic** | Objects, relations, quantifiers |
| **Production Rules** | IF-THEN rules |
| **Semantic Networks** | Graph of concepts & relationships |
| **Frames** | OOP-like with slots |

### 3.2 Expert Systems
- Emulates human expert decision-making
- Components: **Knowledge Base** + **Inference Engine** + UI
- Uses **laws of logic** to represent knowledge
- **Forward chaining** (data→conclusion) vs **Backward chaining** (goal→facts)

---

## LO4: Problem Solving, Planning & Game Playing

### 4.1 State Space Search
- Translate problems into **search algorithms** to find ideal solutions
- States → Actions → Goal test → Path cost

### 4.2 Automatic Planning
- **Automatic programming**: generating plans with conditionals/loops from logical specifications
- STRIPS planning language

### 4.3 Game Playing
- **Minimax**: optimal decision in zero-sum games
- **Alpha-Beta pruning**: optimizes minimax by pruning irrelevant branches

### 4.4 Backtracking & CSP
- **CSP**: variables + domains + constraints
- **Backtracking search**: DFS with constraint checking

---

## LO5: ML Basics (From Exam Questions)

### 5.1 ML Types
- **Supervised**: labeled data (classification, regression)
- **Unsupervised**: **no labels** (clustering, association)
- **Reinforcement**: rewards/punishments
- **Transfer**: knowledge from one task to another

### 5.2 Overfitting (Exam Q4)
- Model fits training data **too closely**
- Works well on training, **poorly on new data**

### 5.3 Model Development
- **Large dataset boosts performance** ✓
- Training > Test set proportion (70-80% train)
- No overlap between train and test

### 5.4 Data Mining Process
**Training → Testing → Evaluation → Deployment**

### 5.5 Association Rule
- Finds relationships between variables (market basket analysis)
- Big data analytics technique

---

## Exam-Style Q&A (From 14 Actual Questions)

**Q1:** What describes informed search algorithms?
- a. Complete   b. Consistent   c. **Admissible** ✓   d. Optimal

**Q2:** Correct statement about local search algorithms?
- a. For convex optimization
- b. Time complexity independent of size
- c. **Quality depends on starting point and neighborhood** ✓
- d. Always globally optimal

**Q3:** Divergence between Dijkstra and UCS?
- a. UCS optimal, Dijkstra not
- b. **Dijkstra discovers as they come; UCS collects in Queue first** ✓
- c. Dijkstra optimal, UCS not
- d. UCS discovers as they come

**Q4:** Model fits training too closely, poor on new data?
- a. **Overfitting** ✓   b. Underfitting   c. Underperforming   d. Sweet spot

**Q5:** AI system is composed of?
- a. **Agent and Environment** ✓   b. Tech & Evolution   c. Data & Info   d. Device & Network

**Q6:** Anything that perceives and acts?
- a. **Agent** ✓   b. Expert System   c. Intelligence   d. API

**Q7:** Informed, exponential worst-case, guarantees optimality?
- a. **A\* search** ✓   b. Greedy best-first   c. UCS   d. IDA\*

**Q8:** Algorithm for data without labels?
- a. Transfer   b. Supervised   c. **Unsupervised** ✓   d. Reinforcement

**Q9:** Correct about AI?
- a. Physical tasks only   b. Simple tasks only   c. Lab tasks only   d. **Tasks requiring human intelligence** ✓

**Q10:** True about ML model development?
- a. Focus on test data   b. **Large dataset boosts performance** ✓   c. Overlap train/test   d. Train < test

**Q11:** Generating plans with conditionals/loops from logical specs?
- a. **Automatic programming** ✓   b. Monitoring   c. Recursive   d. Learning

**Q12:** Correct data mining process?
- a. **Training → Testing → Evaluation → Deployment** ✓
