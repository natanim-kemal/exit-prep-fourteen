# Day 9 — Software Project Management (65 Items)

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

## Quick Reference — Blueprint Table

| LO | Topic | Items | Cognitive |
|----|-------|-------|-----------|
| 1 | Explain SPM tasks | 2 | 1 Rem, 1 Und |
| 2 | Develop WBS, schedule, cost | 4 | 2 App, 2 Ana |
| 3 | Use PM tools, techniques, skills | 2 | 1 Und, 1 App |
| 4 | Plan docs for risk, quality management | 2 | 1 Und, 1 App |
| **Total** | | **7** | |


## Practice Questions (from Question Bank)

Answer: A
### Q836. Critical path in project network?

- A) Highest risk path
- B) Shortest path
- C) Sequence with zero float
- D) Most expensive path
  **Answer: D**

### Q837. In a resource-constrained environment, kLOC stands for?

- A) Kernel Level Object Count
- B) Key Logic Operations Count
- C) Known Lines of Code
- D) Kilo Lines of Code
  **Answer: B**

### Q838. Iron Triangle?

- A) Scope, Time, Cost
- B) Cost, Quality, Risk
- C) Budget, Resources, Schedule
- D) Requirements, Design, Testing
  **Answer: A**

### Q839. Product Owner in Scrum?

- A) Customer only
- B) Technical lead
- C) Manages product backlog
- D) Team facilitator
  **Answer: B**

### Q840. When designing for high performance, wBS is?

- A) Risk register
- B) Hierarchical decompositio
- C) Gantt chart
- D) Network diagram
  **Answer: C**

### Q841. Transfer risk response?

- A) Eliminate cause
- B) Insurance
- C) Accept risk
- D) Reduce probability
  **Answer: D**

### Q842. CMMI Level 3 'Defined'?

- A) Project-level management
- B) Statistical control
- C) Unpredictable processes
- D) Organisation-wide standardised
  **Answer: C**

### Q843. When designing for high performance, pERT vs CPM?

- A) CPM has 3 estimates
- B) PERT has 3 time estimates
- C) CPM for software only
- D) PERT finds critical path
  **Answer: A**

### Q844. Project lifecycle phases in order?

- A) Requirements, Design, Code, Test
- B) Analysis, Design, Build, Test, Deploy
- C) Initiation, Planning, Execution, Monitoring, Closure
- D) Planning, Initiation, Execution, Closure
  **Answer: C**

### Q845. How is Float (slack) in project network best characterized?

- A) Resource availability
- B) Risk probability
- C) Budget buffer
- D) Time task can be delayed
  **Answer: B**

### Q846. In a resource-constrained environment, gantt chart shows?

- A) Risk analysis
- B) Task schedule as bars
- C) Cost breakdown
- D) Resource usage only
  **Answer: A**

### Q847. PERT uses how many time estimates?

- A) 5
- B) 3
- C) 1
- D) 2
  **Answer: C**

### Q848. How is Pert optimistic time estimate best characterized?

- A) Shortest possible duration
- B) Average duration
- C) Most likely duration
- D) Worst case duration
  **Answer: C**

### Q849. When designing for high performance, cPM critical path has float of?

- A) Minimum but >0
- B) 1
- C) Maximum
- D) 0
  **Answer: A**

### Q850. Milestone in project management is?

- A) Resource allocation
- B) Project phase
- C) Significant checkpoint
- D) Risk item
  **Answer: C**

### Q851. Risk probability times impact equals?

- A) Risk response
- B) Risk register entry
- C) Risk tolerance
- D) Risk score/exposure
  **Answer: C**

### Q852. Consider a system where how is Risk avoidance best characterized?

- A) Transfer to insurance
- B) Reduce probability
- C) Accept and monitor
- D) Eliminate risk cause entirely
  **Answer: B**

### Q853. Which statement about Risk mitigation is correct?

- A) Reduce probability
- B) Transfer to insurance
- C) Accept risk
- D) Eliminate risk
  **Answer: C**

### Q854. How is Risk acceptance best characterized?

- A) Transfer risk
- B) Acknowledge risk and
- C) Reduce impact
- D) Eliminate risk
  **Answer: B**

### Q855. Consider a system where function Point Analysis measures?

- A) Test coverage
- B) Lines of code
- C) Functionality from user
- D) Number of bugs
  **Answer: A**

### Q856. Bottom-up estimation?

- A) Expert judgment only
- B) Use historical data
- C) Estimate whole project at once
- D) Estimate each component then sum up
  **Answer: C**

### Q857. Analogous estimation?

- A) Mathematical formula
- B) Decomposing work packages
- C) Using similar past project as basis
- D) Expert consensus
  **Answer: C**

### Q858. Consider a system where identify the correct statement about scope creep.

- A) Budget overrun
- B) Uncontrolled growth in
- C) Project schedule slipping
- D) Quality degradation
  **Answer: B**

### Q859. Which of the following best describes project charter?

- A) Legal contract
- B) Document authorizing
- C) Risk register
- D) Work breakdown structure
  **Answer: A**

### Q860. Which description of stakeholder management is accurate?

- A) Managing company stock
- B) Managing project budget
- C) Identifying and managing
- D) Managing project team
  **Answer: D**

### Q861. Which description of earned value management (EVM) is accurate?

- A) ROI calculation
- B) Employee performance review
- C) Project performance technique
- D) Budget approval process
  **Answer: C**

### Q862. Which statement about Spi (schedule performance index) > 1 is correct?

- A) Over budget
- B) On schedule
- C) Behind schedule
- D) Ahead of schedule
  **Answer: D**

### Q863. Which statement about Cpi (cost performance index) < 1 is correct?

- A) On budget
- B) Under budget
- C) Ahead of schedule
- D) Over budget
  **Answer: C**

### Q864. Identify the correct statement about RAM (Responsibility Assignment Matrix).

- A) Resource allocation matrix
- B) Matrix showing who is
- C) Risk assessment method
- D) Memory management tool
  **Answer: B**

### Q865. RACI stands for?

- A) Risk, Analysis, Control, Implementation
- B) Responsible, Accountable, Consulted, Informed
- C) Requirements, Acceptance, Completion, Inspection
- D) Resource, Activity, Cost, Integration
  **Answer: A**

### Q866. Which description of project baseline is accurate?

- A) Starting budget only
- B) First sprint plan
- C) Approved plan for scope
- D) Initial risk assessment
  **Answer: A**

### Q867. Which of the following best describes change control in projects?

- A) Version control
- B) Bug tracking process
- C) Configuration management
- D) Process for managing and
  **Answer: D**

### Q868. Which of the following best describes project closure?

- A) Deployment phase
- B) Formal completion:
- C) Canceling project
- D) Final testing phase
  **Answer: B**

### Q869. Which description of lessons learned in project management is accurate?

- A) Documentation of what
- B) User documentation
- C) Test results
- D) Training materials
  **Answer: C**

### Q870. Consider a system where which description of resource leveling is accurate?

- A) Making all resources same skill
- B) Equalizing team workload permanently
- C) Balancing project budget
- D) Adjusting schedule to avoid resource
  **Answer: C**

### Q871. Which of the following best describes project management office (PMO)?

- A) Quality assurance team
- B) Development team
- C) Physical office
- D) Department standardizing
  **Answer: A**

### Q872. Which of the following best describes configuration management?

- A) Network configuration
- B) Server configuration
- C) Database configuration
- D) Controlling and tracking
  **Answer: A**

### Q873. In a resource-constrained environment, daily Scrum/Standup purpose?

- A) Sprint planning
- B) Retrospective
- C) Product demo
- D) Brief synchronization on
  **Answer: A**

### Q874. Sprint Review purpose?

- A) Sprint planning
- B) Team performance review
- C) Retrospective
- D) Demonstrating completed
  **Answer: D**

### Q875. Sprint Retrospective purpose?

- A) Planning next sprint
- B) Reviewing backlog
- C) Team reflecting on process
- D) Demo work to customers
  **Answer: B**

### Q876. Consider a system where which of the following best describes sprint goal?

- A) Number of story points completed
- B) Team velocity target
- C) Concise objective for sprint
- D) List of all sprint tasks
  **Answer: B**

### Q877. Identify the correct statement about Definition of Ready (DoR).

- A) When definition is approved
- B) Criteria backlog item must meet
- C) When product is shipped
- D) Developer readiness checklist
  **Answer: C**

### Q878. COCOMO Basic formula?

- A) Effort = KLOC × team_size
- B) Effort = lines_per_day ×
- C) Effort = a × ^b
- D) Effort = function_points ×
  **Answer: A**

### Q879. In a resource-constrained environment, identify the correct statement about project risk register.

- A) Change request log
- B) List of completed risks
- C) Document listing
- D) Bug report database
  **Answer: A**

### Q880. Which description of project management plan is accurate?

- A) Comprehensive document
- B) Project schedule only
- C) Risk assessment
- D) Budget spreadsheet
  **Answer: C**

### Q881. Net Present Value (NPV) in project selection?

- A) Present value of future
- B) Software license cost
- C) Current project cost
- D) Team salary total
  **Answer: D**

### Q882. Which of the following best describes ROI in project context?

- A) Rate of interest
- B) Rate of incidents
- C) Return on Investment —
- D) Risk of implementation
  **Answer: C**

### Q883. Which description of feasibility study is accurate?

- A) Requirements gathering
- B) Assessment of project viability
- C) Market analysis
- D) Testing feasibility of bugs
  **Answer: D**

### Q884. Identify the correct statement about procurement management.

- A) Resource scheduling
- B) Budget allocation
- C) Purchasing office supplies
- D) Managing acquisition of
  **Answer: D**

### Q885. Identify the correct statement about communication management in projects.

- A) Team meetings management
- B) Documentation writing
- C) Email management
- D) Planning and controlling
  **Answer: C**

### Q886. Which of the following best describes project sponsor?

- A) Project manager alternative name
- B) Key stakeholder with no authority
- C) Senior person championing project and
- D) Financial backer from outside
  **Answer: D**

### Q887. Which of the following best describes project scope statement?

- A) Team charter
- B) Risk assessment
- C) Document describing
- D) Budget statement
  **Answer: C**

### Q888. In a resource-constrained environment, identify the correct statement about resource histogram.

- A) Cost variance chart
- B) Bar chart showing resource
- C) Risk visualization
- D) Gantt chart variant
  **Answer: A**

### Q889. Which of the following best describes critical chain method?

- A) Dependency chain optimization
- B) Critical path variant
- C) Schedule method accounting
- D) Risk chain analysis
  **Answer: D**

### Q890. Which description of project constraint is accurate?

- A) Legal requirement
- B) Technical limitation
- C) Restriction limiting
- D) Risk factor
  **Answer: C**

### Q891. Identify the correct statement about quality assurance vs quality control.

- A) Both are testing activities only
- B) QA is process-focused prevention
- C) No difference
- D) QC is prevention
  **Answer: B**

### Q892. Which of the following best describes purpose of a kickoff meeting?

- A) Project closure ceremony
- B) Requirements review
- C) Sprint planning
- D) Formal project start
  **Answer: C**

### Q893. Which description of issue management is accurate?

- A) Process for identifying
- B) Risk identification
- C) Software bug tracking
- D) Change control
  **Answer: C**

### Q894. In a resource-constrained environment, difference between risk and issue in PM?

- A) Issue is potential
- B) Risk is potential future problem
- C) No difference
- D) Both are potential
  **Answer: A**

### Q895. Which of the following best describes time boxing in Agile?

- A) Scheduling meetings
- B) Sprint velocity calculation
- C) Fixed time period for
- D) Estimating in hours
  **Answer: C**

### Q896. Identify the correct statement about minimum viable product (MVP).

- A) Beta version
- B) Prototype
- C) Product with minimum
- D) Cheapest possible product
  **Answer: C**

### Q897. When designing for high performance, what does Monte Carlo simulation do in PM?

- A) Estimates using gambling odds
- B) Optimizes resource allocation
- C) Generates random tasks
- D) Uses random sampling to model
  **Answer: D**

### Q898. Which description of gold plating in project management is accurate?

- A) Premium project approach
- B) High quality deliverable
- C) Adding extra features/functional
- D) Award-winning project
  **Answer: A**

### Q899. Identify the correct statement about purpose of a project status report.

- A) Legal requirement
- B) Communicating progress
- C) Technical documentation
- D) Budget approval
  **Answer: D**

### Q900. When designing for high performance, which of the following best describes capacity planning?

- A) Determining resources
- B) Server capacity
- C) Database capacity
- D) Network capacity
