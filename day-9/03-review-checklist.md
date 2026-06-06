# Day 9 — Software Project Management Review Checklist

## Mastery Checklist

### LO1: SPM Tasks & Fundamentals (2 items)
- [ ] **Project** = temporary + unique product/service/result
- [ ] Project ≠ Process (ongoing/repetitive)
- [ ] Program = group of related projects; Portfolio = collection of programs
- [ ] PM lifecycle: Initiating → Planning → Executing → M&C → Closing
- [ ] **Project Planning** generates: schedule, cost estimates, WBS
- [ ] **Functional organization**: little/no PM authority, little/no resources, functional mgr controls budget
- [ ] **Theory X**: "my way or the highway" (authoritarian)
- [ ] **Theory Y**: assumes workers are self-motivated

### LO2: WBS, Schedule & Cost (4 items)
- [ ] **WBS**: hierarchical decomposition into work packages
- [ ] **Gantt chart**: horizontal axis = **Time Scale**
- [ ] **Critical Path**: longest path, minimum project duration
- [ ] **Slack (Float) = LF - EF** (or LS - ES)
- [ ] **COCOMO**: Effort = **a(KLOC)^b** person-months
- [ ] Modes: Organic (a=2.4,b=1.05), Semi-detached (3.0,1.12), Embedded (3.6,1.20)
- [ ] **Function Point**: based on inputs, outputs, inquiries, files, interfaces
- [ ] **Resource leveling**: adjust dates based on resource constraints
- [ ] **Responsibility Assignment Matrix (RAM)**: maps work to people

### LO3: PM Tools & Techniques (2 items)
- [ ] **ROI = (Gain - Cost) / Cost**
- [ ] **Risk Exposure = Probability of Loss × Size of Loss**
- [ ] **Pareto principle**: 80% of problem → 20% of effort
- [ ] **Affinity diagrams**: groups ideas for analysis
- [ ] **PERT**: Expected = (O + 4M + P) / 6
- [ ] **EVM**: CV = EV-AC, SV = EV-PV, CPI = EV/AC, SPI = EV/PV
- [ ] CPI > 1 = under budget; CPI < 1 = over budget
- [ ] SPI > 1 = ahead schedule; SPI < 1 = behind schedule
- [ ] **Repository** = library of **releases**
- [ ] **Workspace** = library of **promotions**

### LO4: Risk & Quality Management (2 items)
- [ ] Risk response: Avoidance, Transfer, Mitigation, **Acceptance/Retention**
- [ ] Quality = **customer-driven**
- [ ] **CMMI**: plan-check-act, used by quality evaluators
- [ ] **Code Auditor**: checks coding standards
- [ ] QA (process/prevention) vs QC (product/detection)
- [ ] Plan documents: PM Plan, Risk Mgmt Plan, SQA Plan, CM Plan
- [ ] **Testing goal (as QA)**: guarantee software meets specified requirements

---

## Quick Mnemonics

| Concept | Mnemonic |
|---------|----------|
| **COCOMO** | "**a(KLOC) to the b**" — Effort = a(KLOC)^b |
| **Slack** | "**L**ate **F**inish minus **E**arly **F**inish" — LF - EF |
| **ROI** | "**(Gain - Cost) ÷ Cost**" — profit over investment |
| **Risk Exposure** | "**P**robability × **L**oss = **RE**" |
| **Gantt axis** | "Gantt = **G**oing **T**hrough **T**ime" — horizontal = Time |
| **Theory X** | "**X** = e**X**treme boss" — my way or highway |
| **Quality** | "Quality = **C**ustomer says so" |
| **Repository vs Workspace** | "**R**elease = **R**epository; **P**romotion = **W**orkspace" |
| **Pareto** | "80% of bugs from 20% of code" — focus on vital few |
| **Functional org** | "PM has **F**ew rights, **F**unctional manager rules" |

## 1-Page Cram Sheet

```
PROJECT DEFINITION
══════════════════
Project   = temporary + unique
Process   = ongoing + repetitive
Program   = group of projects
Portfolio = group of programs

FORMULAS
════════
COCOMO: Effort = a × (KLOC)^b (person-months)
  Organic: a=2.4, b=1.05
  Semi:    a=3.0, b=1.12
  Embedded: a=3.6, b=1.20

ROI = (Gain - Cost) / Cost × 100%

Slack = LF - EF (or LS - ES)

Risk Exposure = P(Loss) × Size(Loss)

PERT: Expected = (O + 4M + P) / 6

EVM:
  CV = EV - AC (neg = over budget)
  SV = EV - PV (neg = behind)
  CPI = EV / AC (< 1 = over budget)
  SPI = EV / PV (< 1 = behind)
  EAC = BAC / CPI

GANTT: Horizontal axis = Time Scale

TOOLS
═════
Affinity Diagrams → group ideas
Pareto → 80/20 rule
Repository → library of releases
Workspace → library of promotions

RISK
════
Avoidance, Transfer, Mitigation, Acceptance

ORG STRUCTURES
══════════════
Functional: little PM authority
Projectized: full PM authority

QUALITY: Customer driven
CMMI: Plan → Check → Act
```
