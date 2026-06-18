# Software Engineering — Study Notes

## 1. Software Process Models

**Waterfall**: sequential phases (Requirements → Design → Implementation → Testing → Deployment → Maintenance). Simple but inflexible; hard to accommodate changes.

**Agile**: iterative, incremental development with adaptive planning and continuous improvement. Methods: Scrum, XP (Extreme Programming), Kanban.

**Spiral**: iterative risk-driven model. Each iteration has 4 phases: determine objectives, identify risks, develop/test, plan next iteration.

**Incremental model**: system is developed and delivered in increments (each increment adds functionality).

## 2. Requirements Engineering

**Process**: Elicitation → Analysis → Specification → Validation → Management.

**Elicitation techniques**: interviews (in-depth insights from stakeholders), questionnaires, observation, document analysis, brainstorming, prototyping.

**Functional requirements**: describe WHAT the system should do (specific behaviors, functions).

**Non-functional requirements**: describe HOW the system should behave (performance, security, usability, scalability, reliability).

**Well-written functional requirement**: should be testable and measurable.

## 3. Software Design

**Architectural styles**:
- **Layered**: each layer depends only on the layer directly below (OSI, TCP/IP)
- **Client-Server**: server provides services, clients request them
- **Microservices**: small independent services communicating over network
- **Event-Driven**: components communicate via events (publish/subscribe)
- **Peer-to-Peer**: every node is both client and server
- **Pipe-and-Filter**: data flows through sequential processing stages (Unix pipes)
- **MVC**: separates Model (data), View (UI), Controller (logic)
- **Repository**: central data store accessed by all components

**Coupling**: degree of interdependence between modules. Low coupling = good design.
**Cohesion**: degree to which elements within a module are related. High cohesion = good design.
**Principle**: high cohesion + low coupling = good design.

## 4. Testing

**Levels**:
- **Unit Testing**: tests individual components/functions
- **Integration Testing**: tests interactions between modules
- **System Testing**: tests the entire system
- **User Acceptance Testing (UAT)**: tests if system meets user requirements

**Types**:
- **Static testing**: reviews, walkthroughs, inspections (no code execution). Inspection is a formal static test (introduced by Michael Fagan at IBM, 1972).
- **Dynamic testing**: executes code
- **Regression testing**: ensures new code changes don't break existing functionality
- **Smoke testing**: quick initial check of critical functionality
- **Decision coverage**: every branch executed at least once

**Alpha testing**: internal testing by developers.
**Beta testing**: testing by real users in real environment.

## 5. Debugging

Process of identifying and fixing errors in code. Techniques: print statements, breakpoints (pause execution), debugger (step through code), rubber duck debugging, code review.

## 6. Maintenance

**Types**:
- **Corrective**: fixing defects/bugs
- **Adaptive**: adapting to environmental changes (new OS, hardware)
- **Perfective**: improving performance, usability
- **Preventive**: preventing future issues

**Effort estimation**: measured by Function Points (FP), Lines of Code (LOC), or Annual Maintenance Cost (AMC).

## 7. Software Quality

**Key quality attributes**: functionality, reliability, usability, efficiency, maintainability, portability.

**Code smells**: indicators of poor design (long methods, large classes, duplicate code, feature envy, shotgun surgery).

**Refactoring**: improving internal code structure without changing external behavior.

## 8. Ethics & Professional Practice

- Software engineers should act in the public interest
- Maintain confidentiality, professional competence
- Accept responsibility for their work
- Do not accept work beyond their competence
