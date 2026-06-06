# Day 8 — Software Engineering Review Checklist

## Mastery Checklist

### SE Principles (3 items)
- [ ] 4 fundamental SE activities: Spec → Design/Impl → Validation → Evolution
- [ ] Design principles: traceable to analysis, accommodate change, uniform, don't reinvent
- [ ] Modularity, high cohesion (good), low coupling (good)

### Process Models (3 items)
- [ ] **Waterfall**: sequential, fixed scope/time/cost upfront, stable requirements
- [ ] **Incremental**: different priority modules at different times, successive iterations
- [ ] **Agile (Scrum/XP)**: individuals & interactions, working software, customer collaboration, **responding to change**
- [ ] **Agile Manifesto**: what is AGAINST agile = "following a plan over responding to change"
- [ ] **Spiral**: risk-driven, iterative cycles with risk analysis
- [ ] **Prototyping**: scaled-down version to demonstrate/test aspects
- [ ] Scrum: leading agile method; Sprints (2-4 week iterations)
- [ ] Tuckman's stages: **Forming → Storming → Norming → Performing → Adjourning**

### Requirements Engineering
- [ ] Functional = what system does (features/services)
- [ ] Non-functional = constraints (performance, security, etc.)
- [ ] NFRs: failing may make system unusable; one NFR affects whole system
- [ ] Elicitation challenges: conflicting, obsolete, changing requirements
- [ ] Negative stakeholders is NOT a typical challenge
- [ ] Validation: completeness, verifiability, realism, validity
- [ ] Traceability: links requirements ↔ design ↔ tests (NOT cost/schedule)

### UML Diagrams
- [ ] **Class diagram**: classes, attributes, operations, multiplicity, relationships
- [ ] **NOT in class diagram**: class instances (object diagram)
- [ ] **Use case**: workflow of events for a task (actor-system interaction)
- [ ] **Activity**: workflow, flow of control
- [ ] **Sequence**: time-ordered interactions for an operation
- [ ] **Instance**: structural (static snapshot) — NOT behavioral
- [ ] **Behavioral**: Activity, Sequence, Use Case, Collaboration, State
- [ ] **Structural**: Class, Object/Instance, Component, Deployment

### Software Testing
- [ ] **Early testing** saves time and cost
- [ ] **Exhaustive testing impossible**
- [ ] Levels: Unit → Integration → System → Acceptance
- [ ] **Alpha**: at developer's site; **Beta**: at customer's site
- [ ] **Integration testing**: proves components work together
- [ ] **Test Reports**: associated with test execution
- [ ] **Tester** documents faults
- [ ] **Decision coverage**: count True/False paths for each decision
- [ ] Testing purposes: identify shortcomings, improve acceptance, enhance reliability
- [ ] NOT a purpose: requesting more design/implementation time

### Software Architecture
- [ ] Evaluate via **architectural quality attributes**
- [ ] **Performance**: localize critical operations
- [ ] **Maintainability**: fine-grain, self-contained, separate producers/consumers
- [ ] Architecture documentation: stakeholder communication, design decisions, system organization
- [ ] NOT for: figuring out source code flow

### Professional Ethics
- [ ] DO NOT accept work beyond your competence
- [ ] DO stay up-to-date, respect confidentiality, use skills responsibly

### Bonus (from exam questions)
- [ ] **Risk retention**: accept risk, do nothing
- [ ] **Risk transfer**: insurance/outsourcing
- [ ] **Risk avoidance**: change plan to avoid
- [ ] **Risk reduction**: mitigate impact
- [ ] **Software evolution**: Change request → Impact analysis → Release planning → Change implementation → System release
- [ ] **Project definition**: temporary, unique product/service
- [ ] **Code Auditor**: tool for checking coding standards
- [ ] **CMMI**: plan-check-act, quality evaluation
- [ ] **Configuration management**: implement during test planning
- [ ] **Project Planning**: generates schedule, cost estimates, WBS

---

## Quick Mnemonics

| Concept | Mnemonic |
|---------|----------|
| **Tuckman's stages** | "**F**orming **S**torming **N**orming **P**erforming **A**djourning" — "**F**ive **S**tages **N**ever **P**ause **A**t-work" |
| **Evolution order** | "**C**hange → **I**mpact → **R**elease → **C**ode → **S**hip" — C-I-R-C-S |
| **Agile value** | "**R**espond to change, don't **F**ollow the plan blindly" |
| **Instance diagram** | "Instance = **I**mmobile snapshot (structural)" |
| **Alpha vs Beta** | "Alpha = **A**uthor's site, Beta = **B**uyer's site" |
| **Risk retention** | "**R**etention = **R**elax, do nothing" |
| **Decision coverage** | "Each **if** has **two** faces — True and False" |
| **Testing saves** | "**E**arly testing saves **E**verything" |
| **NFR ≠ features** | "Non-functional is **NOT** feature listing" |
| **Architecture evaluation** | "Quality **A**ttributes, not **Q**uantity of parts" |

## 1-Page Cram Sheet

```
PROCESS MODELS
══════════════
Waterfall  → sequential, fixed, stable reqs
Incremental → diff priority, successive adds
Agile      → respond to change, customer collab
Spiral     → risk-driven, iterative

AGILE MANIFESTO (value left, but value RIGHT more)
  Individuals & interactions  > processes & tools
  Working software            > comprehensive docs
  Customer collaboration      > contract negotiation
  Responding to change        > following a plan ✓

UML DIAGRAMS
════════════
STRUCTURAL: Class, Object/Instance, Component
BEHAVIORAL: Use Case, Activity, Sequence, State

Instance = structural (NOT behavioral!)

TESTING
═══════
Principles: Early saves cost, Exhaustive impossible
Levels: Unit → Integration → System → Acceptance
Coverage: Branch (edges), Decision (if-true/false)

ARCHITECTURE
════════════
Evaluate: Quality attributes
Performance → localize critical ops
Maintainability → separate producers/consumers

RISK: Retention (do nothing), Transfer (insure),
      Avoidance (avoid), Reduction (mitigate)

EVOLUTION: Change → Impact → Release → Code → Ship

ETHICS: Don't accept work beyond competence!
```
