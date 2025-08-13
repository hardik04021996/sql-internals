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
Explanation: This is called referential integrity. The foreign key constraint checks that every value in the foreign key column matches a value in the referenced primary key column. If you try to insert or update a value that does not exist in the referenced table, the database will reject the operation to prevent invalid relationships.

**Q: What is ON DELETE CASCADE?**
A: If the referenced row is deleted, all related rows in the child table are also deleted automatically.
Explanation: ON DELETE CASCADE is an option you can set on a foreign key constraint. It means that when a row in the parent table (referenced table) is deleted, all rows in the child table (the table with the foreign key) that reference that row will also be deleted. This helps maintain data consistency and prevents orphaned records in the child table.

**How to use CASCADE and is it optional?**
CASCADE is an optional action you can specify when defining a foreign key constraint. By default, if you do not specify CASCADE, the database will prevent deletion of a parent row if child rows exist (restrict behavior). To use CASCADE, add `ON DELETE CASCADE` or `ON UPDATE CASCADE` to your foreign key definition:

```sql
CREATE TABLE employee (
  id INT PRIMARY KEY,
  name VARCHAR(50),
  dept_id INT,
  FOREIGN KEY (dept_id) REFERENCES department(dept_id) ON DELETE CASCADE
);
```
This means if a department is deleted, all employees in that department are also deleted. You can choose to use CASCADE or not, depending on your data integrity needs.

**If you don't use CASCADE, will UPDATE and DELETE work?**
If you do not specify CASCADE, the default behavior is RESTRICT or NO ACTION. This means:
- **DELETE:** If you try to delete a parent row (e.g., a department) that has related child rows (e.g., employees), the database will prevent the deletion and throw an error to protect referential integrity.
- **UPDATE:** If you try to update the referenced key in the parent table, the database will also prevent the update if child rows exist, unless you specify `ON UPDATE CASCADE` or another action (like SET NULL or SET DEFAULT).
In summary, without CASCADE, you cannot delete or update a parent row if child rows reference it, unless you first remove or update the child rows.

**If you delete or update the referenced row, what happens to the parent row?**
In a foreign key relationship, the referenced row is in the parent table, and the foreign key is in the child table. If you delete or update the referenced row (parent), the effect on the child rows depends on the foreign key constraint options:
- If CASCADE is set, child rows are automatically deleted or updated to match the change in the parent.
- If RESTRICT or NO ACTION is set (default), the database will prevent the deletion or update if child rows exist, to maintain referential integrity.
- Other options include SET NULL (child foreign key is set to NULL) or SET DEFAULT (child foreign key is set to its default value).
The parent row itself is simply deleted or updated as requested; the constraint controls what happens to the child rows that reference it.

---

