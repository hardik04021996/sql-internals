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
A: DDL changes the structure of the database (tables, schemas), DML changes the data inside tables.


**Q: Can you roll back a DDL command?**
A: Usually no, DDL commands (like CREATE, ALTER, DROP) are auto-committed, meaning changes are saved immediately and cannot be undone with a rollback. This is because structural changes to the database are considered permanent as soon as they are executed.

**Q: How do rollbacks and commits work in SQL?**
A: Rollbacks and commits are part of transaction control in SQL, mainly used with DML commands (INSERT, UPDATE, DELETE).

- **COMMIT**: Saves all changes made during the current transaction to the database permanently.
- **ROLLBACK**: Undoes all changes made during the current transaction, reverting the database to its previous state.

**Example:**
```sql
BEGIN;
UPDATE employee SET salary = 20000 WHERE id = 1;
-- If you want to save the change:
COMMIT;
-- If you want to undo the change:
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

---

