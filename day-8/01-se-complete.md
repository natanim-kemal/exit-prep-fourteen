# Day 8 — Fundamentals of Software Engineering Complete Theory (8 Items)

## LO1: Basic Principles of Software Engineering (3 items)

### 1.1 What is Software Engineering?
- **Software Engineering**: systematic, disciplined, quantifiable approach to development, operation, and maintenance of software
- **Fundamental activities**: Software Specification, Design & Implementation, Validation/Testing, Evolution

### 1.2 Software Processes
- A structured set of activities required to develop a software system
- Common activities: Requirements → Design → Implementation → Testing → Deployment → Maintenance

### 1.3 General Design Principles
- **Design should be traceable** to the analysis model
- **Design should accommodate change** (structured for flexibility)
- **Design should exhibit uniformity and integration**
- **Design should NOT reinvent the wheel** — reuse existing patterns/solutions
- **Modularity**: divide system into cohesive components with low coupling
- **Cohesion**: degree to which elements within a module belong together (high = good)
- **Coupling**: degree of interdependence between modules (low = good)

### 1.4 Fundamental SE Activities (Model 2 Q10)
- Software Specification
- Software Design and Implementation
- Software Validation (Testing)
- Software Evolution

---

## LO2: Software Process Models (3 items)

### 2.1 Waterfall Model
```
Requirements → Design → Implementation → Testing → Deployment → Maintenance
```
- **Sequential** phases; each phase completes before next begins
- **Best for**: stable requirements, simple systems, small projects
- **Rigid**: changes are difficult once a phase is complete
- Scope, time, and cost determined in **early phase**

### 2.2 Incremental Model
- Deliver different functionalities (modules) with **different priority at different times**
- Successive iterations add functionality
- **Best for**: when requirements have different priorities, need early delivery of core features
- Each increment adds functionality within predetermined time frame

### 2.3 Agile Methods (High Exam Priority!)
- **Agile Manifesto values**:
  - **Individuals and interactions** over processes and tools
  - **Working software** over comprehensive documentation
  - **Customer collaboration** over contract negotiation
  - **Responding to change** over following a plan ← "Following a plan over responding to change" is AGAINST agile

- **Scrum**: leading agile development method
  - Sprints (time-boxed iterations, usually 2-4 weeks)
  - Roles: Product Owner, Scrum Master, Development Team
  - Events: Sprint Planning, Daily Stand-up, Sprint Review, Sprint Retrospective

- **Extreme Programming (XP)**: another agile method focused on technical practices
- **Best for**: changing environments, evolving requirements, business with uncertainty

### 2.4 Spiral Model
- **Risk-driven** approach
- Combines prototyping + waterfall + risk analysis
- Iterative cycles: Determine objectives → Identify risks → Develop & Test → Plan next iteration

### 2.5 Prototyping
- Creating a scaled-down or incomplete version of a system to demonstrate or test aspects
- Used for: clarifying requirements, demonstrating feasibility, reducing risk

### 2.6 Comparison
| Model | Pros | Cons | Best For |
|-------|------|------|----------|
| Waterfall | Simple, clear milestones | Rigid, late feedback | Stable requirements |
| Incremental | Early delivery, prioritize features | Requires good planning | Different-priority modules |
| Agile (Scrum/XP) | Flexible, customer involved | Less predictable, needs discipline | Changing requirements |
| Spiral | Risk management | Complex, expensive | High-risk projects |

---

## LO3: Requirements Engineering

### 3.1 Requirements Types
- **Functional requirements**: What the system should DO (services, features, behaviors)
  - "The system shall allow users to search products by name"
- **Non-functional requirements**: Constraints on the system (performance, security, usability)
  - "The system shall respond within 2 seconds"
  - Failing to meet NFRs may render the whole system unusable
  - A single NFR may affect the whole system
  - NFRs do NOT list the features of the system (that's functional)

### 3.2 Requirements Elicitation Challenges
- Conflicting requirements (different stakeholders want different things)
- Obsolete requirements (requirements become outdated)
- Requirements change (inevitable, needs management)
- Negative stakeholders (resistant or uncooperative)
- **"Negative stakeholders"** is NOT among typical elicitation challenges

### 3.3 Elicitation Techniques
- Interviewing, Survey/questionnaire, Ethnographic study, Observation
- Brainstorming, Document analysis, Prototyping

### 3.4 Requirements Validation
- **Completeness check**: all requirements documented ✓
- **Verifiability**: can the requirement be tested?
- **Realism check**: is it feasible within constraints?
- **Validity check**: does it align with business goals?
- Documenting requirements to check during delivery = **Verifiability** (to reduce disputes)

### 3.5 Requirements Traceability
- Shows dependency between requirements
- Requirements linked to stakeholders who generated them
- Design elements linked back to requirements
- Does NOT trace cost/schedule of every activity

---

## LO4: UML Diagrams (Exam Priority)

### 4.1 Structural vs Behavioral Diagrams
| Type | Diagrams |
|------|----------|
| **Structural** (Static) | Class, Object, Component, Deployment |
| **Behavioral** (Dynamic) | Use Case, Sequence, Activity, State, Collaboration |

### Class Diagram
- Shows: classes, attributes, operations, **multiplicity**, **relationships** (association, inheritance, dependency)
- **Does NOT show**: class instances (that's an object/instance diagram)

### Use Case Diagram
- Shows interactions between **actors** and **system** to accomplish a task
- Represents functional requirements from user perspective

### Activity Diagram
- Shows workflow of events, flow of control from one activity to another
- How the system reacts to internal and external events

### Sequence Diagram
- Shows sequence of interactions required to complete an operation
- Time-ordered messages between objects

### Instance/Object Diagram
- Shows specific **instances** of classes at a particular point in time
- Not used to represent dynamic behavior of an object during analysis → **Instance diagram** is NOT behavioral

### Key Exam Fact: Which UML diagram is NOT used to represent dynamic behavior?
**Instance diagram** — it's structural (static snapshot). Activity, Sequence, and Collaboration are behavioral.

---

## LO5: Software Testing & Quality (High Exam Priority)

### 5.1 Testing Principles
- **Testing early** in development process saves time and cost ✓
- **Exhaustive testing is not possible**
- **Prioritize testing based on risk and criticality**
- Testing the entire development process affects time and cost (but doesn't save it)

### 5.2 Test Levels
| Level | Description |
|-------|-------------|
| **Unit testing** | Individual components in isolation |
| **Integration testing** | Testing combined components work together |
| **System testing** | Testing the complete system |
| **Acceptance testing** | Customer validates requirements (Alpha, Beta) |

### 5.3 Alpha vs Beta Testing
- **Alpha testing**: done by the customer at the developer's site, controlled environment, may result in minor design changes
- **Beta testing**: done by the customer at the customer's own site, real-world environment

### 5.4 Test Process (Fundamental)
1. **Test Analysis & Design**: evaluate testability of requirements and system
2. Test Implementation & Execution
3. Test Evaluation & Reporting
4. Test Closure

### 5.5 Coverage Testing
- **Branch coverage**: selecting program paths to cover branches (edges) of control flow graph
- **Decision coverage**: percentage of decision outcomes tested
- **Statement coverage**: percentage of executable statements executed

#### Decision Coverage Example (AAU 2015 Q22):
```pseudo
if width > length
then biggest_dimension = width
     if height > width
     then biggest_dimension = height
else biggest_dimension = length
     if height > length
     then biggest_dimension = height
```
- **Answer**: 4 tests required for 100% decision coverage (each if-then-else needs both paths)

### 5.6 Test Work Products
- **Test Cases**: input values, execution conditions, expected results
- **Test Reports**: associated with test execution process group

### 5.7 Testing Metrics
- **Precision**: genuine defective segments / total predicted as defective
- **Recall**: genuine defective segments / total actual defective
- **F-measure**: harmonic mean of precision and recall

### 5.8 Purpose of Testing
- **Identifying shortcomings** ✓
- **Improving product acceptance** ✓
- **Enhancing reliability** ✓
- **NOT** requesting more design and implementation time ✗

### 5.9 Who documents faults?
- **Tester** is responsible for documenting faults found during testing

### 5.10 Configuration Management
- Implement configuration management procedures during **test planning**

---

## LO6: Software Architecture

### 6.1 Quality Attributes
- **Performance**: localize critical operations (not distribute them!)
- **Maintainability**: fine-grain, self-contained components, separate producers from consumers
- **Availability**: uptime, fault tolerance
- **Security**: access control, encryption
- **Assessment/evaluation**: using **architectural quality attributes**

### 6.2 Architecture Design Considerations
- Which architectural organization best delivers functional requirements
- How to decompose structural components into sub-components
- How system distributes across cores/processors
- Which architectural patterns/styles to use
- Evaluating architecture parameters: **architectural quality attribute** (not responsiveness, durability, or component count)

### 6.3 Architecture Documentation
Purpose: stakeholder communication, critical system design decisions, understanding organization/interoperation
**Not for**: figuring out source code flow (that's code-level, not architecture)

---

## LO7: Professional Ethics

### 7.1 Ethical Responsibilities
- **Do NOT** accept work regardless of your competence ✗
- Remain up-to-date in your profession ✓
- Respect confidentiality of employers/clients ✓
- Use technical skills responsibly ✓

---

## LO8: Additional Exam Topics from Questions

### 8.1 Risk Management
| Strategy | Description |
|----------|-------------|
| Risk **retention** | Accept the risk, do nothing about it |
| Risk **avoidance** | Change plan to avoid the risk |
| Risk **transfer** | Shift risk to third party (insurance, outsourcing) |
| Risk **reduction** | Take action to reduce probability/impact |

### 8.2 Software Evolution Process (AAU 2015 Q7)
Correct sequence:
1. **Change request** → 2. **Impact analysis** → 3. **Release planning** → 4. **Change implementation** → 5. **System release**

### 8.3 Project Definition
- **Project**: a temporary endeavor undertaken to create a unique product, service, or result
- **Process**: ongoing, repetitive activities
- **Program**: group of related projects
- **Portfolio**: collection of programs/projects

### 8.4 Tuckman's Team Development Model
Order: **Forming → Storming → Norming → Performing → Adjourning**

### 8.5 Coding Standards
- **Code Auditor**: tool used to check code quality against minimum coding standards
- **Structured programming**: disciplined method for readability, maintainability, debug-ability

### 8.6 Project Planning Activities
- Project schedule, cost estimations, work breakdown structures = **Project Planning** process group

### 8.7 CMMI
- Capability Maturity Model Integration: used by software project quality evaluators
- Approach: plan, check, act (continuous improvement)

---

## Exam-Style Q&A (From 63 Actual Model Exam Questions)

**Q1:** Which is NOT among challenges faced during requirement elicitation?
- a. Conflicting requirements
- b. Obsolete requirement
- c. Requirement change
- d. Negative stakeholders ✓

**Q2:** Which testing principle saves time and cost?
- a. Testing the entire development process
- b. Testing early development process ✓
- c. Exhaustive testing is not possible
- d. Prioritize testing based on risk

**Q3:** Which UML diagram is NOT used to represent dynamic behavior?
- a. Activity diagram
- b. Sequence diagram
- c. Instance diagram ✓
- d. Collaboration diagram

**Q4:** Which describes the leading agile development method?
- a. Extreme Programming
- b. Scrum ✓
- c. Sprint
- d. Six Sigma

**Q5:** Validation vs Verification — which ensures product meets customer needs?
- a. SWOT Analysis
- b. Validation ✓
- c. Verification
- d. Variance

**Q6:** Which shows Tuckman's team stages in order?
- a. Forming, Storming, Norming, Performing, Adjourning ✓
- b. Norming, Forming, Storming, Performing, Adjourning
- c. Storming, Forming, Norming, Performing, Adjourning
- d. Forming, Storming, Performing, Norming, Adjourning

**Q7:** Which slogan is AGAINST agile philosophy?
- a. Following a plan over responding to change ✓
- b. Individuals and interactions over processes and tools
- c. Customer collaboration over contract negotiation
- d. Working software over comprehensive documentation

**Q8:** What model delivers different priority modules at different times?
- a. Incremental model ✓
- b. Spiral model
- c. Waterfall model
- d. Linear model

**Q9:** Correct sequence for software evolution?
- a. Change request, impact analysis, release planning, change implementation, system release ✓
- b. Impact analysis, change request, change implementation...
- c. Change request, impact analysis, change implementation, release planning...
- d. Change request, impact analysis, release planning, change implementation, system release

**Q10:** Accepting risk without taking action is called?
- a. Risk transfer
- b. Risk retention ✓
- c. Risk avoidance
- d. Risk reduction

**Q11:** What is NOT a purpose of software testing?
- a. Identifying shortcomings
- b. Improving product acceptance
- c. Enhancing reliability
- d. Requesting more design and implementation time ✓

**Q12:** Which is NOT shown in a class diagram?
- a. Multiplicity
- b. Class instances ✓
- c. Relationships
- d. Operations and attributes

**Q13:** Role of a use case diagram?
- a. Shows interactions among software components
- b. Shows interactions among objects
- c. Shows workflow of events to accomplish a task ✓
- d. None

**Q14:** What is NOT true about non-functional requirements?
- a. Failing to meet them may render system unusable
- b. A single NFR may affect the whole system
- c. NFRs list the features of the system ✓
- d. None

**Q15:** When to implement configuration management procedures?
- a. During test planning ✓
- b. During test closing
- c. During test execution
- d. During test initiation

**Q16:** What evaluates software architectures?
- a. Responsiveness of Architectures
- b. Durability of Architectures
- c. Architectural quality attribute ✓
- d. Number of components

**Q17:** Which is against professional ethics?
- a. Remain up-to-date in your profession
- b. Accept any work regardless of your competence ✓
- c. Respect confidentiality
- d. Use technical skills responsibly

**Q18:** What represents an activity associated with test execution process?
- a. Test Cases
- b. Code
- c. Requirements
- d. Test Reports ✓

**Q19:** What is a temporary endeavor to create a unique product?
- a. Process
- b. Project ✓
- c. Program
- d. Portfolio

**Q20:** How many tests for 100% decision coverage on nested if-else with 2 decisions?
- **Answer**: 4 tests (each of the 2 decisions has True/False → 2×2 paths)
