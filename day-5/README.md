# Day 5 — Fundamentals of Databases (7 Items)

## Files in this directory

| File | Content |
|------|---------|
| `01-databases-complete.md` | Full theory: database approach vs file systems, ER model, relational model, SQL (SELECT/JOIN/INSERT/GROUP BY), normalization (1NF/2NF/3NF/BCNF), ACID transactions, database security + 15 exam Q&As |
| `02-trace-exercises.md` | 20 exam-style problems: SQL query writing (4 schemas), normalization identification/decomposition, ER diagram cardinality, transaction trace with lost update, SQL error detection, schema design |
| `03-review-checklist.md` | Mastery checklist, mnemonics, 1-page cram sheet |

## How to use today

1. **Read** `01-databases-complete.md` (2 hrs) — pay extra attention to: INSERT syntax, JOIN queries, normalization (2NF is the exam favorite), FOREIGN KEY with CASCADE
2. **Practice** `02-trace-exercises.md` (1.5 hrs) — write the SQL queries by hand, normalize the relations
3. **Self-test** `03-review-checklist.md` (30 min)

## Key exam focus (from actual model exams)

- **INSERT syntax** — correct column list + VALUES
- **JOIN queries** — HOTEL/ROOM/BOOKING/GUEST schema appears multiple times
- **Normalization** — identifying normal form from constraints (no multivalued + no partial = 2NF)
- **Database design sequence** — Enterprise → Logical → Physical → Implementation
- **Foreign key constraints** — REFERENCES, ON UPDATE CASCADE
- **DISTINCT** — eliminates duplicate tuples
- **Database approach features** — what is NOT a feature (application-data dependency)
- **Primary key must be NOT NULL**
- **Participation** — total vs partial (every DORM must have student = total participation by DORM)

## Next: Day 6 — Web Programming (10 items)
