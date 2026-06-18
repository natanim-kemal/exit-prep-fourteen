# Day 5 — Fundamentals of Databases (7 Items)

## 1. Database Fundamentals

### What is a Database?
- **Logically coherent** collection of related data with **inherent meaning**
- Represents some aspect of the real world (miniworld)
- Designed, built, and populated for a specific purpose

### Database vs DBMS
| Database | DBMS |
|----------|------|
| Collection of structured data | Software to manage the database |
| What you store | How you store, query, manage it |
| Examples: student records, inventory | Examples: MySQL, PostgreSQL, Oracle |

### Characteristics of Database Approach

| Feature | Description |
|---------|-------------|
| **Self-describing** | Database contains metadata (catalog) about itself |
| **Data abstraction** | Hides storage details; users see conceptual view |
| **Multiple views** | Different users see different subsets of data |
| **Data sharing** | Multiple users/programs share same data |
| **Controlled redundancy** | Minimizes duplication (unlike file systems) |
| **Data independence** | Changes to storage don't affect applications |

```
Which is NOT a characterizing feature of database approach?
A. Application-data dependency         ← ✗ (this IS a file system problem, not DB)
B. Sharing of data                     ← ✓ feature
C. Self-describing                     ← ✓ feature
D. Data abstraction                    ← ✓ feature
```
**Answer**: A — Application-data dependency is a characteristic of **file systems**, not database approach

### Database Design Process
```
Enterprise data modeling → Conceptual design (ER)
  → Logical design (Relational schema) 
  → Physical design (Storage/Indexes)
  → Implementation (SQL DDL)
```

**Exam question**: Correct sequence of database design processes:
- A. Logical → Enterprise → Physical → Implementation
- B. Enterprise → Logical → Implementation → Physical
- C. **Enterprise → Logical → Physical → Implementation** ← ✓
- D. Logical → Enterprise → Physical → Implementation

---

## 2. Data Models

### Types of Data Models
| Model | Description | Example |
|-------|-------------|---------|
| **Conceptual** | High-level, user-oriented | ER Diagram |
| **Logical** | Implementation-oriented | Relational model |
| **Physical** | Storage details | Indexes, partitions |

### Three-Schema Architecture
```
External Schema  (user views)
      ↓
Conceptual Schema  (logical structure)
      ↓
Internal Schema  (physical storage)
```
Achieves **data independence**: 
- **Logical**: change conceptual schema without affecting external views
- **Physical**: change internal schema without affecting conceptual schema

---

## 3. ER Model (Entity-Relationship)

### ER Components

| Component | Symbol | Example |
|-----------|--------|---------|
| **Entity** | Rectangle | Student, Course |
| **Attribute** | Ellipse | name, ID, age |
| **Relationship** | Diamond | Enrolls, Teaches |
| **Weak Entity** | Double Rectangle | Dependent (depends on Employee) |
| **Key Attribute** | Underlined Ellipse | StudentID |

### Attribute Types
| Type | Description | Example |
|------|-------------|---------|
| **Simple** | Atomic, cannot be split | Age |
| **Composite** | Can be subdivided | Name → First + Last |
| **Single-valued** | One value per entity | StudentID |
| **Multi-valued** | Multiple values possible | PhoneNumbers |
| **Derived** | Can be computed from others | Age (from DOB) |
| **Key** | Uniquely identifies entity | StudentID |

### Relationship Types
- **Degree**: unary, binary, ternary
- **Cardinality**: 1:1, 1:N, M:N
- **Participation**: Total (every entity participates) vs Partial
- **Existence dependency**: weak entity depends on strong entity

### Participation Exam Question
```
DORM (DormID, floorNumber) — DormID is PK
STUDENT (IdNo, Name, Department) — IdNo is PK
Rule: six students per dorm, every DORM must have at least one student.

Which is true?
A. STUDENT has existence dependency
B. STUDENT has total participation     ← ✗ (a student could exist without a dorm?)
C. DORM has total participation        ← ✓ (every dorm must have students)
```
**Answer**: C — The rule says "every DORM must have at least one student" → DORM has **total participation**

---

## 4. Relational Model

### Relational Terminology

| Formal Term | Informal Equivalent |
|-------------|-------------------|
| **Relation** | Table |
| **Tuple** | Row |
| **Attribute** | Column |
| **Domain** | Set of allowed values |
| **Degree** | Number of attributes |
| **Cardinality** | Number of tuples |
| **Schema** | Table structure (name + attributes) |

### Relational Constraints

| Constraint | Description |
|------------|-------------|
| **Domain** | Values must be from declared domain |
| **Key** | Each tuple must be uniquely identifiable |
| **Entity Integrity** | Primary key cannot be NULL |
| **Referential Integrity** | Foreign key must match a primary key value OR be NULL |

### Primary Key Rules
- Must be **NOT NULL** (entity integrity)
- Must be **unique** across all tuples
- Should be **stable** (rarely changes)

```
In relation design, primary key should be defined as:
A. Non-editable
B. NULL
C. NOT NULL       ← ✓
D. Within limited value
```

### Foreign Key
- Attribute(s) in one relation that references **primary key** of another relation
- Maintains **referential integrity**
- Values must either match a PK value or be NULL

```sql
-- STUDENT table references DORM
CREATE TABLE STUDENT (
    IdNo INT PRIMARY KEY,
    Name VARCHAR(100),
    Department VARCHAR(50),
    DorID INT,
    FOREIGN KEY (DorID) REFERENCES DORM(DormID)
);
```

### Referential Triggered Actions
| Action | Description |
|--------|-------------|
| **ON DELETE CASCADE** | Delete referencing tuples when referenced tuple is deleted |
| **ON DELETE SET NULL** | Set FK to NULL when referenced tuple is deleted |
| **ON DELETE RESTRICT** | Prevent deletion if referencing tuples exist |
| **ON UPDATE CASCADE** | Update FK when PK of referenced tuple changes |

```
ON UPDATE CASCADE means:
A. Sets referencing PK to default
B. Changes referencing FK to updated PK for all referencing tuples  ← ✓
C. Deletes all referencing tuples
D. Sets referencing PK to NULL
```

---

## 5. SQL (Structured Query Language)

### SQL Categories

| Category | Description | Commands |
|----------|-------------|----------|
| **DDL** (Data Definition) | Define/modify schema | CREATE, ALTER, DROP, TRUNCATE |
| **DML** (Data Manipulation) | Query/modify data | SELECT, INSERT, UPDATE, DELETE |
| **DCL** (Data Control) | Permissions | GRANT, REVOKE |
| **TCL** (Transaction Control) | Manage transactions | COMMIT, ROLLBACK, SAVEPOINT |

### SELECT Statement — Clauses Order
```sql
SELECT   column(s)               -- 5. Which columns to show
FROM     table(s)                -- 1. Which tables
WHERE    condition(s)            -- 2. Filter rows
GROUP BY column(s)               -- 3. Group rows
HAVING   group_condition(s)      -- 4. Filter groups
ORDER BY column(s) [ASC|DESC];   -- 6. Sort result
```
**Execution order**: FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY

### INSERT Statement
```sql
-- Correct syntax:
INSERT INTO HOTEL (Hotel_id, Hotel_name, Sub_city)
VALUES (1, 'Hilton', 'Yeka');

-- WRONG: missing column list
INSERT INTO HOTEL (1, 'Hilton', 'Yeka');

-- WRONG: VALUES before INTO
INSERT VALUES INTO HOTEL (...) VALUES (...);

-- WRONG: wrong quote style (backticks for identifiers, quotes for strings)
INSERT INTO HOTEL (Hotel_id, Hotel_name, Sub_city)
VALUES (1, `Hilton`, `Yeka`);
```
**Correct**: `INSERT INTO table (columns) VALUES (values);`
Strings must use **single quotes** `' '`, not backticks.

### JOIN Queries
```sql
-- INNER JOIN — matching rows from both tables
SELECT Hotel_Name, Room_Id
FROM HOTEL, ROOM
WHERE ROOM.Hotel_id = HOTEL.Hotel_id;

-- Or with explicit JOIN syntax:
SELECT Hotel_Name, Room_Id
FROM HOTEL
INNER JOIN ROOM ON HOTEL.Hotel_id = ROOM.Hotel_id;
```

**Exam question**: Schema — HOTEL(Hotel_id, Hotel_Name, Sub_city), ROOM(Room_id, Hotel_id, Price). Which SQL retrieves Hotel names with Room_id?
```sql
A. SELECT Hotel_Name, Room_Id FROM HOTEL, ROOM 
   WHERE ROOM.Hotel_id = HOTEL.Hotel_id;               ← ✓ correct

B. SELECT Hotel_Name, Room_Id FROM HOTEL, ROOM;       -- ✗ Cartesian product

C. SELECT Hotel_Name, Room_Id FROM HOTEL, ROOM 
   WHERE ROOM.Room_id = HOTEL.Hotel_id;                -- ✗ wrong join condition
```

### DISTINCT — Eliminate Duplicates
```sql
SELECT DISTINCT City FROM Customers;
-- Returns each city only once (no duplicates)
```

### Aggregate Functions
| Function | Description |
|----------|-------------|
| `COUNT()` | Number of rows/values |
| `SUM()` | Sum of values |
| `AVG()` | Average of values |
| `MIN()` | Minimum value |
| `MAX()` | Maximum value |

```sql
SELECT COUNT(*) FROM Students;           -- total rows
SELECT AVG(Price) FROM Products;         -- average price
SELECT Department, COUNT(*) 
FROM Students 
GROUP BY Department;                     -- count per department
```

### GROUP BY & HAVING
```sql
-- How many students per department, only show departments with > 10 students
SELECT Department, COUNT(*) AS StudentCount
FROM Students
GROUP BY Department
HAVING COUNT(*) > 10
ORDER BY StudentCount DESC;
```
- `WHERE` filters rows **before** grouping
- `HAVING` filters groups **after** grouping

### LIKE & Wildcards
```sql
SELECT * FROM Students WHERE Name LIKE 'A%';    -- starts with A
SELECT * FROM Students WHERE Name LIKE '%son';   -- ends with "son"
SELECT * FROM Students WHERE Name LIKE '%mith%'; -- contains "mith"
SELECT * FROM Students WHERE Name LIKE '_at%';   -- second char is 'a'
```
- `%` — any sequence of characters (including zero)
- `_` — exactly one character

---

## 6. Normalization

### Purpose of Normalization
- Eliminate data redundancy (duplication)
- Eliminate update anomalies (insert, update, delete)
- Ensure data integrity

### Normal Forms

| Normal Form | Rule | How to Fix |
|-------------|------|------------|
| **1NF** | Atomic values, no repeating groups | Separate multi-valued attributes into new tables |
| **2NF** | 1NF + No partial dependencies (non-key depends on part of composite key) | Remove partial dependencies |
| **3NF** | 2NF + No transitive dependencies (non-key depends on another non-key) | Remove transitive dependencies |
| **BCNF** | 3NF + Every determinant is a candidate key | More restrictive 3NF |

### 1NF (First Normal Form)
- Each cell contains **atomic** (single) value
- No **repeating groups** or arrays
- Each row is unique

**Unnormalized** (not 1NF):
| StudentID | Name | Courses |
|-----------|------|---------|
| 101 | Alice | CS101, CS102 |

**1NF**:
| StudentID | Name | Course |
|-----------|------|--------|
| 101 | Alice | CS101 |
| 101 | Alice | CS102 |

### 2NF (Second Normal Form)
- Must be in 1NF
- **No partial dependencies** — every non-key attribute must depend on the **entire** primary key (relevant for composite keys)

**Not 2NF** (with composite PK: StudentID + CourseID):
| StudentID | CourseID | StudentName | CourseName | Grade |
|-----------|----------|-------------|------------|-------|
| 101 | CS101 | Alice | Algorithms | A |

StudentName depends only on StudentID (partial dependency)
CourseName depends only on CourseID (partial dependency)

**2NF**: Split into 3 tables:
- Students(StudentID, StudentName)
- Courses(CourseID, CourseName)
- Enrollments(StudentID, CourseID, Grade)

### 3NF (Third Normal Form)
- Must be in 2NF
- **No transitive dependency** — non-key attribute does not depend on another non-key attribute

**Not 3NF**:
| EmpID | EmpName | DeptID | DeptLocation |
|-------|---------|--------|-------------|

DeptLocation depends on DeptID, not directly on EmpID (transitive dependency)

### Normalization Exam Question
```
While optimizing a relation, we find that no multivalued attributes 
AND no partial dependencies exist. What normal form is the relation in?

A. 1NF    (would have multivalued attributes — violates 1NF)
B. 2NF    (1NF + no partial dependencies)   ← ✓
C. 3NF    (would also need no transitive dependencies)
D. 4NF    (would need BCNF + no multi-valued dependencies)
```
**Answer**: B — 2NF (1NF + no partial dependencies; transitive dependencies may still exist)

---

## 7. Transactions & ACID

### Transaction
A **transaction** is a logical unit of work with one or more SQL operations.
- All operations succeed → **COMMIT**
- Any operation fails → **ROLLBACK** (undo all changes)

### ACID Properties

| Property | Description |
|----------|-------------|
| **Atomicity** | All or nothing — transaction is indivisible |
| **Consistency** | Database moves from one valid state to another |
| **Isolation** | Concurrent transactions don't interfere with each other |
| **Durability** | Committed changes survive system failures |

### Concurrency Problems
| Problem | Description |
|---------|-------------|
| **Dirty Read** | Reading uncommitted data from another transaction |
| **Lost Update** | Two transactions read same data, one overwrites other's changes |
| **Unrepeatable Read** | Same query returns different results within a transaction |
| **Phantom Read** | New rows inserted by another transaction appear in same query |

### Locking
- **Shared Lock** (read): multiple transactions can read simultaneously
- **Exclusive Lock** (write): only one transaction can write
- **Deadlock**: two transactions each hold a lock the other needs

---

## 8. Database Security

### Security Issues
- **Authentication**: verifying user identity
- **Authorization**: granting access privileges
- **Encryption**: protecting data at rest and in transit
- **SQL Injection**: malicious SQL in user input

### SQL Injection Example
```sql
-- Vulnerable code: string concatenation with user input
"SELECT * FROM Users WHERE name = '" + userName + "';"

-- User enters: ' OR '1'='1
-- Becomes: SELECT * FROM Users WHERE name = '' OR '1'='1';
-- Returns ALL users!
```
**Defense**: Use **prepared statements** (parameterized queries)

### GRANT & REVOKE
```sql
GRANT SELECT, INSERT ON Students TO user1;
REVOKE DELETE ON Students FROM user1;
```

---

## Exam-Style Practice Questions

### Q1: INSERT Syntax
Which SQL correctly inserts a tuple into HOTEL(Hotel_id, Hotel_name, Sub_city)?
```sql
A. INSERT INTO HOTEL (Hotel_id, Hotel_name, Sub_city) VALUES ('Hilton','Yeka')
                                                              -- ✗ missing Hotel_id
B. INSERT INTO HOTEL (Hotel_id, Hotel_name, Sub_city) VALUES (1, 'Hilton','Yeka')  ← ✓
C. INSERT INTO HOTEL (1, 'Hilton','Yeka')                    -- ✗ missing column list
D. INSERT VALUES INTO HOTEL (Hotel_id, Hotel_name, Sub_city) VALUES (1, 'Hilton','Yeka')
                                                              -- ✗ wrong syntax
```
**Answer**: B

---

### Q2: Primary Key
Which constraint must a primary key satisfy?
- A. Non-editable
- B. NULL
- C. **NOT NULL** ← ✓
- D. Within limited value

---

### Q3: Normalization
No multivalued attributes + no partial dependencies = which normal form?
- A. 1NF
- B. **2NF** ← ✓
- C. 3NF
- D. 4NF

---

### Q4: Database Design Sequence
Correct order of database design:
- A. Logical → Enterprise → Physical → Implementation
- B. Enterprise → Logical → Implementation → Physical
- C. **Enterprise → Logical → Physical → Implementation** ← ✓
- D. Logical → Enterprise → Physical → Implementation

---

### Q5: Foreign Key
Which SQL correctly adds a FK in STUDENT referencing DORM?
```sql
A. FOREIGN KEY (DorID) REFERENCES DORM(DormID)     ← ✓
B. STUDENT table is a reference relation             ← ✗ not SQL
C. FOREIGN KEY (DorID) REFERENCEd by DORM(DormID)   ← ✗ wrong syntax
D. DORM table is a referencing relation              ← ✗ not SQL
```

---

### Q6: ON UPDATE CASCADE
ON UPDATE CASCADE means:
- A. Sets referencing PK to default
- B. **Changes FK to updated PK for referencing tuples** ← ✓
- C. Deletes all referencing tuples
- D. Sets referencing PK to NULL

---

### Q7: DISTINCT
Keyword to eliminate duplicate tuples from SELECT result?
- A. Group By
- B. UNIQUE
- C. PRIMARY
- D. **DISTINCT** ← ✓

---

### Q8: JOIN Query
Schemas: HOTEL(Hotel_id, Hotel_Name, Sub_city), ROOM(Room_id, Hotel_id, Price)
Which retrieves Hotel names with their Room_id?
```sql
A. SELECT Hotel_Name, Room_Id FROM HOTEL, ROOM 
   WHERE ROOM.Hotel_id = HOTEL.Hotel_id;              ← ✓
B. SELECT Hotel_Name, Room_Id FROM HOTEL, ROOM;       -- ✗ Cartesian
C. SELECT Hotel_Name, Room_Id FROM HOTEL, ROOM 
   WHERE ROOM.Room_id = HOTEL.Hotel_id;               -- ✗ wrong condition
D. SELECT Hotel_Name, Room_Id FROM HOTEL, ROOM 
   WHERE ROOM.Room_id = HOTEL.Hotel_id AND ROOM.Hotel_id = HOTEL.Hotel_id;  -- ✗
```

---

### Q9: Database Approach Feature
Which is NOT a feature of database approach?
- A. **Application-data dependency** ← ✗ (this is a file system flaw)
- B. Sharing of data
- C. Self-describing
- D. Data abstraction

---

### Q10: Multiple Views
"Database supports different user groups with different interest in different parts" describes:
- A. **Multiple views** ← ✓
- B. Parallel transaction
- C. Multiple users
- D. Concurrent transaction

---

### Q11: Participation
DORM must have at least one student. What type of participation?
- A. STUDENT has total participation
- B. **DORM has total participation** ← ✓
- C. Partial participation
- D. Weak participation

---

### Q12: Database Definition
"Database is a logically coherent collection of data with inherent meaning" describes that:
- A. All attributes of entity should be related
- B. There should be one primary key
- C. Entity should be physical object
- D. **Data has inherent meaning** — the definition itself

---

### Q13: Aggregate Functions
Which SQL calculates average price?
```sql
A. SELECT AVG(Price) FROM Products;    ← ✓
B. SELECT SUM(Price) FROM Products;
C. SELECT COUNT(Price) FROM Products;
D. SELECT MEAN(Price) FROM Products;
```

---

### Q14: GROUP BY
Count students per department:
```sql
SELECT Department, COUNT(*) 
FROM Students 
GROUP BY Department;     ← ✓
```

---

### Q15: Referential Integrity
A foreign key value must:
- A. Always be NULL
- B. Match a primary key value OR be NULL ← ✓
- C. Be unique
- D. Never change

---

---

## Question Bank Study Notes

### Normalization
1NF: atomic values. 2NF: 1NF + no partial dependencies. 3NF: 2NF + no transitive dependencies. BCNF: every determinant is candidate key. Anomalies: update, insertion, deletion.

### ACID
Atomicity (all or nothing), Consistency (valid state to valid state), Isolation (concurrent don't interfere), Durability (committed persists).

### SQL
DDL: CREATE, ALTER, DROP. DML: SELECT, INSERT, UPDATE, DELETE. `WHERE` before `GROUP BY`, `HAVING` after. `DISTINCT` removes duplicates. `JOIN` combines tables on condition. `CASCADE`: auto-delete referencing rows.

### Keys
**Primary key**: NOT NULL + unique. **Foreign key**: enforces referential integrity; can be NULL or valid reference.

### Views & Indexes
View = virtual table (no physical storage). Indexes speed reads, slow writes.

### Security
SQL Injection: use parameterized queries. Encryption: at rest (TDE) and in transit (SSL).


## Quick Reference Card

```
SQL KEYWORDS
════════════
SELECT columns FROM tables WHERE condition
INSERT INTO table (cols) VALUES (vals)
UPDATE table SET col = val WHERE condition
DELETE FROM table WHERE condition
CREATE TABLE name (col type constraints)
ALTER TABLE name ADD/MODIFY/DROP column

CONSTRAINTS
═══════════
PRIMARY KEY → NOT NULL + UNIQUE
FOREIGN KEY → REFERENCES other_table(pk)
NOT NULL    → value required
UNIQUE      → no duplicates
DEFAULT     → default value
CHECK       → condition check

AGGREGATE FUNCTIONS
═══════════════════
COUNT, SUM, AVG, MIN, MAX

NORMAL FORMS
════════════
1NF: atomic values, no repeating groups
2NF: 1NF + no partial dependencies
3NF: 2NF + no transitive dependencies
BCNF: every determinant is a candidate key

ACID
════
Atomicity, Consistency, Isolation, Durability

DESIGN SEQUENCE
══════════════
Enterprise Modeling → ER → Logical → Physical → Implementation

KEY RULES
═════════
- Primary key = NOT NULL
- Foreign key = value OR NULL
- DISTINCT removes duplicate rows
- WHERE before GROUP BY, HAVING after
- Strings use single quotes ' '
- JOIN needs correct condition (FK = PK)
- CASCADE updates/deletes referencing rows
```
