# Day 9 — Software Project Management Complete Theory (7 Items)

## LO1: SPM Tasks & Fundamentals (2 items)

### 1.1 What is a Project?
- **Project**: a **temporary** endeavor undertaken to create a **unique** product, service, or result
- **NOT a process** (processes are ongoing, repetitive activities)
- **Program**: group of related projects managed together
- **Portfolio**: collection of programs, projects, and operations

### 1.2 Project vs Process
| Aspect | Project | Process |
|--------|---------|---------|
| Duration | Temporary (finite) | Ongoing (continuous) |
| Output | Unique product/service | Repeatable result |
| Example | Building a mobile app | Monthly payroll |

### 1.3 Project Management Lifecycle
- **Initiating** → **Planning** → **Executing** → **Monitoring & Controlling** → **Closing**
- **Project Planning** process group generates: project schedule, cost estimations, work breakdown structure (WBS)

### 1.4 Organizational Structures
| Structure | PM Authority | Resource Availability | PM Role |
|-----------|-------------|---------------------|---------|
| **Functional** | Little or none | Little or none | Functional manager controls budget, PM is part-time |
| Matrix (weak/balanced/strong) | Low to high | Low to high | Varies |
| **Projectized** | High to almost total | High to almost total | Full-time PM + admin staff |

**Functional**: limited PM authority, limited resource availability, part-time PM role, functional manager controls project budget

### 1.5 Leadership Styles
| Style | Description |
|-------|-------------|
| **Theory X** | "My way or the highway" — assumes workers are lazy, need coercion |
| **Theory Y** | Assumes workers are motivated, self-directed |
| **Theory Z** | Japanese management — consensus, long-term employment |

---

## LO2: WBS, Scheduling & Cost Estimation (4 items)

### 2.1 Work Breakdown Structure (WBS)
- Hierarchical decomposition of project deliverables into smaller work packages
- Foundation for: scheduling, cost estimation, resource allocation
- Level 0 = Project → Level 1 = Major deliverables → Level 2 = Work packages

### 2.2 Gantt Charts
- **Horizontal axis**: **Time Scale**
- Vertical axis: tasks/activities
- Bars represent task duration
- Shows task dependencies and progress

### 2.3 Critical Path & Slack
- **Critical Path**: longest path through the project network; determines minimum project duration
- **Slack (Float)**: amount of time a task can be delayed without affecting the project
- **Slack = LF - EF** (Late Finish - Early Finish)
- **Also**: Slack = LS - ES (Late Start - Early Start)

### 2.4 COCOMO Model (Constructive Cost Model)
**Basic COCOMO formula:**
```
Effort (Ei) = a × (KLOC)^b   (person-months)
```
Where:
- a, b = constants depending on project mode
- KLOC = thousands of lines of code

**Project modes**:
| Mode | a | b | Description |
|------|---|---|-------------|
| Organic | 2.4 | 1.05 | Small teams, familiar environment |
| Semi-detached | 3.0 | 1.12 | Medium complexity, mixed experience |
| Embedded | 3.6 | 1.20 | Tight constraints, hardware interface |

**Example**: 50 KLOC, organic mode → Ei = 2.4 × (50)^1.05 ≈ 2.4 × 63.1 ≈ 151.4 person-months

### 2.5 Function Point Analysis
- Alternative to LOC-based estimation
- Based on: inputs, outputs, inquiries, files, interfaces
- Adjusted by complexity and environmental factors

### 2.6 Resource Optimization
- **Resource leveling**: adjusting start/finish dates based on resource constraints to balance demand with available supply
- **Resource smoothing**: adjusting activities within their float to avoid peaks
- **Responsibility Assignment Matrix (RAM)**: maps work packages to team members

---

## LO3: PM Tools, Techniques & Skills (2 items)

### 3.1 Affinity Diagrams
- Technique that allows large numbers of ideas to be classified into groups for review and analysis
- Used during brainstorming and requirements gathering

### 3.2 Pareto Principle (80/20 Rule)
- **80% of the problem** can be fixed with **20% of the effort**
- Focus on the vital few tasks that yield the most benefit

### 3.3 PERT (Program Evaluation Review Technique)
- Uses three time estimates: Optimistic (O), Most Likely (M), Pessimistic (P)
- Expected time = (O + 4M + P) / 6

### 3.4 Earned Value Management (EVM) — Key Formulas
| Term | Meaning | Formula |
|------|---------|---------|
| **PV** | Planned Value (budgeted cost of work scheduled) | — |
| **EV** | Earned Value (budgeted cost of work performed) | — |
| **AC** | Actual Cost (actual cost of work performed) | — |
| **CV** | Cost Variance | EV - AC (negative = over budget) |
| **SV** | Schedule Variance | EV - PV (negative = behind schedule) |
| **CPI** | Cost Performance Index | EV / AC (< 1 = over budget) |
| **SPI** | Schedule Performance Index | EV / PV (< 1 = behind schedule) |
| **EAC** | Estimate at Completion | BAC / CPI |
| **ETC** | Estimate to Complete | EAC - AC |

### 3.5 Repository vs Workspace
| Term | Definition |
|------|-----------|
| **Repository** | A **library of releases** (permanent storage of approved baselines) |
| **Workspace** | A **library of promotions** (individual developer working area) |

---

## LO4: Risk Management, Quality & Plan Documents (2 items)

### 4.1 Risk Management
**Risk Exposure (RE)** = **Probability of Loss × Size of Loss**
- Also known as Risk Exposure or Risk Priority

**Risk Response Strategies**:
| Strategy | Action |
|----------|--------|
| **Risk Avoidance** | Change plan to avoid the risk |
| **Risk Transfer** | Shift impact to third party (insurance, contract) |
| **Risk Mitigation/Reduction** | Reduce probability or impact |
| **Risk Acceptance/Retention** | Acknowledge risk, no proactive action |

### 4.2 Quality Management
- **Quality is customer-driven** — defined by meeting customer expectations
- **CMMI** (Capability Maturity Model Integration): used by quality evaluators; plan-check-act approach
- **Code Auditor**: tool for checking minimum coding standards
- **Testing goal (as QA)**: to guarantee software meets specified requirements

### 4.3 SQA vs QC
| Aspect | Quality Assurance (QA) | Quality Control (QC) |
|--------|----------------------|---------------------|
| Focus | Process prevention | Product detection |
| When | Throughout project | During/after development |
| Activity | Audits, standards, CMMI | Testing, inspection, reviews |

### 4.4 Plan Documents
- **Project Management Plan**: integrates scope, schedule, cost, quality, risk
- **Risk Management Plan**: identifies risks, analysis, response strategies
- **Software Quality Management Plan**: quality standards, metrics, reviews
- **Configuration Management Plan**: identifies CM procedures, tools, roles

---

## Exam-Style Q&A (From Actual Model Exams)

**Q1:** In COCOMO model, Initial estimate Ei = ?
- a. b(KLOC)^a
- b. a*(KLOC)*b
- c. **a(KLOC)^b** ✓
- d. b*(KLOC)*a

**Q2:** In Gantt Chart, the horizontal axis is the?
- a. Total no. of Persons
- b. Cost of project
- c. **Time Scale** ✓
- d. Scope of the Project

**Q3:** Slack = ?
- a. LS-EF
- b. ES-LF
- c. ES-LS
- d. **LF-EF** ✓

**Q4:** Return on Investment (ROI) = ?
- a. **(Gain - Cost) / Cost** ✓
- b. (Gain - Cost) / Gain
- c. (Cost - Gain) / Gain
- d. (Cost - Gain) / Cost

**Q5:** A repository is a library of?
- a. Task Set
- b. **Releases** ✓
- c. Milestone
- d. Work Product

**Q6:** A workspace is a library of?
- a. Repository
- b. **Promotions** ✓
- c. Static Space
- d. Dynamic Space

**Q7:** Which leadership style is "my way or the highway"?
- a. **Theory X** ✓
- b. Theory L
- c. Theory Y
- d. Theory Z

**Q8:** Quality is?
- a. Analyst Driven
- b. Tester Driven
- c. Developer driven
- d. **Customer driven** ✓

**Q9:** Risk Exposure (RE) = ?
- a. Probability of Risk × Size of Risk
- b. **Probability of Loss × Size of Loss** ✓
- c. Probability of Risk / Size of Risk
- d. Probability of Loss / Size of Loss

**Q10:** Which principle states 80% of the problem can be fixed with 20% effort?
- a. **Pareto principle** ✓
- b. Parametric principle
- c. Pairwise principle
- d. Partition principle

**Q11:** ROI calculation — Total discounted benefits = Birr 120,000; Total discounted cost = Birr 100,000; ROI = ?
- a. **20%** ✓ → (120,000 - 100,000) / 100,000 = 20,000/100,000 = 0.20 = 20%
- b. 12%
- c. 30%
- d. 10%

**Q12:** Resource optimization adjusting dates based on resource constraints to balance demand with supply?
- a. Responsibility assignment matrix
- b. Resource smoothing
- c. **Resource leveling** ✓
- d. Resource grouping

**Q13:** Which organizational structure has little/no PM authority, little/no resource availability, functional manager controls budget?
- a. **Functional organization** ✓
- b. Projectized organization
- c. Matrix organization
- d. Strong matrix

**Q14:** Technique that classifies large numbers of ideas into groups for review?
- a. Activity-on-Node
- b. Activity List
- c. Adaptive Life Cycle
- d. **Affinity Diagrams** ✓

**Q15:** The process generating project schedule, cost estimates, and WBS is?
- a. Project Initiating
- b. Project Executing
- c. Project Closing
- d. **Project Planning** ✓

**Q16:** A temporary endeavor to create a unique product is a?
- a. Process
- b. **Project** ✓
- c. Program
- d. Portfolio

---

---

## Question Bank Study Notes

### Project Basics
**Project**: temporary, unique product. **Program**: related projects. **Portfolio**: collection of projects + programs.

### Planning & Scheduling
**WBS**: hierarchical task decomposition (scope management). **Gantt Chart**: visual timeline. **CPM**: critical path = longest dependent path, minimum project duration. **PERT**: probabilistic (optimistic/pessimistic/most likely).

### Cost Estimation
Expert judgment, analogous, parametric (COCOMO), bottom-up, three-point.

### Risk
Process: Identify → Analyze → Plan Response → Monitor. Strategies: Avoidance, Mitigation, Transference (insurance/outsource), Acceptance.

### EVM
PV (planned value), EV (earned value), AC (actual cost). CPI = EV/AC (>1 = under budget). SPI = EV/PV (>1 = ahead).


## Quick Reference — Blueprint Table

| LO | Topic | Items | Cognitive |
|----|-------|-------|-----------|
| 1 | Explain SPM tasks | 2 | 1 Rem, 1 Und |
| 2 | Develop WBS, schedule, cost | 4 | 2 App, 2 Ana |
| 3 | Use PM tools, techniques, skills | 2 | 1 Und, 1 App |
| 4 | Plan docs for risk, quality management | 2 | 1 Und, 1 App |
| **Total** | | **7** | |
