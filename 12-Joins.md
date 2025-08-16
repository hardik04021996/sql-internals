# 12-Joins

## What are Joins?
Joins are used to combine rows from two or more tables based on a related column between them.

### Types of Joins
| Join Type   | Description                                      |
|-------------|--------------------------------------------------|
| INNER JOIN  | Returns records with matching values in both tables |
| LEFT JOIN   | Returns all records from the left table, and matched records from the right table |
| RIGHT JOIN  | Returns all records from the right table, and matched records from the left table |
| FULL JOIN   | Returns all records when there is a match in either table |

### Example
```sql
-- Sample output for joins (assuming sample data):

-- employee table:
| id | name   | dept_id | manager_id |
|----|--------|---------|------------|
| 1  | Alice  | 10      | NULL       |
| 2  | Bob    | 20      | 1          |
| 3  | Carol  | NULL    | 1          |

-- department table:
| dept_id | dept_name |
|---------|-----------|
| 10      | HR        |
| 20      | IT        |
| 30      | Finance   |

-- INNER JOIN:
SELECT e.name, d.dept_name
FROM employee e
INNER JOIN department d ON e.dept_id = d.dept_id;

| name  | dept_name |
|-------|-----------|
| Alice | HR        |
| Bob   | IT        |

-- LEFT JOIN:
SELECT e.name, d.dept_name
FROM employee e
LEFT JOIN department d ON e.dept_id = d.dept_id;

| name  | dept_name |
|-------|-----------|
| Alice | HR        |
| Bob   | IT        |
| Carol | NULL      |

-- RIGHT JOIN:
SELECT e.name, d.dept_name
FROM employee e
RIGHT JOIN department d ON e.dept_id = d.dept_id;

| name  | dept_name |
|-------|-----------|
| Alice | HR        |
| Bob   | IT        |
| NULL  | Finance   |

-- FULL JOIN:
SELECT e.name, d.dept_name
FROM employee e
FULL JOIN department d ON e.dept_id = d.dept_id;

| name  | dept_name |
|-------|-----------|
| Alice | HR        |
| Bob   | IT        |
| Carol | NULL      |
| NULL  | Finance   |

-- CROSS JOIN:
SELECT e.name, d.dept_name
FROM employee e
CROSS JOIN department d;

| name  | dept_name |
|-------|-----------|
| Alice | HR        |
| Alice | IT        |
| Alice | Finance   |
| Bob   | HR        |
| Bob   | IT        |
| Bob   | Finance   |
| Carol | HR        |
| Carol | IT        |
| Carol | Finance   |

-- SELF JOIN (employees with their manager):
SELECT a.name AS employee, b.name AS manager
FROM employee a
INNER JOIN employee b ON a.manager_id = b.id;

| employee | manager |
|----------|---------|
| Bob      | Alice   |
| Carol    | Alice   |
```

## Q&A
**Q: What is the difference between INNER JOIN and LEFT JOIN?**

A: INNER JOIN returns only matching records; LEFT JOIN returns all records from the left table and matching records from the right.

**Q: What is the default join in SQL?**

A: If you write JOIN without specifying a type, it is treated as INNER JOIN by default in most SQL databases, including MySQL and PostgreSQL.

**Q: What is a CROSS JOIN?**

A: Returns the Cartesian product of two tables.

**Q: What is the use case of CROSS JOIN?**

A: CROSS JOIN is useful when you need all possible combinations of rows from two tables. For example, generating a list of every employee with every department, or creating test data for all possible pairs.

**Q: What is a SELF JOIN?**

A: A table joined with itself.

**Q: Can you join more than two tables?**

A: Yes, you can join multiple tables in a single query.

**Q: What is an equi join?**

A: A join using equality comparison in the ON clause.

**Use case:**

Equi join is used when you want to combine rows from two tables based on matching values in specified columns.

**Example:**

```sql
SELECT e.name, d.dept_name
FROM employee e
JOIN department d ON e.dept_id = d.dept_id;
```
This query returns employee names along with their department names where the dept_id matches in both tables.

**Q: Is LEFT JOIN a type of equi join?**

A: Yes, LEFT JOIN can be an equi join if the join condition uses equality (e.g., ON a.id = b.id). Equi join refers to the condition, while LEFT JOIN refers to the type of join (all rows from the left table, matched rows from the right). Most LEFT JOINs in practice are equi joins.

**Example of LEFT JOIN that is not an equi join:**

Suppose you want to find all possible promotion opportunities for employees by listing all designations with a higher grade than the employee's current grade. This helps HR or managers see which designation an employee could be promoted to based on grade hierarchy.

**Input tables:**

-- employee table:
| id | name   | grade |
|----|--------|-------|
| 1  | Alice  | 1     |
| 2  | Bob    | 2     |
| 3  | Carol  | 1     |
| 4  | Stuart | 3     |

-- grade table:
| grade | designation       |
|-------|-------------------|
| 1     | Software Engineer |
| 2     | Senior Engineer   |
| 3     | Lead Engineer     |

**Query:**

```sql
SELECT e.name, g.designation
FROM employee e
LEFT JOIN grade g ON e.grade < g.grade;
```
This query lists each employee with all departments that have a higher grade than the employee's current grade. If an employee is already at the highest grade, the department columns will be NULL for that employee.

This query lists each employee with all designations that have a higher grade than the employee's current grade. If an employee is already at the highest grade, the designation column will be NULL for that employee.

**Sample output:**

| name   | designation      |
|--------|-----------------|
| Alice  | Senior Engineer |
| Alice  | Lead Engineer   |
| Bob    | Lead Engineer   |
| Carol  | Senior Engineer |
| Carol  | Lead Engineer   |
| Stuart | NULL            |

---

