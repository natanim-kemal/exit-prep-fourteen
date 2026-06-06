# Day 9 — Software Project Management Trace Exercises & Problem-Solving (Exam-Style)

## Set 1: Formula Trace (Exam Priority!)

### Problem 1 — COCOMO Calculation
Calculate the effort for a 32 KLOC project in organic mode (a=2.4, b=1.05).

**Solution:**
```
Ei = a × (KLOC)^b
Ei = 2.4 × (32)^1.05
log(32) = 1.505
1.05 × 1.505 = 1.580
32^1.05 ≈ 10^1.580 ≈ 38.0
Ei ≈ 2.4 × 38.0 ≈ 91.2 person-months
```

---

### Problem 2 — COCOMO Mode Selection
A safety-critical flight control system with 80 KLOC. Which COCOMO mode? What is the effort estimate?

**Solution:**
- **Embedded mode** (safety-critical, tight constraints): a=3.6, b=1.20
- Ei = 3.6 × (80)^1.20
- log(80) = 1.903, 1.20 × 1.903 = 2.284
- 80^1.20 ≈ 10^2.284 ≈ 192.3
- Ei ≈ 3.6 × 192.3 ≈ **692 person-months**

---

### Problem 3 — ROI Calculation
A project has total discounted benefits of Birr 250,000 and total discounted costs of Birr 200,000. What is the ROI?

**Solution:**
```
ROI = (Gain - Cost) / Cost × 100%
ROI = (250,000 - 200,000) / 200,000 × 100%
ROI = 50,000 / 200,000 × 100%
ROI = 0.25 × 100% = 25%
```

---

### Problem 4 — Slack Calculation
Task A has: ES = day 3, EF = day 8, LS = day 5, LF = day 10
What is the slack?

**Solution:**
```
Slack = LF - EF = 10 - 8 = 2 days
(Slack = LS - ES = 5 - 3 = 2 days ✓)
```
Task A can be delayed up to 2 days without affecting project completion.

---

### Problem 5 — Risk Exposure (RE)
A risk has 40% probability of occurring. If it occurs, the estimated loss is Birr 500,000. What is the Risk Exposure?

**Solution:**
```
RE = Probability of Loss × Size of Loss
RE = 0.40 × 500,000 = Birr 200,000
```

---

### Problem 6 — EVM Trace
Given: PV = Birr 50,000, EV = Birr 40,000, AC = Birr 45,000, BAC = Birr 100,000

Calculate: CV, SV, CPI, SPI, EAC

**Solution:**
```
CV = EV - AC = 40,000 - 45,000 = -5,000 (over budget)
SV = EV - PV = 40,000 - 50,000 = -10,000 (behind schedule)
CPI = EV / AC = 40,000 / 45,000 = 0.89 (< 1, over budget)
SPI = EV / PV = 40,000 / 50,000 = 0.80 (< 1, behind schedule)
EAC = BAC / CPI = 100,000 / 0.89 = Birr 112,360
```

---

### Problem 7 — EVM Interpretation
If CPI = 1.2 and SPI = 0.9, what is the project status?

**Solution:**
- CPI = 1.2 > 1 → **under budget** (getting more value for each birr spent)
- SPI = 0.9 < 1 → **behind schedule** (less work completed than planned)

---

## Set 2: Gantt & Scheduling Trace

### Problem 8 — Gantt Chart
```
Task A:   ████████ (days 1-8)
Task B:      ████████ (days 5-12)
Task C:         ██████ (days 9-14)
```
a) What is the horizontal axis?
b) Which tasks overlap?
c) What is the total project duration?

**Solution:**
a) Time Scale (days)
b) A overlaps with B (days 5-8); B overlaps with C (days 9-12)
c) 14 days

---

### Problem 9 — Critical Path
Three parallel paths:
- Path 1: A(3d) → B(4d) → C(2d) = 9 days
- Path 2: D(5d) → E(3d) = 8 days
- Path 3: F(6d) → G(1d) = 7 days

a) What is the critical path?
b) What is the minimum project duration?
c) What is the slack on Path 3?

**Solution:**
a) Path 1 (A→B→C) = 9 days (longest)
b) 9 days
c) Slack = 9 - 7 = 2 days (Path 3 can be delayed 2 days)

---

## Set 3: Process Model & Project Type

### Problem 10 — Identify Project Type
Classify each as Project or Process:
a) Writing monthly expense reports → _________
b) Developing a new e-commerce website → _________
c) Conducting daily standup meetings → _________
d) Migrating company data to a new server → _________

**Solution:**
a) Process (ongoing, repetitive)
b) Project (temporary, unique)
c) Process (ongoing, routine)
d) Project (temporary, unique deliverable)

---

### Problem 11 — Process Model Match
"Successive phases repeated sequentially with no feedback loops" describes which process model?

**Solution:** **Incremental** model — from SPM Model Q1: "Incremental" has dependent phases repeated sequentially with no feedback loops

---

## Set 4: Quality & Risk

### Problem 12 — Pareto Principle
A support team logs 100 bugs. 20 bugs account for 85% of customer complaints. What principle applies?

**Solution:** **Pareto Principle** (80/20 rule) — 80% of the problem is caused by 20% of the defects. Fix the 20 most impactful bugs first.

---

### Problem 13 — Risk Response Strategy
Match:
1. Buy insurance → _________
2. Accept the risk without action → _________
3. Change technology to avoid risk → _________
4. Add automated tests → _________

**Solution:**
1. Risk transfer
2. Risk retention
3. Risk avoidance
4. Risk reduction/mitigation

---

### Problem 14 — Quality Ownership
A QA manager says: "Quality is the responsibility of the testers." Is this correct?

**Solution:** No. Quality is **customer-driven** (SPM Model Q8). While QA/QC processes support quality, ultimately quality is defined by whether the product meets customer needs. Everyone on the team contributes to quality.

---

## Set 5: Organizational Structure

### Problem 15 — Structure Identification
In Company A, the project manager has no authority to hire team members. Resources are shared across departments, and the functional manager controls the project budget. What organizational structure is this?

**Solution:** **Functional organization** — little/no PM authority, functional manager controls budget, limited resource availability

---

### Problem 16 — Leadership Style
A manager says: "My way or the highway — if you don't like it, leave." Which leadership theory?

**Solution:** **Theory X** — assumes workers need coercion and direction

---

## Set 6: Estimation & Planning

### Problem 17 — WBS Level
A project has: Level 0 = "E-commerce Platform", Level 1 = "Frontend", "Backend", "Database", "Deployment". What is this called?

**Solution:** Work Breakdown Structure (WBS) — a hierarchical decomposition of deliverables

---

### Problem 18 — PERT Estimate
A task has: Optimistic = 5 days, Most Likely = 8 days, Pessimistic = 17 days. What is the expected duration?

**Solution:**
```
Expected = (O + 4M + P) / 6
Expected = (5 + 4×8 + 17) / 6
Expected = (5 + 32 + 17) / 6
Expected = 54 / 6 = 9 days
```

---

### Problem 19 — Affinity Diagram Scenario
A project team brainstormed 200 feature ideas. They need to organize them into meaningful groups for prioritization. Which technique?

**Solution:** **Affinity Diagrams** — classifies large numbers of ideas into groups for review and analysis

---

### Problem 20 — Repository vs Workspace
Which is which?
a) Contains approved baselines, accessible to all team members → _________
b) Individual developer's working area for daily changes → _________

**Solution:**
a) Repository (library of releases)
b) Workspace (library of promotions)

---

## Common Exam Traps — Software Project Management

| Trap | Explanation |
|------|-------------|
| **COCOMO formula** | Ei = **a(KLOC)^b** — NOT b(KLOC)^a or a×KLOC×b |
| **Slack formula** | **LF - EF** (or LS - ES) — NOT ES-LS or LS-EF |
| **ROI formula** | **(Gain - Cost) / Cost** — denominator is COST, not gain |
| **Gantt horizontal** | **Time Scale** — NOT persons, cost, or scope |
| **Risk Exposure** | **Probability of Loss × Size of Loss** — NOT probability × size of risk |
| **Resource leveling** | Adjusts dates based on **resource constraints** to balance demand/supply |
| **Repository** | Library of **releases** (NOT task sets, milestones, or work products) |
| **Workspace** | Library of **promotions** (NOT static/dynamic space) |
| **Theory X** | "My way or the highway" — authoritarian |
| **Quality owner** | **Customer-driven** — not analyst, tester, or developer-driven |
| **Functional org** | Little/no PM authority, functional manager controls budget |
| **Pareto** | 80% of problem → 20% of effort |
| **Affinity diagrams** | Groups ideas (not scheduling/PERT) |
| **Project definition** | Temporary + unique product (not ongoing process) |
| **Project Planning** | Generates schedule + cost estimates + WBS |
