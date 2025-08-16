# 5-DDL-vs-DML-commands


## DDL (Data Definition Language)
- Used to define and modify the structure of database objects (tables, schemas, etc).
- Common DDL commands: CREATE, ALTER, DROP, TRUNCATE.
- DDL changes are auto-committed (cannot be rolled back in most databases).

| Command | Description                  |
|---------|------------------------------|
| CREATE  | Create a new table/database  |
| ALTER   | Modify an existing table     |
| DROP    | Delete a table/database      |
| TRUNCATE| Remove all records from table|


## DML (Data Manipulation Language)
- Used to manage data within tables.
- Common DML commands: INSERT, UPDATE, DELETE, SELECT.
- DML changes can be rolled back or committed (transaction control).

| Command | Description                  |
|---------|------------------------------|
| INSERT  | Add new records              |
| UPDATE  | Modify existing records      |
| DELETE  | Remove records               |
| SELECT  | Retrieve records             |


## Q&A
**Q: What is the difference between DDL and DML?**
A: DDL changes the structure of the database (tables, schemas); DML changes the data inside tables.

**Q: Can you roll back a DDL command?**
A: Usually no, DDL commands (like CREATE, ALTER, DROP) are auto-committed, meaning changes are saved immediately and cannot be undone with a rollback. 
This is because structural changes to the database are considered permanent as soon as they are executed.

**Q: How do rollbacks and commits work in SQL?**
A: Rollbacks and commits are part of transaction control in SQL, mainly used with DML commands (INSERT, UPDATE, DELETE).


**Example:**
```sql
BEGIN;
UPDATE employee SET salary = 20000 WHERE id = 1;
COMMIT;
ROLLBACK;
```


**How it works:**
- When you start a transaction (with BEGIN or START TRANSACTION), changes are not visible to other users and are not permanent until you COMMIT.
- If you ROLLBACK, all changes since the last BEGIN are undone and the database returns to its previous state.
- DML commands are transactional and can be rolled back, but DDL commands are auto-committed and cannot be rolled back in most databases.

**What happens internally:**
- **Without BEGIN/COMMIT/ROLLBACK (Autocommit Mode):**
  - Each DML statement (INSERT, UPDATE, DELETE) is executed and committed immediately.
  - Changes are permanent as soon as the statement finishes and cannot be undone.
  - Most databases default to autocommit mode unless you explicitly start a transaction.
  - Example:
    ```sql
    UPDATE employee SET salary = 20000 WHERE id = 1;
    -- Change is saved instantly and cannot be rolled back.
    ```
- **With BEGIN/COMMIT/ROLLBACK (Explicit Transaction):**
  - BEGIN (or START TRANSACTION) starts a transaction block.
  - Changes made by DML statements are not visible to other users and are not permanent until you COMMIT.
  - You can make multiple changes and then either COMMIT (save all changes) or ROLLBACK (undo all changes since BEGIN).
  - This allows you to group several operations and ensure either all succeed or none are applied (atomicity).
  - Example:
    ```sql
    BEGIN;
    UPDATE employee SET salary = 20000 WHERE id = 1;
    DELETE FROM employee WHERE id = 2;
    -- If everything is correct:
    COMMIT;   -- All changes are saved
    -- If you want to undo:
    ROLLBACK; -- All changes since BEGIN are undone
    ```

**How ACID is followed in complex queries with COMMIT and ROLLBACK:**
When you run a query or a series of queries inside a transaction (using BEGIN), the database ensures ACID properties:

- **Atomicity:** All operations within the transaction are treated as a single unit. Either all succeed (COMMIT) or none are applied (ROLLBACK).
- **Consistency:** The database moves from one valid state to another. If any part of the transaction fails, ROLLBACK restores the previous consistent state.
- **Isolation:** Changes made in the transaction are not visible to other users until COMMIT. Other transactions cannot see partial results.
- **Durability:** Once COMMIT is issued, changes are permanently saved, even if there is a system failure.

**Example:**
Suppose you want to transfer money between two accounts:
```sql
BEGIN;
UPDATE accounts SET balance = balance - 100 WHERE id = 1;
UPDATE accounts SET balance = balance + 100 WHERE id = 2;
-- If both succeed:
COMMIT;
-- If any error occurs (e.g., insufficient funds):
ROLLBACK;
```
If any part of the transaction fails (e.g., the first UPDATE fails due to insufficient funds), ROLLBACK undoes all changes, ensuring atomicity and consistency. Only when both updates succeed do you COMMIT, making the transfer permanent and visible to others.

**Single query with subqueries and ACID in autocommit mode:**
If you run a single SQL statement—even if it contains multiple subqueries or operations—without explicitly starting a transaction (BEGIN), most databases operate in autocommit mode. The entire statement is treated as a single atomic operation: if it succeeds, all changes are committed immediately; if it fails, no changes are applied. You cannot use ROLLBACK to undo the changes after the statement completes, because the commit happens automatically.

ACID properties are still followed for that statement:
- **Atomicity:** The statement is all-or-nothing; either all changes succeed or none are applied.
- **Consistency:** The database remains in a valid state before and after the statement.
- **Isolation:** Other users do not see partial results during execution.
- **Durability:** Once the statement finishes, changes are permanent.

**Example:**
```sql
UPDATE accounts
SET balance = balance - 100
WHERE id = 1 AND balance >= 100 AND EXISTS (
  SELECT 1 FROM accounts WHERE id = 2
);
```
This query deducts 100 from account 1 only if account 1 has at least 100 balance (sufficient funds) and account 2 exists. The subquery in the WHERE clause ensures account 2 exists, and the balance check ensures atomicity and correctness. If either condition fails, no change is made. The entire statement is atomic in autocommit mode and follows ACID properties for that operation.

---

