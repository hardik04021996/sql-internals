# 8-Aggregate-Functions

## What are Aggregate Functions?
Aggregate functions perform calculations on multiple rows and return a single value.

| Function | Description                       |
|----------|-----------------------------------|
| COUNT    | Counts rows or non-NULL values    |
| SUM      | Adds up numeric values            |
| AVG      | Calculates average of numeric values |
| MIN      | Finds minimum value               |
| MAX      | Finds maximum value               |

## Example
```sql
-- Count all employees
SELECT COUNT(*) FROM employee;

-- Average salary of all employees
SELECT AVG(salary) FROM employee;

-- Total salary paid
SELECT SUM(salary) FROM employee;

-- Minimum and maximum salary
SELECT MIN(salary) FROM employee;
SELECT MAX(salary) FROM employee;

-- Count employees per department
SELECT department, COUNT(*) FROM employee GROUP BY department;

-- Average salary per department, only departments with avg salary > 20000
SELECT department, AVG(salary) FROM employee GROUP BY department HAVING AVG(salary) > 20000;
```

## Q&A
**Q: What are aggregate functions?**

A: Functions that operate on sets of rows and return a single value (e.g., COUNT, SUM, AVG, MIN, MAX).

**Q: Can aggregate functions be used with GROUP BY?**

A: Yes, GROUP BY groups rows and aggregate functions calculate values for each group.

**Q: What does HAVING do?**

A: HAVING filters groups after aggregation, similar to WHERE for rows.

**Q: How are NULLs handled in aggregate functions?**

A: Most aggregate functions ignore NULL values except COUNT(*), which counts all rows.

**Q: What happens if there is a data type mismatch?**

A: SQL will throw an error if you try to use aggregate functions on incompatible data types (e.g., SUM on a string column).

**Q: Are aggregate functions case sensitive?**

A: Aggregate functions themselves are not case sensitive, but string comparisons in WHERE or GROUP BY may be case sensitive depending on database settings.

---

