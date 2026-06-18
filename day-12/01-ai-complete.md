# Day 12 — Fundamentals of AI (87 Items)

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


## Practice Questions (from Question Bank)

Answer: A
### Q1096. A* f(n) = g(n) + h(n)?

- A) g=cost from start
- B) f=nodes explored
- C) g=heuristic
- D) f=path cost
  **Answer: D**

### Q1097. Admissible heuristic?

- A) Never overestimates true
- B) Always overestimates
- C) Computed in O
- D) Returns 0 always
  **Answer: C**

### Q1098. Consider a system where iDDFS advantage over BFS?

- A) DFS memory with BFS
- B) Handles weighted edges
- C) Faster always
- D) Never revisits nodes
  **Answer: D**

### Q1099. Alpha-beta pruning?

- A) Evaluates leaf nodes only
- B) Prunes branches not affecting result
- C) Changes minimax result
- D) Adds learning to minimax
  **Answer: B**

### Q1100. Model-Based Reflex Agent vs Simple Reflex?

- A) Simple has memory
- B) Model-Based uses only
- C) Same capability
- D) Model-Based maintains
  **Answer: B**

### Q1101. In a resource-constrained environment, how is ∀x in first-order logic best characterized?

- A) No value of x
- B) For all values of x
- C) At least one x
- D) Exactly one x
  **Answer: A**

### Q1102. Bayes Theorem in AI?

- A) Shortest paths
- B) Updating probability of
- C) Neural network training
- D) Game tree evaluation
  **Answer: D**

### Q1103. Hill Climbing stuck in?

- A) Goal states
- B) Local maxima and other mechanisms
- C) Start states
- D) Global maxima
  **Answer: B**

### Q1104. Consider a system where state space is?

- A) Branching factor × depth
- B) All optimal solutions
- C) Memory used by search
- D) All states reachable from initial state
  **Answer: C**

### Q1105. A* space complexity weakness?

- A) Cannot use heuristics
- B) Keeps all generated
- C) Not optimal
- D) Not complete
  **Answer: B**

### Q1106. BFS vs DFS completeness?

- A) DFS complete
- B) BFS complete
- C) Neither complete
- D) Both complete
  **Answer: A**

### Q1107. When designing for high performance, uCS (Uniform Cost Search) expands?

- A) Random node
- B) Shallowest node
- C) Deepest node
- D) Node with lowest path cost
  **Answer: A**

### Q1108. Depth-Limited Search limitation?

- A) Not optimal
- B) Fails if goal is deeper
- C) Uses too much memory
- D) Too slow
  **Answer: D**

### Q1109. Bidirectional search complexity?

- A) Ob
- B) Od
- C) Ob^d
- D) Ob^d/2
  **Answer: C**

### Q1110. Consider a system where greedy Best-First Search uses?

- A) Random heuristic
- B) Only g
- C) f = g + h
- D) Only h
  **Answer: A**

### Q1111. Greedy Best-First Search is?

- A) Optimal but not complete
- B) Fast but not optimal
- C) Complete and optimal
- D) Neither fast nor optimal
  **Answer: A**

### Q1112. Consistent heuristic satisfies?

- A) h = g always
- B) h > actual cost always
- C) h = 0 for all n
- D) h ≤ c + h for all successors
  **Answer: C**

### Q1113. When designing for high performance, simulated annealing improves hill climbing by?

- A) Expanding all neighbours
- B) Running multiple agents
- C) Accepting worse moves with
- D) Using better heuristic
  **Answer: A**

### Q1114. Genetic algorithm uses?

- A) Selection, crossover
- B) Constraint propagation
- C) Gradient descent
- D) Game trees
  **Answer: D**

### Q1115. Minimax MAX player does?

- A) Prunes alpha branches
- B) Maximizes score choosing
- C) Evaluates leaf nodes
- D) Minimizes score
  **Answer: D**

### Q1116. When designing for high performance, minimax MIN player does?

- A) Minimizes score
- B) Maximizes score
- C) Evaluates root only
- D) Prunes beta branches
  **Answer: A**

### Q1117. Alpha in alpha-beta pruning is?

- A) Best MAX can guarantee
- B) Heuristic estimate
- C) Current path cost
- D) Best MIN can guarantee
  **Answer: D**

### Q1118. Beta in alpha-beta pruning is?

- A) Branching factor
- B) Node depth
- C) Best MIN can guarantee
- D) Best MAX can guarantee
  **Answer: C**

### Q1119. When designing for high performance, prune in alpha-beta when?

- A) Alpha >= Beta
- B) Depth limit reached
- C) Alpha < Beta
- D) Goal found
  **Answer: C**

### Q1120. Modus Ponens inference rule?

- A) If P and Q then R
- B) If not P then Q
- C) If P
- D) If P and P→Q then Q
  **Answer: B**

### Q1121. Bayesian Network is a?

- A) Directed Acyclic Graph of
- B) Markov decision process
- C) Hidden Markov model
- D) Feed-forward neural network
  **Answer: A**

### Q1122. Consider a system where sTRIPS in classical planning uses?

- A) Neural networks
- B) Preconditions, add list
- C) Bayesian inference
- D) Search without state
  **Answer: B**

### Q1123. CSP (Constraint Satisfaction Problem) components?

- A) Variables, domains, constraints
- B) States, actions, goals
- C) Sensors, actuators, environment
- D) Nodes, edges, weights
  **Answer: A**

### Q1124. Backtracking in CSP?

- A) Forward checking only
- B) Random restart
- C) Reverses search order
- D) Assigns value
  **Answer: A**

### Q1125. When designing for high performance, forward chaining in logic?

- A) Works forward from facts to
- B) Works backward from goal
- C) Uses Bayesian inference
- D) Combines both directions
  **Answer: C**

### Q1126. Backward chaining in logic?

- A) Works forward from facts
- B) Uses Bayesian network
- C) Combines both directions
- D) Works backward from goal to
  **Answer: A**

### Q1127. Resolution principle in logic?

- A) Updates Bayesian network
- B) Plans action sequences
- C) Inference rule combining
- D) Solves CSP
  **Answer: B**

### Q1128. When designing for high performance, in which scenario would is be employed?

- A) Grid problems where
- B) Weighted graphs
- C) 3D navigation
- D) Euclidean distance
  **Answer: D**

### Q1129. Euclidean distance heuristic is?

- A) Not admissible
- B) Straight-line distance —
- C) Always overestimating
- D) Only for unweighted grids
  **Answer: B**

### Q1130. Which statement about Bfs space complexity o(b^d) is correct?

- A) Linear in branching
- B) Linear in depth
- C) Constant space
- D) Exponential in number of
  **Answer: C**

### Q1131. Which statement about Dfs space complexity o(bm) is correct?

- A) Constant
- B) Linear in maximum depth
- C) Quadratic
- D) Exponential
  **Answer: C**

### Q1132. Which description of rational agent is accurate?

- A) Agent with perfect knowledge
- B) Agent using rational numbers
- C) Agent following rules only
- D) Agent acting to maximize
  **Answer: B**

### Q1133. Goal-Based Agent?

- A) Maximizes utility function
- B) No goals
- C) Uses only condition-action rules
- D) Has goals and chooses actions to
  **Answer: A**

### Q1134. In a resource-constrained environment, utility-Based Agent?

- A) No goals
- B) Only goal-driven
- C) Uses utility function to
- D) Simple reflex agent
  **Answer: D**

### Q1135. Learning Agent components?

- A) Goal and utility only
- B) Learning element
- C) Sensors and actuators only
- D) Rules and facts
  **Answer: C**

### Q1136. Which description of environment observability is accurate?

- A) Number of agents
- B) Size of state space
- C) Whether agent can access
- D) How fast agent acts
  **Answer: C**

### Q1137. In a resource-constrained environment, fully observable vs partially observable?

- A) Fully: agent perceives
- B) No difference
- C) Both mean same thing
- D) Partially: complete state
  **Answer: A**

### Q1138. Which of the following best describes stochastic environment?

- A) Static environment
- B) Has uncertainty — same
- C) Single agent only
- D) Fully predictable
  **Answer: A**

### Q1139. Which of the following best describes n episodic environment?

- A) Each episode independent
- B) Sequential decisions matter
- C) Continuous learning
- D) Time-based tasks
  **Answer: B**

### Q1140. Consider a system where which description of Turing Test is accurate?

- A) Test of machine intelligence:
- B) Cryptography test
- C) Computational speed test
- D) Alan Turing's programming
  **Answer: C**

### Q1141. Which description of production system in AI is accurate?

- A) Deep learning system
- B) Software for production
- C) Rule-based system with
- D) Manufacturing AI
  **Answer: B**

### Q1142. Expert system components?

- A) Search tree and heuristic
- B) Neural network layers
- C) Training data and model
- D) Knowledge base + inference engine
  **Answer: A**

### Q1143. In a resource-constrained environment, identify the correct statement about frame problem in AI.

- A) Neural network overfitting
- B) Video frame analysis
- C) Search space size problem
- D) Challenge of representing what
  **Answer: A**

### Q1144. Planning graph in Graphplan?

- A) Bayesian network
- B) Structure alternating
- C) State space search tree
- D) Neural network graph
  **Answer: A**

### Q1145. Identify the correct statement about constraint propagation in CSP.

- A) Propositional logic inference
- B) Neural propagation
- C) Reducing domains using constraints
- D) Spreading constraints to other
  **Answer: B**

### Q1146. In a resource-constrained environment, arc consistency (AC-3) in CSP?

- A) AC-3 is arc compression
- B) Ensures for every value in
- C) Builds constraint arcs
- D) Makes graph arc-shaped
  **Answer: A**

### Q1147. Propositional logic limitation vs FOL?

- A) Cannot express disjunctions
- B) Cannot express relations over objects
- C) Cannot handle uncertainty
- D) Cannot express implications
  **Answer: D**

### Q1148. Which of the following best describes knowledge base in AI?

- A) Set of sentences in
- B) Database of facts
- C) Search algorithm
- D) Training dataset
  **Answer: B**

### Q1149. When designing for high performance, which of the following best describes inference in AI?

- A) Neural computation
- B) Machine learning
- C) Pattern recognition
- D) Deriving new knowledge
  **Answer: A**

### Q1150. Truth table for P→Q: when is it FALSE?

- A) P=T, Q=T
- B) P=T, Q=F
- C) P=F, Q=T
- D) P=F, Q=F
  **Answer: B**

### Q1151. Which statement about Propositional logic ∧ is correct?

- A) NOT
- B) OR
- C) IMPLIES
- D) AND
  **Answer: C**

### Q1152. In a resource-constrained environment, how is Propositional logic ∨ best characterized?

- A) NOT
- B) OR
- C) IMPLIES
- D) AND
  **Answer: A**

### Q1153. How is Propositional logic ¬ best characterized?

- A) NOT
- B) OR
- C) AND
- D) IMPLIES
  **Answer: B**

### Q1154. Identify the correct statement about n admissible heuristic for 8-puzzle.

- A) Manhattan distance
- B) Number of moves made
- C) Euclidean distance only
- D) Distance to goal state
  **Answer: A**

### Q1155. Consider a system where iDA* combines?

- A) A* with iterative deepening
- B) Greedy search and UCS
- C) Bidirectional search and A*
- D) BFS and DFS
  **Answer: B**

### Q1156. Identify the correct statement about game tree.

- A) Decision tree for
- B) Tree of all possible game
- C) Minimax path only
- D) Random forest in game
  **Answer: A**

### Q1157. Evaluation function in minimax?

- A) Cost function for path
- B) Estimates utility of non-terminal
- C) Heuristic for finding goal
- D) Exact utility of leaf node
  **Answer: A**

### Q1158. Which description of n environment's transitional model is accurate?

- A) Describes what state results from each action
- B) Probability of environment changes
- C) Environment changes over time
- D) Sensor readings transition
  **Answer: B**

### Q1159. Identify the correct statement about path cost in search.

- A) Numerical cost of reaching
- B) Number of states in path
- C) Memory used for path
- D) Time to find path
  **Answer: D**

### Q1160. Complete search algorithm?

- A) Has no time limit
- B) Always finds optimal path
- C) Guaranteed to find
- D) Explores all states
  **Answer: D**

### Q1161. When designing for high performance, optimal search algorithm?

- A) Uses best heuristic
- B) Fastest algorithm
- C) Guaranteed to find
- D) Always complete
  **Answer: D**

### Q1162. DFS memory advantage?

- A) O1
- B) Ob^d
- C) O — only needs to store
- D) Ob^m
  **Answer: D**

### Q1163. Which description of hill climbing's random restart is accurate?

- A) Restarts from random state to
- B) Restarts with same starting state
- C) Restarts with larger step
- D) Restarts from goal
  **Answer: B**

### Q1164. When designing for high performance, genetic algorithm crossover?

- A) Selects best individual
- B) Removes worst individual
- C) Mutates single individual
- D) Combines parts of two parent
  **Answer: A**

### Q1165. Genetic algorithm mutation?

- A) Selects best individuals
- B) Combines two parents
- C) Eliminates weakest
- D) Randomly modifies
  **Answer: B**

### Q1166. Genetic algorithm selection?

- A) Selects all equally
- B) Random selection
- C) Preferentially selects
- D) Selects worst for
  **Answer: D**

### Q1167. Identify the correct statement about fitness function in GA.

- A) Crossover probability
- B) Physical fitness of agent
- C) Constraint checker
- D) Function evaluating quality
  **Answer: C**

### Q1168. Temperature in simulated annealing?

- A) CPU temperature
- B) Environment warmth
- C) Constant parameter
- D) Parameter controlling
  **Answer: D**

### Q1169. Identify the correct statement about n informed search strategy.

- A) Search using problem-specific knowledge
- B) Search with complete information
- C) Search with no domain knowledge
- D) Search with guaranteed optimality
  **Answer: D**

### Q1170. Consider a system where bFS optimal condition?

- A) Optimal when all step costs
- B) Always optimal
- C) Optimal when heuristic is
- D) Optimal on trees only
  **Answer: D**

### Q1171. Which description of iterative deepening depth first search complexity is accurate?

- A) O memory
- B) Same as DFS
- C) Worse than both BFS and
- D) Same asymptotic as BFS
  **Answer: B**

### Q1172. Which description of closed list in search is accurate?

- A) Priority queue
- B) List of goals
- C) Failed states
- D) Set of already-explored
  **Answer: B**

### Q1173. Identify the correct statement about frontier/open list in search.

- A) Failed nodes
- B) Goal states
- C) Nodes generated but not
- D) Explored nodes
  **Answer: B**

### Q1174. Dijkstra's algorithm is equivalent to?

- A) Greedy best-first search
- B) DFS on weighted graph
- C) UCS
- D) BFS on weighted graph
  **Answer: A**

### Q1175. What does 'pruning' mean in search?

- A) Eliminating branches that
- B) Trimming trees
- C) Removing leaf nodes
- D) Reducing heuristic value
  **Answer: B**

### Q1176. Consider a system where identify the correct statement about solution in search.

- A) Optimal path only
- B) Any state in state space
- C) Any path from start
- D) Sequence of actions
  **Answer: C**

### Q1177. Which description of n action's precondition in planning is accurate?

- A) Condition that must hold
- B) Effect of action
- C) Duration of action
- D) Cost of action
  **Answer: B**

### Q1178. Identify the correct statement about goal test in search.

- A) Optimality check
- B) Test of heuristic quality
- C) Completeness check
- D) Check determining if
  **Answer: A**

### Q1179. Consider a system where expert system advantage over neural network?

- A) Learns from data
- B) Explainable reasoning —
- C) Better performance
- D) Handles uncertainty better
  **Answer: D**

### Q1180. Which description of fuzzy logic is accurate?

- A) Logic for fuzzy data
- B) Probabilistic logic
- C) Approximate reasoning with
- D) Logic with errors
  **Answer: A**

### Q1181. Which description of Markov Decision Process (MDP) is accurate?

- A) Network protocol
- B) Framework for decision
- C) Data compression method
- D) Cryptography protocol
  **Answer: A**

### Q1182. When designing for high performance, which description of Bellman equation in RL is accurate?

- A) Neural network update
- B) Heuristic calculation
- C) Recursive equation
- D) Encryption formula
