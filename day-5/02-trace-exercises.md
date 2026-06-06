# Day 5 — Databases Trace Exercises & Problem-Solving (Exam-Style)

## Set 1: SQL Query Writing

### Problem 1 — Schema Interpretation
Schema: HOTEL(Hotel_id, Hotel_Name, Sub_city), ROOM(Room_id, Hotel_id, Price)
BOOKING(Hotel_id, Room_id, Date_from, Date_to), GUEST(Guest_id, Name, Country)

Write SQL to find all hotels in "Yeka" sub-city.

**Solution:**
```sql
SELECT Hotel_Name 
FROM HOTEL 
WHERE Sub_city = 'Yeka';
```

---

### Problem 2 — JOIN Query
Find all rooms with price greater than 1000, showing hotel name and room price.

**Solution:**
```sql
SELECT HOTEL.Hotel_Name, ROOM.Price
FROM HOTEL
JOIN ROOM ON HOTEL.Hotel_id = ROOM.Hotel_id
WHERE ROOM.Price > 1000;
```

---

### Problem 3 — Multi-table JOIN
Find guest names who booked rooms at "Hilton" hotel.

**Solution:**
```sql
SELECT DISTINCT GUEST.Name
FROM GUEST
JOIN BOOKING ON GUEST.Guest_id = BOOKING.Guest_id
JOIN HOTEL ON BOOKING.Hotel_id = HOTEL.Hotel_id
WHERE HOTEL.Hotel_Name = 'Hilton';
```

---

### Problem 4 — Aggregate with GROUP BY
Find the number of rooms per hotel, showing hotel name and room count.

**Solution:**
```sql
SELECT HOTEL.Hotel_Name, COUNT(ROOM.Room_id) AS RoomCount
FROM HOTEL
LEFT JOIN ROOM ON HOTEL.Hotel_id = ROOM.Hotel_id
GROUP BY HOTEL.Hotel_Name;
```

---

### Problem 5 — INSERT with Foreign Key
Insert a new room with ID 201, in hotel 1, priced at 1500.

**Solution:**
```sql
INSERT INTO ROOM (Room_id, Hotel_id, Price)
VALUES (201, 1, 1500);
```

---

### Problem 6 — DELETE with Condition
Delete all bookings for hotel "Hilton".

**Solution:**
```sql
DELETE FROM BOOKING
WHERE Hotel_id = (SELECT Hotel_id FROM HOTEL WHERE Hotel_Name = 'Hilton');
```

---

## Set 2: Normalization Exercises

### Problem 7 — Identify Normal Form
Relation R(A, B, C, D) with FD: AB → C, AB → D, C → D

```
CK = AB (candidate key)

Check 2NF: 
- AB is composite key
- Any non-key attribute depending on part of AB? 
  A → ? No. B → ? No. So no partial dependency. It's in 2NF.

Check 3NF:
- C → D is a transitive dependency (D depends on C, not directly on AB)
- Since there's a transitive dependency, it's NOT in 3NF.

Answer: 2NF
```

---

### Problem 8 — Decompose to 3NF
R(StudentID, CourseID, Instructor, InstructorOffice) 
FD: StudentID + CourseID → Instructor, Instructor → InstructorOffice

```
CK = (StudentID, CourseID)

Partial dependencies? No (single attribute depends on part? No)

Transitive dependency: Instructor → InstructorOffice
  Instructor depends on StudentID+CourseID
  InstructorOffice depends on Instructor (not directly on CK)

Decompose to 3NF:
R1(StudentID, CourseID, Instructor) — PK = (StudentID, CourseID)
R2(Instructor, InstructorOffice) — PK = Instructor
```

---

### Problem 9 — 1NF Check
Is this in 1NF?
| EmpID | Name | PhoneNumbers |
|-------|------|--------------|
| 1 | Alice | 0911, 0922 |

**Answer**: No — PhoneNumbers contains multiple values (violates atomicity). 
**Fix**: 
| EmpID | Name | Phone |
|-------|------|-------|
| 1 | Alice | 0911 |
| 1 | Alice | 0922 |

---

### Problem 10 — BCNF Check
R(A, B, C) with FD: A → B, B → C

```
CK = A
Is it in 3NF? A → B (A is CK ✓), B → C (B is NOT a CK but C depends on B)
  For B → C: B is not a superkey → violates BCNF
  But C is prime? No. So it's not even 3NF (transitive dependency B→C)

Answer: Not in 3NF (transitive dependency). Decompose to R1(A, B), R2(B, C)
```

---

## Set 3: ER Diagram Interpretation

### Problem 11 — Cardinality
A DEPARTMENT has many EMPLOYEES. An EMPLOYEE belongs to exactly one DEPARTMENT.

What is the cardinality?
- **DEPARTMENT to EMPLOYEE**: 1:N (one department has many employees)
- **EMPLOYEE to DEPARTMENT**: N:1 (many employees to one department) → actually 1:1
  Wait: each employee belongs to exactly ONE department. So EMPLOYEE:DEPARTMENT = N:1

**Answer**: 1:N relationship between DEPARTMENT and EMPLOYEE

---

### Problem 12 — Weak Entity
Can a ROOM exist without a HOTEL?

**Answer**: No — ROOM is likely a weak entity (existence depends on HOTEL)
- Identifying relationship: HOTEL "contains" ROOM
- ROOM's key includes HOTEL's key: (Hotel_id, Room_id)

---

## Set 4: Transaction & ACID

### Problem 13 — Transaction Trace
```
Transaction T1: Read X, X = X + 100, Write X
Transaction T2: Read X, X = X - 50, Write X

Initial X = 500

Schedule:
T1: Read X (X=500)
T2: Read X (X=500)     ← dirty read if T1 fails!
T1: X = X + 100 = 600
T1: Write X (X=600)
T1: COMMIT
T2: X = X - 50 = 450
T2: Write X (X=450)
T2: COMMIT

Final X = 450
```
**Problem**: If T2 had read X after T1 wrote but before T1 committed, T2 read 500 (old value). T2's computation is based on stale data.

---

### Problem 14 — Lost Update
```
Initial X = 100

T1: Read X (X=100)
T2: Read X (X=100)
T1: X = X + 50 → 150
T1: Write X
T2: X = X - 30 → 70
T2: Write X

Final X = 70   ← T1's update LOST!
Correct should be: 100 + 50 - 30 = 120
```

---

## Set 5: SQL Error Detection

### Problem 15 — Find the Error
```sql
SELECT Department, COUNT(*)
FROM Students
WHERE COUNT(*) > 5
GROUP BY Department;
```
**Error**: `WHERE` cannot use aggregate functions. Use `HAVING` instead:
```sql
SELECT Department, COUNT(*)
FROM Students
GROUP BY Department
HAVING COUNT(*) > 5;
```

---

### Problem 16 — Find the Error
```sql
INSERT INTO Students VALUES ('Alice');
```
**Error**: Missing column specification. If the table has more columns, this fails.
```sql
INSERT INTO Students (Name) VALUES ('Alice');
```

---

### Problem 17 — Find the Error
```sql
SELECT * FROM Employees ORDER BY Salary WHERE Salary > 50000;
```
**Error**: ORDER BY comes AFTER WHERE, not before.
```sql
SELECT * FROM Employees WHERE Salary > 50000 ORDER BY Salary;
```

---

### Problem 18 — Find the Error
```sql
UPDATE Students SET Grade = 'A' WHERE ;
```
**Error**: Missing condition after WHERE (would update ALL rows!)

---

## Set 6: Schema Design

### Problem 19 — Dormitory Database Design
Requirements:
- DORM(DormID, floorNumber) — PK = DormID
- STUDENT(IdNo, Name, Department) — PK = IdNo
- Six students per dorm
- Each student assigned to one dorm

**Design**:
```sql
CREATE TABLE DORM (
    DormID INT PRIMARY KEY,
    FloorNumber INT
);

CREATE TABLE STUDENT (
    IdNo INT PRIMARY KEY,
    Name VARCHAR(100),
    Department VARCHAR(50),
    DorID INT,
    FOREIGN KEY (DorID) REFERENCES DORM(DormID)
);
```
The FK is in STUDENT (many-to-one from STUDENT to DORM).

---

### Problem 20 — Library Database Design
Design tables for: BOOK(ISBN, Title, Author), MEMBER(MemberID, Name), BORROWING(MemberID, ISBN, Date)

```sql
CREATE TABLE BOOK (
    ISBN VARCHAR(20) PRIMARY KEY,
    Title VARCHAR(200),
    Author VARCHAR(100)
);

CREATE TABLE MEMBER (
    MemberID INT PRIMARY KEY,
    Name VARCHAR(100)
);

CREATE TABLE BORROWING (
    MemberID INT,
    ISBN VARCHAR(20),
    BorrowDate DATE,
    PRIMARY KEY (MemberID, ISBN, BorrowDate),
    FOREIGN KEY (MemberID) REFERENCES MEMBER(MemberID),
    FOREIGN KEY (ISBN) REFERENCES BOOK(ISBN)
);
```

---

## Common Exam Traps — Databases

| Trap | Explanation |
|------|-------------|
| **WHERE vs HAVING** | WHERE filters rows (before GROUP BY); HAVING filters groups |
| **INSERT INTO syntax** | `INSERT INTO table (cols) VALUES (vals)` — never `INSERT VALUES INTO` |
| **Strings in SQL** | Single quotes `' '`, not backticks `` ` `` |
| **DISTINCT ≠ UNIQUE** | DISTINCT is SQL keyword; UNIQUE is a constraint |
| **Cartesian JOIN** | Missing WHERE condition → every row matched with every other row |
| **Foreign Key NULL** | FK can be NULL (not every student needs a dorm assignment) |
| **Partial dependency** | Only relevant for composite primary keys |
| **1NF violation** | Multi-valued attributes in a single column (phone numbers) |
| **CASCADE direction** | ON UPDATE CASCADE changes FK to match new PK value |
| **Database approach** | Application-data dependency is a FILE SYSTEM problem, not DB |
