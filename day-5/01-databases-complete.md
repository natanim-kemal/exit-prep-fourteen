# Databases — Study Notes

## 1. Normalization

**Normal forms** eliminate data redundancy and anomalies:
- **1NF**: atomic values, no repeating groups
- **2NF**: 1NF + no partial dependencies
- **3NF**: 2NF + no transitive dependencies
- **BCNF**: 3NF + every determinant is a candidate key

Higher normal forms remove specific types of anomalies:
- **Update anomaly**: updating one fact requires updating multiple rows
- **Insertion anomaly**: unable to insert data due to missing other data
- **Deletion anomaly**: deleting one fact accidentally deletes others

## 2. Transaction Properties (ACID)

- **Atomicity**: all or nothing — transaction completes fully or not at all
- **Consistency**: transaction brings database from one valid state to another
- **Isolation**: concurrent transactions don't interfere with each other
- **Durability**: committed changes persist even after system failure

**Transaction isolation levels**: Read Uncommitted, Read Committed, Repeatable Read, Serializable.

## 3. SQL Concepts

**DDL** (Data Definition Language): `CREATE`, `ALTER`, `DROP`, `TRUNCATE`
**DML** (Data Manipulation Language): `SELECT`, `INSERT`, `UPDATE`, `DELETE`
**DCL** (Data Control Language): `GRANT`, `REVOKE`

**Key SQL commands**:
- `SELECT ... FROM ... WHERE ... GROUP BY ... HAVING ... ORDER BY ... LIMIT`
- `JOIN`: `INNER JOIN`, `LEFT JOIN`, `RIGHT JOIN`, `FULL OUTER JOIN` — combines rows from multiple tables based on a condition
- `CREATE TABLE`, `ALTER TABLE` (add/modify/drop columns)
- **CASCADE**: automatically deletes/updates referencing rows when referenced row is deleted/updated

## 4. Database Design

**Conceptual design**: ER diagram with entities, attributes, relationships (1:1, 1:M, M:N).
**Logical design**: mapping ER to relational model (tables, primary keys, foreign keys).
**Physical design**: storage structures, indexing.

**Foreign key**: enforces referential integrity between related tables. Links a column to the primary key of another table. Can be NULL or a valid referenced value.

**Primary key**: uniquely identifies each row in a table; must be NOT NULL and unique.

**DISTINCT**: removes duplicate rows from query results.

**Filter order**: `WHERE` before `GROUP BY`, `HAVING` after `GROUP BY`.

## 5. Views vs Tables

- **View**: virtual table based on a SELECT query; doesn't store data physically; can simplify complex queries and restrict data access.
- **Table**: physically stores data.

## 6. Indexing

Indexes speed up data retrieval but slow down write operations (INSERT, UPDATE, DELETE). Types: B-tree, hash, bitmap, full-text. Primary key creates a clustered index by default.

## 7. Database Security

- **SQL Injection**: prevented by parameterized queries/prepared statements
- **Encryption**: encrypt sensitive data at rest (TDE, column-level encryption) and in transit (SSL/TLS)
- **Access control**: GRANT/REVOKE permissions; principle of least privilege
- **Backup and recovery**: regular backups to prevent data loss

## 8. Key Differences

- **DROP vs DELETE**: DROP removes table structure; DELETE removes rows (can be rolled back)
- **TRUNCATE vs DELETE**: TRUNCATE removes all rows (faster, cannot rollback); DELETE can have WHERE clause
- **CHAR vs VARCHAR**: CHAR is fixed-length (padded); VARCHAR is variable-length
- **Stored Procedures**: precompiled SQL statements stored on the server (benefit: performance, reusability, security)
