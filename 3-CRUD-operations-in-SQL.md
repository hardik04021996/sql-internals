# 3-CRUD-operations-in-SQL

## What is CRUD?
CRUD stands for Create, Read, Update, and Delete. These are the four basic operations for managing records in a database table.

| Operation | SQL Command | Description                        |
|-----------|-------------|------------------------------------|
| Create    | INSERT      | Add new records to a table         |
| Read      | SELECT      | Retrieve records from a table      |
| Update    | UPDATE      | Modify existing records            |
| Delete    | DELETE      | Remove records from a table        |

## Example Table Structure
```sql
CREATE TABLE employee (
  first_name VARCHAR(20),
  middle_name VARCHAR(20),
  last_name VARCHAR(20),
  age INT,
  salary INT,
  location VARCHAR(20)
);
```


## Example CRUD Operations
- **Insert:**
  ```sql
  INSERT INTO employee (first_name, last_name, age, salary, location)
  VALUES ('Kapil', 'Sharma', 28, 10000, 'Bangalore');
  -- Best practice: Always specify column names for clarity and to avoid errors if table structure changes.
  ```
- **Read:**
  ```sql
  SELECT * FROM employee;
  -- Use WHERE clause to filter results:
  SELECT * FROM employee WHERE location = 'Bangalore';
  ```
- **Update:**
  ```sql
  UPDATE employee SET salary = 12000 WHERE first_name = 'Kapil';
  -- Always use a WHERE clause to avoid updating all records by mistake.
  ```
- **Delete:**
  ```sql
  DELETE FROM employee WHERE first_name = 'Kapil';
  -- Always use a WHERE clause to avoid deleting all records.
  ```


## Q&A
**Q: What happens if you try to insert a record with missing columns?**
A: You must specify the columns you are inserting into, or provide values for all columns. Otherwise, you will get a column count mismatch error.

**Q: What is NULL in SQL?**
A: NULL represents an unknown or missing value, not zero. It is not equal to zero or an empty string.

**Q: What happens if you omit the WHERE clause in UPDATE or DELETE?**
A: All rows in the table will be updated or deleted, which is usually a critical mistake.

**Q: How do you insert multiple rows at once?**
A: Use a single INSERT statement with multiple value sets:
```sql
INSERT INTO employee (first_name, last_name, age, salary, location)
VALUES ('A', 'B', 25, 10000, 'City1'),
       ('C', 'D', 30, 20000, 'City2');
```

---

