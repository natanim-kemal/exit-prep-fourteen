# Day 8 — Fundamentals of Software Engineering (92 Items)

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

### 6.4 Architectural Styles & Patterns

| Style | How it works | Example | Erosion Risk |
|-------|-------------|---------|:------------:|
| **Layered** | Each layer depends only on the one directly below | OSI model, Spring Boot, TCP/IP | High — layer skipping/bridging |
| **Peer-to-Peer (P2P)** | Every node is both client and server; no central coordinator | BitTorrent, blockchain, Skype | Low — no hierarchy to violate |
| **Client-Server** | Centralized server, multiple clients request services | Web apps (browser ←→ server) | Medium — server coupling |
| **Master-Slave** | One master assigns work to replicated slaves | Database replication (primary → replicas) | Medium — single point of failure |
| **Pipe-and-Filter** | Data flows through sequential processing stages | Unix pipes, compilers (lexer → parser → code gen) | Low — well-defined interfaces |
| **Event-Driven** | Components communicate via events (publish/subscribe) | GUI frameworks, Kafka, Node.js EventEmitter | Low — loose coupling by design |
| **Microservices** | Small independent services communicating over network | Netflix, Uber, Amazon | Medium — network/contract drift |
| **Model-View-Controller (MVC)** | Separates data (Model), UI (View), and logic (Controller) | Django, Rails, Spring MVC | Medium — controller bloat |
| **Repository** | Central data store accessed by all components | Database-backed apps | High — single point of coupling |
| **Blackboard** | Shared knowledge base, multiple specialists read/write | AI expert systems | Low — independent specialists |
| **Broker** | Central broker mediates between clients and servers | CORBA, message queues | Medium — broker becomes bottleneck |
| **Service-Oriented (SOA)** | Loosely coupled services via protocols | Enterprise SOAP/XML systems | Medium — service contract versioning |

#### Architectural Erosion Defined
**Architectural erosion**: the gradual degradation of a system's intended structure when code-level dependencies violate the designed architecture.

**In layered architectures specifically**:
- Correct: `(A,B)` — layer A depends on the layer directly below (B) ✓
- Erosion: `(D,A)` — bottom calls top (circular/backward dependency) ✗
- Erosion: `(A,C)` — layer A skips B and calls C directly (layer bridging) ✗
- Erosion: `(C,B)` — lower layer calls upper layer (reverse dependency) ✗

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


## Practice Questions (from Question Bank)

Answer: A
### Q744. When designing for high performance, waterfall model main drawback?

- A) Inflexible
- B) Only for small projects
- C) No testing phase
- D) Too iterative
  **Answer: A**

### Q745. Which statement about Validation is correct?

- A) Meets specification
- B) Test coverage adequate
- C) Meets actual user needs
- D) Syntax correct
  **Answer: C**

### Q746. Adaptive maintenance is for?

- A) Performance improvements
- B) New OS/environment changes
- C) Bug fixes
- D) Future bug prevention
  **Answer: B**

### Q747. When designing for high performance, sRS purpose?

- A) Lists bugs found
- B) Provides user manual
- C) Documents source code
- D) Formally documents
  **Answer: C**

### Q748. Observer pattern category?

- A) Behavioural
- B) Creational
- C) Structural
- D) Architectural
  **Answer: B**

### Q749. Open/Closed Principle says?

- A) Open to modification, closed to
- B) Open to extension, closed to
- C) Interfaces closed, abstract open
- D) All methods public
  **Answer: A**

### Q750. In a resource-constrained environment, white-box testing has access to?

- A) Performance benchmarks
- B) I/O only
- C) User criteria only
- D) Internal code structure
  **Answer: B**

### Q751. Spiral model is driven by?

- A) Risk analysis each cycle
- B) Sequential phases
- C) Customer feedback
- D) Time-boxed sprints
  **Answer: A**

### Q752. Layered architecture separates?

- A) Modules by language
- B) Frontend and backend always
- C) Client and server
- D) Presentation, business
  **Answer: D**

### Q753. Identify the correct statement about verification in testing.

- A) Performance meets benchmarks
- B) Meets specification — are we
- C) Code has no syntax errors
- D) Meets user needs
  **Answer: C**

### Q754. Unit testing tests?

- A) User acceptance
- B) Integration between
- C) Individual functions/clas
- D) Whole system
  **Answer: B**

### Q755. Integration testing tests?

- A) Individual functions
- B) Interaction between
- C) User acceptance
- D) Full system against
  **Answer: A**

### Q756. When designing for high performance, system testing tests?

- A) Complete integrated system
- B) Individual units
- C) Module interactions
- D) User workflows only
  **Answer: A**

### Q757. Acceptance testing is done by?

- A) Developers
- B) End users/clients
- C) QA team alone
- D) Testers only
  **Answer: C**

### Q758. Agile values working software over?

- A) Customer collaboration
- B) Individuals and interactions
- C) Responding to change
- D) Comprehensive documentation
  **Answer: A**

### Q759. When designing for high performance, scrum Sprint duration?

- A) 1 month always
- B) 1 week
- C) 3-6 months
- D) 2-4 weeks
  **Answer: D**

### Q760. Scrum Master role?

- A) Developer team lead
- B) Product decision maker
- C) Customer representative
- D) Facilitator removing
  **Answer: D**

### Q761. Product Owner responsibility?

- A) Team facilitation
- B) Technical architecture
- C) Daily standup facilitation
- D) Managing product backlog and
  **Answer: C**

### Q762. How is Xp (extreme programming) practice: tdd best characterized?

- A) Test-Driven Development —
- B) Type-Driven Design
- C) Test Data Development
- D) Technology-Driven Design
  **Answer: B**

### Q763. Identify the correct statement about pair programming.

- A) Two programs running
- B) Parallel testing
- C) Code review process
- D) Two developers working
  **Answer: B**

### Q764. Identify the correct statement about continuous integration.

- A) Frequently merging code to shared
- B) Continuous refactoring
- C) Continuous customer meetings
- D) Continuous deployment only
  **Answer: D**

### Q765. Consider a system where which description of technical debt is accurate?

- A) Cost of shortcuts/quick
- B) Outdated technology
- C) Financial cost of software
- D) Poor test coverage
  **Answer: B**

### Q766. Which of the following best describes use case?

- A) Description of system
- B) Source code example
- C) Deployment diagram
- D) Test case
  **Answer: C**

### Q767. Identify the correct statement about n actor in use case modeling.

- A) Database table
- B) System component
- C) Animated UI element
- D) External entity interacti
  **Answer: B**

### Q768. In a resource-constrained environment, which statement about Software reliability is correct?

- A) Software is fast
- B) Software is secure
- C) Probability of failure-fre
- D) Software is maintainable
  **Answer: C**

### Q769. Cyclomatic complexity measures?

- A) Number of classes
- B) Number of linearly
- C) Lines of code
- D) Memory usage
  **Answer: B**

### Q770. Identify the correct statement about refactoring.

- A) Adding new features
- B) Fixing bugs
- C) Restructuring code without
- D) Rewriting from scratch
  **Answer: C**

### Q771. Which of the following best describes difference between fault, error, and failure?

- A) All mean wrong output
- B) Fault=defect in code
- C) Fault is hardware
- D) No difference
  **Answer: C**

### Q772. Black-box testing is also called?

- A) Clear-box testing
- B) Unit testing
- C) Structural testing
- D) Functional testing
  **Answer: A**

### Q773. Grey-box testing combines?

- A) Unit and system testing
- B) Functional and performance testing
- C) Black-box and white-box testing
- D) Manual and automated testing
  **Answer: B**

### Q774. When designing for high performance, which description of regression testing is accurate?

- A) Testing on older hardware
- B) Testing new features
- C) Testing old versions
- D) Re-testing after changes to
  **Answer: C**

### Q775. Identify the correct statement about smoke testing.

- A) Quick basic test to check if
- B) Testing under heavy load
- C) Stress testing
- D) Testing security vulnerabilities
  **Answer: C**

### Q776. Which description of load testing is accurate?

- A) Testing system under
- B) Testing file loading
- C) Testing hardware limits
- D) Loading test data
  **Answer: B**

### Q777. Consider a system where identify the correct statement about stress testing.

- A) Testing beyond normal capacity
- B) Performance benchmarking
- C) Testing developer stress
- D) Load testing synonym
  **Answer: C**

### Q778. Identify the correct statement about software architecture.

- A) High-level structure of
- B) Source code organization
- C) Database schema
- D) Physical building for developers
  **Answer: B**

### Q779. Microservices architecture characteristics?

- A) Layered architecture variant
- B) Single deployable monolith
- C) Small independent services
- D) Client-server pattern only
  **Answer: A**

### Q780. Which of the following best describes coupling in software design?

- A) Measure of class size
- B) Degree of interdependence
- C) Inheritance depth
- D) Number of methods
  **Answer: B**

### Q781. Which of the following best describes cohesion in software design?

- A) Code comments quality
- B) Test coverage
- C) Degree to which elements
- D) Module dependencies
  **Answer: A**

### Q782. Which of the following best describes Facade design pattern?

- A) Hides object creation
- B) Provides simple interface to
- C) Converts interfaces
- D) Adds behavior to objects
  **Answer: B**

### Q783. When designing for high performance, which description of Adapter design pattern is accurate?

- A) Adds new behavior
- B) Decomposes composite
- C) Converts incompatible
- D) Provides simplified
  **Answer: A**

### Q784. Identify the correct statement about Template Method pattern.

- A) Defines skeleton algorithm in
- B) Creates objects without
- C) Handles events
- D) Manages single instance
  **Answer: D**

### Q785. Which of the following best describes Strategy pattern?

- A) Chain handlers
- B) Define family of algorithms
- C) Single fixed algorithm
- D) Encapsulate request as object
  **Answer: C**

### Q786. Consider a system where which description of version control's purpose is accurate?

- A) Compile source code
- B) Deploy software
- C) Track changes, enable
- D) Control software licensing
  **Answer: C**

### Q787. What does git commit do?

- A) Downloads remote changes
- B) Records snapshot of staged
- C) Merges branches
- D) Sends changes to server
  **Answer: C**

### Q788. What does git push do?

- A) Creates new branch
- B) Sends local commits to
- C) Downloads remote changes
- D) Stages files
  **Answer: A**

### Q789. When designing for high performance, what does git pull do?

- A) Pushes changes
- B) Creates branch
- C) Downloads and merges
- D) Commits changes
  **Answer: D**

### Q790. Which of the following best describes pull request in git workflow?

- A) Code backup request
- B) Git pull command
- C) Proposing changes from
- D) Requesting others to pull
  **Answer: A**

### Q791. Which description of branching in git is accurate?

- A) Splitting project into
- B) Copying repository
- C) Forking project
- D) Creating parallel
  **Answer: C**

### Q792. When designing for high performance, identify the correct statement about software quality.

- A) Code length
- B) Number of features
- C) Development speed
- D) Degree of excellence:
  **Answer: B**

### Q793. Corrective maintenance is?

- A) Improving performance
- B) Fixing bugs after deployment
- C) Adapting to new environment
- D) Preventing future bugs
  **Answer: D**

### Q794. Perfective maintenance is?

- A) Preventing bugs
- B) Improving performance/usa
- C) New environment adaptatio
- D) Fixing bugs
  **Answer: A**

### Q795. Consider a system where preventive maintenance is?

- A) Adapting to new OS
- B) Restructuring/cleaning
- C) Fixing current bugs
- D) Adding new features
  **Answer: C**

### Q796. Identify the correct statement about legacy system.

- A) Old system that no longer works
- B) System using old programming language
- C) Unmaintained abandoned system
- D) Old system still in use, costly to
  **Answer: D**

### Q797. Which description of software entropy is accurate?

- A) Software performance
- B) Memory fragmentation
- C) Data corruption
- D) Tendency for software to
  **Answer: A**

### Q798. Identify the correct statement about agile manifesto's first value.

- A) Responding to change over following a plan
- B) Working software over comprehensive documentation
- C) Individuals and interactions over processes and tools
- D) Customer collaboration over contract negotiation
  **Answer: C**

### Q799. Which description of sprint backlog is accurate?

- A) List of bugs
- B) All product features
- C) Set of items from
- D) Release plan
  **Answer: A**

### Q800. Which of the following best describes product backlog?

- A) Prioritized list of all
- B) Sprint plan
- C) List of bugs to fix
- D) Test cases
  **Answer: B**

### Q801. Consider a system where identify the correct statement about velocity in Scrum.

- A) Development speed in LOC
- B) Deployment frequency
- C) Bug fix rate
- D) Amount of work team
  **Answer: B**

### Q802. Which of the following best describes burndown chart?

- A) Bug tracking chart
- B) Chart showing remaining work
- C) Team performance review
- D) Server performance chart
  **Answer: C**

### Q803. RAD (Rapid Application Development) emphasizes?

- A) Formal documentation
- B) Prototyping and fast delivery
- C) Risk-driven development
- D) Detailed upfront planning
  **Answer: D**

### Q804. When designing for high performance, which description of V-Model is accurate?

- A) Visual modeling method
- B) Version control model
- C) Waterfall variant with
- D) Agile framework
  **Answer: C**

### Q805. Which description of incremental development is accurate?

- A) Delivering system in increments
- B) Delivering all at once
- C) Risk-driven phases
- D) Iterative refinement only
  **Answer: A**

### Q806. Identify the correct statement about prototype in software development.

- A) Architecture diagram
- B) Final product
- C) Test case
- D) Early model to explore
  **Answer: C**

### Q807. Which of the following best describes throwaway prototyping?

- A) Prototype built to explore
- B) Minimal viable product
- C) Prototype that becomes final
- D) Quick bug fix
  **Answer: D**

### Q808. Which of the following best describes evolutionary prototyping?

- A) Prototype discarded after use
- B) Architecture prototype
- C) Prototype for performance testing
- D) Prototype refined and evolved into
  **Answer: A**

### Q809. Which of the following best describes purpose of code review?

- A) Generate test cases
- B) Peer examination of code to
- C) Deploy code to production
- D) Manage code repositories
  **Answer: A**

### Q810. In a resource-constrained environment, which of the following best describes static analysis?

- A) Examining source code without
- B) Security penetration testing
- C) Analysis of running program
- D) Performance profiling
  **Answer: D**

### Q811. Which of the following best describes dynamic analysis?

- A) Code review
- B) Examining code without
- C) Analyzing program behavior
- D) Formal verification
  **Answer: B**

### Q812. Which of the following best describes Model-Driven Development (MDD)?

- A) Machine learning in development
- B) Database-driven development
- C) Pattern-driven development
- D) Using models as primary artifacts
  **Answer: C**

### Q813. In a resource-constrained environment, which of the following best describes Kanban methodology?

- A) Continuous flow visualization
- B) Pair programming methodology
- C) Risk-driven development
- D) Fixed-length sprints
  **Answer: A**

### Q814. Which of the following best describes definition of done (DoD) in Scrum?

- A) Customer accepts feature
- B) Product is shipped
- C) Sprint is over
- D) Shared checklist criteria
  **Answer: C**

### Q815. Identify the correct statement about user story in Agile.

- A) Short description of
- B) User documentation
- C) Bug report
- D) Test case
  **Answer: D**

### Q816. When designing for high performance, which description of story point estimation is accurate?

- A) Estimating time in hours
- B) Bug severity score
- C) Relative complexity measure for
- D) Points earned by developers
  **Answer: B**

### Q817. Which of the following best describes planning poker?

- A) Requirement gathering technique
- B) Casino game for developers
- C) Collaborative estimation
- D) Risk assessment game
  **Answer: C**

### Q818. Which of the following best describes continuous delivery (CD)?

- A) Continuous code writing
- B) Daily deployments always
- C) Keeping software always in
- D) Continuous integration only
  **Answer: A**

### Q819. Identify the correct statement about Infrastructure as Code (IaC).

- A) Hardware programming
- B) Network configuration management
- C) Writing infrastructure documentation
- D) Managing infrastructure using
  **Answer: D**

### Q820. Which description of DevOps is accurate?

- A) Security operations
- B) Culture/practice unifying
- C) Development operations research
- D) IT department methodology
  **Answer: C**

### Q821. Which description of software metric is accurate?

- A) Performance benchmark
- B) Quantitative measure of
- C) Bug classification
- D) Software measurement unit
  **Answer: A**

### Q822. When designing for high performance, which of the following best describes CASE tool?

- A) Court case management
- B) Code analysis security engine
- C) Case sensitivity tool
- D) Computer-Aided Software
  **Answer: B**

### Q823. Identify the correct statement about formal verification.

- A) Standard compliance testing
- B) Mathematically proving
- C) Official testing
- D) End user certification
  **Answer: D**

### Q824. Identify the correct statement about model checking.

- A) ML model evaluation
- B) Automated verification
- C) Reviewing UML models
- D) Checking model accuracy
  **Answer: B**

### Q825. When designing for high performance, which description of fault tolerance is accurate?

- A) User error handling
- B) Accepting poor quality
- C) Bug tolerance in code
- D) System's ability to continue
  **Answer: C**

### Q826. Identify the correct statement about purpose of IEEE standards in SE.

- A) Mandate specific languages
- B) Provide standardized
- C) Replace agile methods
- D) Speed up development
  **Answer: D**

### Q827. Which description of CMMI is accurate?

- A) Capability Maturity Model Integration —
- B) Continuous Metrics Monitoring Integration
- C) Computer Maintenance Management Interface
- D) Code Management Maturity Index
  **Answer: B**

### Q828. Consider a system where how is Cmmi level 1 (initial) best characterized?

- A) Processes are measured
- B) Processes are managed
- C) Processes are defined
- D) Processes unpredictable
  **Answer: B**

### Q829. Which statement about Cmmi level 5 (optimizing) is correct?

- A) Continuous process
- B) Processes defined
- C) Processes are initial
- D) Processes quantitatively
  **Answer: D**

### Q830. Which of the following best describes ISO 9001?

- A) Network security standard
- B) Quality management systems standard
- C) Programming language standard
- D) Database standard
  **Answer: A**

### Q831. When designing for high performance, which description of goal of SQA is accurate?

- A) Find and fix bugs
- B) Write test cases
- C) Ensure quality processes
- D) Deploy software
  **Answer: A**

### Q832. Which of the following best describes defect density?

- A) Number of defects per unit of
- B) Test coverage percentage
- C) Number of testers per module
- D) Severity of defects
  **Answer: C**

### Q833. Identify the correct statement about test coverage.

- A) Number of testers
- B) Number of test cases
- C) Test execution time
- D) Percentage of code/requirem
  **Answer: D**

### Q834. When designing for high performance, which of the following best describes mutation testing?

- A) Deliberately introducing faults to
- B) Testing database mutations
- C) Testing in different environments
- D) Testing modified requirements
  **Answer: B**

### Q835. Identify the correct statement about exploratory testing.

- A) Simultaneous learning
- B) Testing all code paths
- C) Automated regression testing
- D) Load testing variants
