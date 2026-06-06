# Day 5 — Databases Review Checklist

## Mastery Checklist

### Database Fundamentals
- [ ] Definition: logically coherent collection of data with inherent meaning
- [ ] Database approach features (self-describing, abstraction, multiple views, sharing)
- [ ] Application-data dependency is a file system problem, NOT database
- [ ] Three-schema architecture (external, conceptual, internal)
- [ ] Data independence (logical + physical)

### ER Model
- [ ] Entity, Attribute (simple/composite/multi-valued/derived/key), Relationship
- [ ] Cardinality: 1:1, 1:N, M:N
- [ ] Participation: total vs partial
- [ ] Weak entity (existence dependency)

### Relational Model
- [ ] Relation, tuple, attribute, domain, schema
- [ ] Primary key (NOT NULL, unique, stable)
- [ ] Foreign key (references PK, can be NULL)
- [ ] Entity integrity (PK ≠ NULL)
- [ ] Referential integrity (FK = PK value or NULL)
- [ ] ON UPDATE/DELETE CASCADE, SET NULL, RESTRICT

### SQL
- [ ] SELECT ... FROM ... WHERE ... GROUP BY ... HAVING ... ORDER BY
- [ ] INSERT INTO table (cols) VALUES (vals)
- [ ] UPDATE table SET col = val WHERE condition
- [ ] DELETE FROM table WHERE condition
- [ ] JOIN (INNER, LEFT, RIGHT) with ON condition
- [ ] DISTINCT eliminates duplicates
- [ ] Aggregate: COUNT, SUM, AVG, MIN, MAX
- [ ] LIKE: `%` (any), `_` (one char)
- [ ] Correct quote usage (single quotes for strings)
- [ ] WHERE vs HAVING (rows vs groups)

### Normalization
- [ ] 1NF: atomic values, no repeating groups
- [ ] 2NF: 1NF + no partial dependencies (composite key)
- [ ] 3NF: 2NF + no transitive dependencies
- [ ] BCNF: every determinant is candidate key
- [ ] Identifying normal form from functional dependencies

### Transactions & ACID
- [ ] Atomicity, Consistency, Isolation, Durability
- [ ] COMMIT vs ROLLBACK
- [ ] Concurrency problems: dirty read, lost update, unrepeatable read

### Database Design Process
- [ ] Enterprise modeling → ER → Logical → Physical → Implementation

---

## Quick Mnemonics

| Concept | Mnemonic |
|---------|----------|
| **SQL execution order** | **FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY** |
| **1NF** | "Atomic or Array-free" — no multi-valued attributes |
| **2NF** | "No Partial" — every non-key depends on ALL of composite key |
| **3NF** | "No Transitive" — non-key depends only on key |
| **ACID** | **A**tomicity, **C**onsistency, **I**solation, **D**urability |
| **Foreign Key** | "FK = PK or NULL" |
| **DISTINCT** | "Unique rows — distinct means no duplicates" |
| **WHERE vs HAVING** | "WHERE is for rows, HAVING is for groups" |
| **ON UPDATE CASCADE** | "Update FK when PK changes — cascade the change" |

## 1-Page Cram Sheet

```
SQL CLAUSE ORDER
════════════════
SELECT  → 5 (columns)
FROM    → 1 (tables)
WHERE   → 2 (row filter)
GROUP BY → 3 (grouping)
HAVING  → 4 (group filter)
ORDER BY → 6 (sort)

NORMAL FORMS
════════════
1NF: Atomic values ✓
2NF: 1NF + No partial dependencies ✓
3NF: 2NF + No transitive dependencies ✓

SQL KEYWORDS
════════════
INSERT INTO table (cols) VALUES (vals)
SELECT cols FROM t1 JOIN t2 ON condition
DISTINCT — removes duplicates
LIKE '%pattern%' — wildcard search

CONSTRAINTS
═══════════
PRIMARY KEY → NOT NULL + UNIQUE
FOREIGN KEY → references PK of other table
             → value OR NULL (if nullable)

AGGREGATE FUNCTIONS (with GROUP BY)
════════════
COUNT(*)     — number of rows
SUM(col)     — sum of values
AVG(col)     — average
MIN(col)     — minimum
MAX(col)     — maximum

ACID PROPERTIES
═══════════════
Atomicity — all or nothing
Consistency — valid state → valid state
Isolation — concurrent transactions independent
Durability — committed changes persist

DESIGN PROCESS
══════════════
Enterprise Model → ER Diagram → Logical Schema 
  → Physical Design → Implementation (SQL DDL)
```
