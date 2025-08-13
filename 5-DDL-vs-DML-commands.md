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
A: Usually no, DDL commands are auto-committed. DML commands can be rolled back if not committed.

---
*Extracted from transcript session 2.*
