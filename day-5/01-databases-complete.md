# Day 5 — Fundamentals of Databases (105 Items)

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


## Practice Questions (from Question Bank)

Answer: C
### Q542. Normal form eliminating transitive dependencies?

- A) 1NF
- B) 2NF
- C) BCNF
- D) 3NF
  **Answer: D**

### Q543. Consider a system where which statement about Acid isolation is correct?

- A) Concurrent transactions
- B) Permanently saved
- C) Completes fully
- D) Stays consistent
  **Answer: A**

### Q544. LEFT JOIN returns?

- A) All rows both sides
- B) Only matching rows
- C) All left + matching right
- D) All right + matching left
  **Answer: C**

### Q545. M:N relationship converted to tables by?

- A) Adding FK to both
- B) Merging entities
- C) FK on smaller table
- D) Creating junction table
  **Answer: D**

### Q546. Consider a system where partial dependency eliminated by?

- A) 3NF
- B) 1NF
- C) BCNF
- D) 2NF
  **Answer: D**

### Q547. SQL to undo uncommitted changes?

- A) COMMIT
- B) TRUNCATE
- C) SAVEPOINT
- D) ROLLBACK
  **Answer: D**

### Q548. Adding index speeds up SELECT but slows?

- A) DELETE only
- B) INSERT and UPDATE
- C) COMMIT
- D) SELECT further
  **Answer: B**

### Q549. When designing for high performance, cOUNT(column_name) counts?

- A) Non-NULL values only
- B) Distinct values
- C) NULL values only
- D) All rows
  **Answer: A**

### Q550. VIEW vs base table?

- A) View is virtual based on SELECT
- B) Both store data
- C) Views update indexes
- D) View stores data physically
  **Answer: A**

### Q551. 1NF violation characteristic?

- A) Transitive dependency
- B) Repeating groups
- C) Partial dependency
- D) Two candidate keys
  **Answer: B**

### Q552. When designing for high performance, which statement about Acid atomicity is correct?

- A) Valid state maintained
- B) Transaction fully completes
- C) Concurrent safe
- D) Data survives failure
  **Answer: B**

### Q553. Which statement about Acid consistency is correct?

- A) Changes are permanent
- B) Database moves from one valid
- C) Transactions don't interfere
- D) Transactions are atomic
  **Answer: B**

### Q554. Which statement about Acid durability is correct?

- A) Committed data survives
- B) Consistency
- C) Atomicity
- D) Isolation
  **Answer: A**

### Q555. Consider a system where iNNER JOIN returns?

- A) All rows both sides
- B) All right rows
- C) Only rows with matching
- D) All left rows
  **Answer: C**

### Q556. FULL OUTER JOIN returns?

- A) All right + NULLs for left
- B) All left + NULLs for right
- C) Matching rows only
- D) All rows from both tables with
  **Answer: D**

### Q557. RIGHT JOIN returns?

- A) All left + matching right
- B) All rows both sides
- C) All right + matching left
- D) Matching only
  **Answer: C**

### Q558. When designing for high performance, which description of primary key is accurate?

- A) Foreign key constraint
- B) Most important table
- C) First column of table
- D) Column uniquely identifying each row
  **Answer: D**

### Q559. Which description of foreign key is accurate?

- A) Key from external system
- B) Composite key
- C) Key encrypted for security
- D) Column referencing primary key
  **Answer: D**

### Q560. Which description of candidate key is accurate?

- A) Potential future primary key
- B) Any column that could serve
- C) Secondary index
- D) Foreign key candidate
  **Answer: B**

### Q561. Consider a system where identify the correct statement about composite key.

- A) Key with multiple data types
- B) Primary key made of two
- C) Key referencing multiple tables
- D) Encrypted key
  **Answer: B**

### Q562. DDL stands for?

- A) Data Display Language
- B) Data Definition Language —
- C) Dynamic Data Layer
- D) Data Deletion Logic
  **Answer: B**

### Q563. DML stands for?

- A) Database Management Layer
- B) Data Modeling Language
- C) Data Manipulation Language —
- D) Data Migration Library
  **Answer: C**

### Q564. In a resource-constrained environment, what does GROUP BY do in SQL?

- A) Filters rows
- B) Groups rows with same
- C) Joins tables
- D) Sorts results
  **Answer: B**

### Q565. What does HAVING clause do?

- A) Filters groups after GROUP BY
- B) Filters rows before grouping
- C) Joins groups
- D) Sorts groups
  **Answer: A**

### Q566. Difference between WHERE and HAVING?

- A) No difference
- B) HAVING filters rows
- C) WHERE filters rows
- D) Both filter rows
  **Answer: C**

### Q567. When designing for high performance, identify the correct statement about subquery.

- A) Query nested inside another query
- B) Stored procedure
- C) View definition
- D) Simplified main query
  **Answer: A**

### Q568. Which description of correlated subquery is accurate?

- A) Subquery without WHERE
- B) Subquery using JOIN
- C) Subquery that references
- D) Subquery with aggregate
  **Answer: C**

### Q569. What does DISTINCT keyword do?

- A) Removes duplicate rows
- B) Groups rows
- C) Sorts results
- D) Filters NULL values
  **Answer: A**

### Q570. In a resource-constrained environment, what does ORDER BY do?

- A) Limits results
- B) Filters results
- C) Sorts result by specified column
- D) Groups results
  **Answer: C**

### Q571. What does LIMIT/TOP do?

- A) Groups results
- B) Restricts number of rows
- C) Sorts results
- D) Filters rows
  **Answer: B**

### Q572. Which of the following best describes normalization?

- A) Converting data to normal form
- B) Standardizing column names
- C) Normalizing numeric values
- D) Eliminating data redundancy and
  **Answer: C**

### Q573. When designing for high performance, which description of denormalization is accurate?

- A) Removing primary keys
- B) Breaking normalization rules
- C) Converting to NoSQL
- D) Intentionally introducing
  **Answer: D**

### Q574. Which description of transaction is accurate?

- A) Table join operation
- B) Index creation
- C) Unit of work treated atomically
- D) Single SQL query
  **Answer: C**

### Q575. SAVEPOINT in transactions?

- A) Creates rollback point
- B) Locks table
- C) Ends transaction
- D) Commits transaction
  **Answer: A**

### Q576. Consider a system where clustered vs non-clustered index?

- A) Both create separate structures
- B) Non-clustered orders physical data
- C) Clustered orders physical data
- D) No difference
  **Answer: B**

### Q577. Which description of dirty read concurrency problem is accurate?

- A) Reading same row twice
- B) Reading committed data
- C) Reading uncommitted data from
- D) Reading non-existent row
  **Answer: C**

### Q578. Which of the following best describes non-repeatable read?

- A) Reading uncommitted data
- B) Reading deleted row
- C) Same row read twice gives
- D) Reading rows that
  **Answer: C**

### Q579. When designing for high performance, identify the correct statement about phantom read.

- A) Reading null values
- B) Reading uncommitted data
- C) Re-executing query returns
- D) Reading deleted record
  **Answer: C**

### Q580. Highest isolation level preventing all anomalies?

- A) READ COMMITTED
- B) READ UNCOMMITTED
- C) SERIALIZABLE
- D) REPEATABLE READ
  **Answer: C**

### Q581. What does TRUNCATE do vs DELETE?

- A) TRUNCATE keeps structure
- B) Both identical
- C) DELETE is faster
- D) TRUNCATE removes all
  **Answer: A**

### Q582. When designing for high performance, what does DROP TABLE do?

- A) Renames table
- B) Removes table definition
- C) Removes all rows but
- D) Drops index only
  **Answer: B**

### Q583. Which of the following best describes referential integrity?

- A) Column values must be unique
- B) All columns must have values
- C) Foreign key must reference existing
- D) Primary key must be unique
  **Answer: C**

### Q584. Which of the following best describes CASCADE DELETE?

- A) Sets child FK to NULL on parent delete
- B) Prevents deletion if referenced records exist
- C) Logs deletion for audit
- D) Automatically deletes child records when
  **Answer: D**

### Q585. When designing for high performance, identify the correct statement about NoSQL database.

- A) Database with no transactions
- B) Database with no indexes
- C) Non-relational database
- D) Database with no SQL support
  **Answer: C**

### Q586. Identify the correct statement about document database (e.g., MongoDB).

- A) Stores data as key-value pairs
- B) Stores data as JSON-like documents
- C) Stores data in tables
- D) Stores data as graphs
  **Answer: B**

### Q587. Identify the correct statement about key-value store.

- A) Database with primary keys only
- B) Graph with labeled edges
- C) Relational table with key column
- D) Simplest NoSQL database — data stored
  **Answer: D**

### Q588. Consider a system where when is NoSQL preferred over relational?

- A) When ACID is required
- B) When high scalability, flexible schema
- C) When data is highly relational
- D) For small datasets
  **Answer: B**

### Q589. Which description of schema in database context is accurate?

- A) Backup of database
- B) User permission set
- C) Instance of data at a
- D) Blueprint defining tables
  **Answer: D**

### Q590. Identify the correct statement about database instance.

- A) Database schema
- B) Table definition
- C) Running database software
- D) Actual data stored in
  **Answer: D**

### Q591. When designing for high performance, identify the correct statement about n ER diagram used for.

- A) Creating SQL queries
- B) Visually modeling entities
- C) Planning UI wireframes
- D) Designing network topology
  **Answer: B**

### Q592. In ER diagram, entity is represented by?

- A) Arrow
- B) Ellipse
- C) Rectangle
- D) Diamond
  **Answer: C**

### Q593. In ER diagram, relationship is represented by?

- A) Rectangle
- B) Diamond
- C) Ellipse
- D) Circle
  **Answer: B**

### Q594. Consider a system where in ER diagram, attribute is represented by?

- A) Diamond
- B) Ellipse
- C) Triangle
- D) Rectangle
  **Answer: B**

### Q595. Identify the correct statement about total participation in ER.

- A) Every entity doesn't
- B) Optional participation
- C) Partial participation
- D) Every entity must participate
  **Answer: D**

### Q596. BCNF requires?

- A) Every determinant is a candidate key
- B) No transitive dependencies
- C) No partial dependencies
- D) No repeating groups
  **Answer: A**

### Q597. Consider a system where which description of functional dependency is accurate?

- A) Procedural dependency
- B) A function calling another
- C) Foreign key dependency
- D) Attribute X determines attribute Y
  **Answer: D**

### Q598. Identify the correct statement about superkey.

- A) Primary key with most columns
- B) Set of attributes that
- C) Candidate key variant
- D) Super admin key
  **Answer: B**

### Q599. What does ALTER TABLE ADD COLUMN do?

- A) Adds new column to existing table
- B) Creates new table
- C) Deletes column
- D) Modifies column type
  **Answer: A**

### Q600. In a resource-constrained environment, which description of stored procedure is accurate?

- A) Precompiled SQL code
- B) Saved SQL query
- C) Trigger function
- D) Index on procedure call
  **Answer: A**

### Q601. Which of the following best describes trigger in databases?

- A) Procedure that automatica
- B) An index type
- C) A scheduled job
- D) A foreign key action
  **Answer: A**

### Q602. Identify the correct statement about GRANT in SQL security.

- A) Removes privileges
- B) Creates user accounts
- C) Encrypts data
- D) Gives user/role specific
  **Answer: D**

### Q603. When designing for high performance, which description of REVOKE in SQL is accurate?

- A) Creates roles
- B) Logs access
- C) Removes previously
- D) Grants privileges
  **Answer: C**

### Q604. Which description of difference between UNION and UNION ALL is accurate?

- A) No difference
- B) UNION removes duplicates
- C) UNION ALL removes duplicates
- D) UNION keeps duplicates
  **Answer: C**

### Q605. Which of the following best describes n aggregate function?

- A) String function
- B) Function combining two tables
- C) Function computing single
- D) Function on single row
  **Answer: C**

### Q606. When designing for high performance, what does AVG() function return?

- A) Average of numeric values
- B) Sum of values
- C) Maximum value
- D) Minimum value
  **Answer: A**

### Q607. Which description of purpose of LIKE operator is accurate?

- A) Numeric comparison
- B) Compares exact values
- C) Pattern matching in strings
- D) NULL checking
  **Answer: C**

### Q608. What does IS NULL check for?

- A) Missing/unknown value
- B) Empty string
- C) Zero value
- D) Negative value
  **Answer: A**

### Q609. Which of the following best describes difference between CHAR and VARCHAR?

- A) VARCHAR is fixed
- B) CHAR is fixed-length
- C) No difference
- D) Both are variable
  **Answer: A**

### Q610. Identify the correct statement about n index's impact on query performance.

- A) Only helps with JOINs
- B) Speeds up SELECT on indexed
- C) No impact
- D) Always slows queries
  **Answer: B**

### Q611. Which description of self-join is accurate?

- A) Join with no condition
- B) Table joining with itself using alias
- C) Cross join variant
- D) Joining same-named columns
  **Answer: B**

### Q612. In a resource-constrained environment, identify the correct statement about CROSS JOIN.

- A) Join removing duplicates
- B) Join matching rows only
- C) Join on primary-foreign key
- D) Cartesian product — every row
  **Answer: D**

### Q613. Which description of natural join is accurate?

- A) Join with no duplicates
- B) Join automatically using
- C) Join defined by user conditions
- D) Outer join variant
  **Answer: B**

### Q614. Identify the correct statement about database normalization's main goal.

- A) Simplify queries
- B) Improve query speed always
- C) Increase database size
- D) Reduce redundancy and prevent
  **Answer: D**

### Q615. In a resource-constrained environment, which of the following best describes n insert anomaly?

- A) Inserting in wrong table
- B) Inserting NULL primary key
- C) Unable to insert data without
- D) Inserting duplicate rows
  **Answer: C**

### Q616. Which of the following best describes n update anomaly?

- A) UPDATE syntax error
- B) NULL update error
- C) UPDATE permission denied
- D) Must update same data in
  **Answer: D**

### Q617. Identify the correct statement about delete anomaly.

- A) DELETE syntax error
- B) Foreign key violation on
- C) Deleting one piece of data
- D) Deleting wrong row
  **Answer: C**

### Q618. In a resource-constrained environment, what does EXPLAIN in SQL do?

- A) Shows index definitions
- B) Explains database structure
- C) Documents table schema
- D) Shows query execution plan for
  **Answer: B**

### Q619. Which description of connection pooling is accurate?

- A) Load balancing queries
- B) Pooling database servers
- C) Replicating databases
- D) Reusing database connections
  **Answer: D**

### Q620. Which description of database replication is accurate?

- A) Copying database to one
- B) Backup creation
- C) Schema duplication
- D) Index copying
  **Answer: A**

### Q621. Consider a system where which description of sharding is accurate?

- A) Backup method
- B) Horizontally partitioning
- C) Splitting tables
- D) Indexing strategy
  **Answer: B**

### Q622. Identify the correct statement about CAP theorem for distributed databases.

- A) Cost, Availability, Performance
- B) Consistency, Availability, Partition
- C) Caching, Atomicity, Persistence
- D) Concurrency, Atomicity, Performance
  **Answer: B**

### Q623. What does BASE stand for in NoSQL context?

- A) Balanced Aligned Stored Efficient
- B) Block Async Stateless Encrypted
- C) Basically Available Soft-state Eventual consistency
- D) Binary Atomic Scalable Efficient
  **Answer: C**

### Q624. Consider a system where identify the correct statement about n OLTP system.

- A) Offline Transaction Protocol
- B) Online Analytical Processing —
- C) Object-Level Transfer Protocol
- D) Online Transaction Processing — many
  **Answer: D**

### Q625. Which of the following best describes n OLAP system?

- A) Online Analytical Processing —
- B) Online Transaction Processing
- C) Offline Log Analytics Platform
- D) Object-Level Access Protocol
  **Answer: A**

### Q626. Which of the following best describes data warehouse?

- A) Database backup system
- B) File storage system
- C) Central repository
- D) Database for transactional
  **Answer: C**

### Q627. Consider a system where which description of ETL is accurate?

- A) Extract, Transform, Load —
- B) External Table Link
- C) Encrypted Table Layer
- D) Execution, Test, Launch
  **Answer: A**

### Q628. Which of the following best describes materialized view?

- A) Indexed table
- B) View with security policy
- C) View that physically stores
- D) Virtual table like standard view
  **Answer: C**

### Q629. Which of the following best describes sequence in SQL databases?

- A) Sorting mechanism
- B) Transaction order
- C) Database object generatin
- D) Ordered result set
  **Answer: C**

### Q630. Which description of purpose of the COALESCE function is accurate?

- A) Combines strings
- B) Returns first non-NULL
- C) Converts data types
- D) Counts non-null values
  **Answer: B**

### Q631. Which description of database encryption at rest is accurate?

- A) Encrypting passwords only
- B) Encrypting stored data files/tablespaces
- C) SSL for database connections
- D) Encrypting network traffic
  **Answer: B**

### Q632. What does BETWEEN do in SQL?

- A) Filters rows where value
- B) Compares strings
- C) Calculates difference
- D) Joins two tables
  **Answer: A**

### Q633. In a resource-constrained environment, what does IN operator do in SQL?

- A) Checks if value matches
- B) Pattern matching
- C) Null checking
- D) Joins tables
  **Answer: B**

### Q634. Which description of difference between DELETE and TRUNCATE is accurate?

- A) No difference
- B) DELETE cannot be rolled back
- C) TRUNCATE can use WHERE
- D) DELETE is logged and can use
  **Answer: C**

### Q635. Which description of n entity in ER modeling is accurate?

- A) Relationship type
- B) Real-world object
- C) Column in a table
- D) Attribute value
  **Answer: B**

### Q636. Which description of cardinality in ER modeling is accurate?

- A) Number of tables
- B) Number of instances
- C) Number of attributes
- D) Number of keys
  **Answer: B**

### Q637. Which description of 4NF is accurate?

- A) Eliminates transitive dependencies
- B) Eliminates partial dependencies
- C) Extends BCNF eliminating multi-valued
- D) Eliminates repeating groups
  **Answer: C**

### Q638. What does CASE expression do in SQL?

- A) Conditional expression
- B) Creates procedures
- C) Handles exceptions
- D) Creates loops
  **Answer: A**

### Q639. In a resource-constrained environment, which description of NULL value in SQL is accurate?

- A) Unknown
- B) False boolean
- C) Zero
- D) Empty string
  **Answer: A**

### Q640. Three-valued logic in SQL handles NULL how?

- A) NULL = NULL is FALSE
- B) NULL is ignored in comparisons
- C) NULL treated as 0
- D) NULL = NULL is TRUE
  **Answer: A**

### Q641. Which description of EXCEPT/MINUS operator in SQL is accurate?

- A) Returns rows in first query not
- B) Combines all rows
- C) Returns rows in both queries
- D) Intersects two result sets
  **Answer: A**

### Q642. Consider a system where identify the correct statement about INTERSECT in SQL.

- A) Returns rows in first
- B) Returns rows appearing
- C) Joins two tables
- D) Combines all rows
  **Answer: B**

### Q643. Which description of bitmap index is accurate?

- A) Compressed B-tree index
- B) Index on binary columns
- C) Index using bit arrays for
- D) Index storing bitmap images
  **Answer: D**

### Q644. Which of the following best describes B-tree index?

- A) Bitmap index variant
- B) Hash-based index
- C) Binary tree stored
- D) Balanced tree index
  **Answer: D**

### Q645. When designing for high performance, identify the correct statement about hash index.

- A) Spatial index
- B) Index for string columns
- C) Index using hash
- D) B-tree variant
  **Answer: C**

### Q646. Which description of query optimization is accurate?

- A) Process of finding most
- B) Indexing all columns
- C) Writing shorter queries
- D) Caching query results
