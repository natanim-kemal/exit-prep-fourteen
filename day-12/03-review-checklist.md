# Day 12 — Fundamentals of AI Review Checklist

## Mastery Checklist

### LO1: Intelligent Agents & AI Systems
- [ ] AI = machines performing tasks requiring human intelligence
- [ ] AI system = Agent + Environment
- [ ] Agent = perceives via sensors, acts via effectors
- [ ] Agent types: Simple Reflex, Model-Based, Goal-Based, Utility-Based, Learning

### LO2: Search Strategies
- [ ] Uninformed (blind): BFS, DFS, UCS, Iterative Deepening
- [ ] Informed (heuristic): A*, Greedy Best-First
- [ ] A*: f(n) = g(n) + h(n) — informed, complete, optimal (admissible heuristic)
- [ ] Admissible heuristic: never overestimates (h(n) ≤ true cost)
- [ ] UCS vs Dijkstra: UCS collects in queue first; Dijkstra discovers as they come
- [ ] Local Search: quality depends on starting point + neighborhood function

### LO3: Knowledge Representation & Expert Systems
- [ ] Knowledge rep methods: logic, rules, semantic networks, frames
- [ ] Expert system: Knowledge Base + Inference Engine + UI
- [ ] Forward chaining (data→conclusion), Backward chaining (goal→facts)

### LO4: Problem Solving & Game Playing
- [ ] State space search: translate problems to search algorithms
- [ ] Minimax: optimal in zero-sum games; Alpha-Beta pruning optimizes
- [ ] CSP: variables + domains + constraints; backtracking search
- [ ] Automatic programming: plans with conditionals/loops from logical specs

### LO5: Machine Learning Basics
- [ ] Supervised (labeled), Unsupervised (no labels), Reinforcement (rewards)
- [ ] Overfitting: good on training, poor on new data
- [ ] Large dataset boosts model performance
- [ ] Data mining process: Train → Test → Evaluate → Deploy

---

## Quick Mnemonics

| Concept | Mnemonic |
|---------|----------|
| AI definition | "Human intelligence, not simple/lab-only" |
| Agent | "Perceives + Acts = Agent" |
| A* formula | "f = got from start + hope to goal" |
| Admissible | "Never Overestimate = Admissible" |
| UCS vs Dijkstra | "UCS = Queue first; Dijkstra = Discover as they come" |
| Overfitting | "Only training fits, test fails" |
| Data mining | "Train → Test → Evaluate → Deploy" (TTED) |

## 1-Page Cram Sheet

```
AI = machines doing tasks requiring human intelligence
Agent + Environment

AGENTS: Simple Reflex | Model-Based | Goal-Based | Utility-Based | Learning

SEARCH:
  Uninformed: BFS, DFS, UCS, Iterative Deepening
  Informed: A*, Greedy Best-First
  A*: f(n) = g(n) + h(n) — informed, complete, optimal (admissible h)

EXPERT SYSTEMS: Knowledge Base + Inference Engine + UI

MINIMAX: optimal zero-sum; Alpha-Beta = pruning

ML: Supervised (labeled) | Unsupervised (no labels) | Reinforcement (rewards)
Overfitting: train ✓, test ✗
Data Mining: Train → Test → Evaluate → Deploy
