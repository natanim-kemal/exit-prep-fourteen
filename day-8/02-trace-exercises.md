# Day 8 — Software Engineering Trace Exercises & Problem-Solving (Exam-Style)

## Set 1: Process Model Selection

### Problem 1 — Match Scenario to Model
Which process model fits each scenario?

a) A startup needs to deliver a core MVP quickly, then add features in later releases
b) Safety-critical medical system where risks must be carefully managed at each phase
c) A simple calculator tool with well-known, fixed requirements
d) A web app where requirements change frequently based on user feedback

**Solution:**
a) **Incremental** — deliver core first, add features later
b) **Spiral** — risk-driven, good for safety-critical
c) **Waterfall** — simple, stable requirements
d) **Agile (Scrum)** — flexible, adapts to changing requirements

---

### Problem 2 — Agile vs Waterfall Decision
Your client says: "I need the full budget and timeline approved before any coding starts, and I want a detailed requirements document signed off first."

Which model would you recommend?

**Solution:** **Waterfall** — the client wants fixed scope, time, and cost determined upfront, with signed-off requirements before implementation. Agile would not work because the client doesn't want iterative scope changes.

---

### Problem 3 — Against Agile
Which of the following statements contradicts the Agile Manifesto?
a) "We prioritize working software over comprehensive documentation"
b) "We follow the plan strictly; changes need formal approval"
c) "We collaborate with customers throughout the project"
d) "We value individuals and interactions"

**Solution:** b) — "Following a plan over responding to change" is explicitly against the Agile Manifesto

---

## Set 2: UML Diagram Identification

### Problem 4 — Which Diagram?
Identify the UML diagram from the description:
- a) Shows the sequence of messages between objects over time
- b) Shows the workflow of activities in a process
- c) Shows classes with attributes, operations, and their relationships
- d) Shows how actors interact with system use cases
- e) Shows specific instances of classes at a point in time

**Solution:**
- a) Sequence diagram
- b) Activity diagram
- c) Class diagram
- d) Use case diagram
- e) Instance/Object diagram

---

### Problem 5 — Behavioral vs Structural
Classify each diagram:
1. Class diagram → _________
2. Activity diagram → _________
3. Sequence diagram → _________
4. Instance diagram → _________
5. Use case diagram → _________

**Solution:**
1. Structural
2. Behavioral
3. Behavioral
4. Structural (static snapshot)
5. Behavioral

---

### Problem 6 — Which is NOT behavioral?
Select the UML diagram that does NOT represent dynamic behavior:
a) Activity diagram
b) Sequence diagram
c) Instance diagram
d) Collaboration diagram

**Solution:** c) Instance diagram — it's a structural diagram showing a static snapshot of objects at a specific time.

---

### Problem 7 — Class Diagram Content
Which of the following would you NOT find in a class diagram?
a) Multiplicity (1..*, 0..1)
b) Class instances (specific objects)
c) Relationships (association, inheritance)
d) Operations and attributes

**Solution:** b) Class instances — those belong in an object/instance diagram

---

## Set 3: Requirements Engineering Trace

### Problem 8 — Functional vs Non-Functional
Classify each requirement:
1. "The system shall allow users to reset their password"
2. "The system shall handle 1000 concurrent users"
3. "The system shall be available 99.9% of the time"
4. "The system shall display search results sorted by relevance"

**Solution:**
1. Functional (a feature the system provides)
2. Non-functional (performance constraint)
3. Non-functional (availability constraint)
4. Functional (a specific service/behavior)

---

### Problem 9 — Elicitation Techniques
A project team is having trouble getting clear requirements because stakeholders give conflicting information. Which technique would help most?

**Solution:** **Stakeholder interviews and workshops** (bring stakeholders together to resolve conflicts), or **prototyping** (let stakeholders see and react to a working model)

---

### Problem 10 — Traceability
A developer asks: "I need to know which requirements are affected if I change this database schema." What should the project have maintained?

**Solution:** **Requirements traceability matrix** — links requirements to design elements, code, and tests both forward and backward.

---

## Set 4: Software Testing Trace

### Problem 11 — Test Level Identification
Which test level matches each description?
a) Testing individual functions in isolation
b) Testing that combined modules work together
c) Testing the complete system end-to-end
d) Customer validates the system meets requirements

**Solution:**
a) Unit testing
b) Integration testing
c) System testing
d) Acceptance testing

---

### Problem 12 — Alpha vs Beta
An app company releases a pre-release version to 100 external users who try it on their own devices and report bugs. Is this alpha or beta testing?

**Solution:** **Beta testing** — external users on their own sites/devices. Alpha testing happens at the developer's site with controlled environment.

---

### Problem 13 — Decision Coverage Count
```pseudo
if (a > b)
    x = 1;
    if (c > d)
        y = 2;
    end_if
else
    x = 0;
    if (e > f)
        y = 3;
    end_if
end_if
```
How many test cases needed for 100% decision coverage?

**Trace:**
- Decision 1: a > b (True/False) → 2 branches
- Decision 2: c > d (True/False) → 2 branches (only when a>b is True)
- Decision 3: e > f (True/False) → 2 branches (only when a>b is False)

**Answer:** 4 test cases (True/True, True/False, False/True, False/False)

---

### Problem 14 — Test Reports
After executing a test suite, the tester produces a document summarizing pass/fail status, defect counts, and metrics. What is this called?

**Solution:** **Test Report** — associated with the test execution process group

---

### Problem 15 — Testing Purpose Identification
Which of these is NOT a purpose of testing?
a) Identify defects before release
b) Verify the system meets requirements
c) Increase design and implementation time
d) Improve product reliability

**Solution:** c) Increasing design/implementation time is NOT a purpose of testing

---

### Problem 16 — Who Reports Faults?
A tester finds a critical bug during system testing. Who is responsible for formally documenting this fault?

**Solution:** The **Tester** is responsible for documenting faults found during testing

---

## Set 5: Architecture & Design Trace

### Problem 17 — Quality Attribute Matching
Match the architectural decision to the quality attribute it supports:
1. Localize critical operations → _________
2. Separate data producers from consumers → _________
3. Add redundancy and failover → _________
4. Encrypt all network traffic → _________

**Solution:**
1. Performance
2. Maintainability
3. Availability
4. Security

---

### Problem 18 — Architecture Documentation
Which is NOT a valid purpose for documenting software architecture?
a) Stakeholder communication
b) Figuring out source code flow
c) Recording critical design decisions
d) Understanding system organization and interoperation

**Solution:** b) Figuring out source code flow is NOT an architecture documentation purpose — that's code-level.

---

### Problem 18b — Architectural Style Identification
Match each scenario to the correct architectural style:

1. Nodes act as both clients and servers with no central coordinator → _________
2. Data flows through sequential processing stages like Unix pipes → _________
3. Components communicate via events in a publish/subscribe model → _________
4. Small independent services each deployed separately over a network → _________
5. A central broker mediates requests between clients and servers → _________
6. A shared knowledge base with multiple specialist components → _________

**Solution:**
1. **Peer-to-Peer (P2P)**
2. **Pipe-and-Filter**
3. **Event-Driven**
4. **Microservices**
5. **Broker**
6. **Blackboard**

---

### Problem 18c — Layered Architecture Erosion
Given four layers A (top), B, C, D (bottom). For each relation, state if it causes architectural erosion:

a) Layer A calls a method in layer B → _________
b) Layer D directly accesses a class in layer A → _________
c) Layer A skips B and uses a function in layer C → _________
d) Layer C depends on a service in layer B → _________

**Solution:**
a) **No erosion** — A depends on the layer directly below it ✓
b) **Erosion** — bottom calling top (circular/backward dependency)
c) **Erosion** — layer bridging/skipping (A bypasses B)
d) **Erosion** — reverse dependency (C is below B, should not depend upward)

---

## Set 6: Risk Management & Ethics

### Problem 19 — Risk Strategy Identification
Match the scenario to the risk strategy:
a) Buying cyber insurance → _________
b) Accepting that a minor feature might be cut → _________
c) Using a different technology stack to avoid known security issues → _________
d) Adding automated tests to reduce defect risk → _________

**Solution:**
a) Risk transfer
b) Risk retention
c) Risk avoidance
d) Risk reduction

---

### Problem 20 — Ethics Scenario
A software engineer is asked to sign off on a project she knows has critical security flaws. According to professional ethics, what should she do?

**Solution:** She should **refuse** to sign off and escalate the issue. Accepting work regardless of competence or quality is against professional ethics (from Q11: "Accepting any work regardless of your competence" is unethical).

---

## Set 7: Process & Lifecycle

### Problem 21 — Evolution Process Order
Put these steps in the correct order:
- [ ] Change implementation
- [ ] System release
- [ ] Change request
- [ ] Impact analysis
- [ ] Release planning

**Solution:** Change request → Impact analysis → Release planning → Change implementation → System release

---

### Problem 22 — Project vs Process
Classify each as Project or Process:
a) Developing a new mobile app → _________
b) Daily server backups → _________
c) Building a bridge → _________
d) Monthly payroll processing → _________

**Solution:**
a) Project (temporary, unique)
b) Process (ongoing, repetitive)
c) Project (temporary, unique)
d) Process (ongoing, repetitive)

---

## Common Exam Traps — Software Engineering

| Trap | Explanation |
|------|-------------|
| **Instance diagram** | NOT behavioral — it's structural (static snapshot) |
| **non-functional ≠ features** | NFRs are constraints, NOT system features |
| **defect responsibility** | Tester documents faults, not developer |
| **Agile value "following plan"** | "Following a plan" is the **opposite** of agile |
| **Alpha vs Beta site** | Alpha = developer's site; Beta = customer's site |
| **Evolution order** | Impact analysis comes BEFORE implementation, not after |
| **Risk retention** | Accepting risk and doing nothing = retention, not avoidance |
| **Architecture quality** | Evaluate via quality attributes, not component count |
| **Exception vs tested** | Integration testing is NOT about isolated components |
| **Test reports** | Belong to test execution process group |
| **Decision coverage** | Count each if's True AND False path |
| **CMMI** | Used by quality evaluators, plan-check-act approach |
| **Testing saves cost** | Early testing saves time/cost (not "whole process testing") |
| **NFR single affect** | ONE NFR can affect the WHOLE system |
