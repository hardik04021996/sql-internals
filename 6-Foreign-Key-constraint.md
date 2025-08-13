# 6-Foreign-Key-constraint


## What is a Foreign Key?
A foreign key is a column or set of columns in one table that refers to the primary key in another table. It is used to maintain referential integrity between tables.

- Ensures that the value in the foreign key column matches a value in the referenced table's primary key.
- Prevents actions that would destroy links between tables.
- Enforces valid relationships between tables (e.g., every employee must belong to a valid department).
- Can be used to cascade updates or deletes (ON UPDATE CASCADE, ON DELETE CASCADE).

## Example
```sql
CREATE TABLE department (
  dept_id INT PRIMARY KEY,
  dept_name VARCHAR(50)
);

CREATE TABLE employee (
  id INT PRIMARY KEY,
  name VARCHAR(50),
  dept_id INT,
  FOREIGN KEY (dept_id) REFERENCES department(dept_id)
);
```


## Q&A
**Q: Why use a foreign key?**
A: To ensure data consistency and enforce relationships between tables. It prevents orphan records.

**Q: Can a foreign key be NULL?**
A: Yes, if the relationship is optional. If not, use NOT NULL constraint.

**Q: What happens if you try to insert a value in the foreign key column that does not exist in the referenced table?**
A: The database will throw an error and prevent the insert or update.

**Q: What is ON DELETE CASCADE?**
A: If the referenced row is deleted, all related rows in the child table are also deleted automatically.

---
*Extracted from transcript session 3.*
