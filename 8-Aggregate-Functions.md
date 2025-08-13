# 8-Aggregate-Functions

## What are Aggregate Functions?
Aggregate functions perform calculations on multiple rows and return a single value.

| Function | Description                |
|----------|----------------------------|
| COUNT    | Counts number of rows      |
| SUM      | Adds up values             |
| AVG      | Calculates average         |
| MIN      | Finds minimum value        |
| MAX      | Finds maximum value        |
| Function | Description                |
|----------|----------------------------|
| COUNT    | Counts rows or non-NULL values |
| SUM      | Adds up numeric values     |
| AVG      | Calculates average of numeric values |
| MIN      | Finds minimum value        |
| MAX      | Finds maximum value        |

## Example
```sql
SELECT COUNT(*) FROM employee;
SELECT AVG(salary) FROM employee;
SELECT COUNT(*) FROM employee;
SELECT SUM(salary) FROM employee;
SELECT AVG(age) FROM employee;
SELECT MIN(salary) FROM employee;
SELECT MAX(salary) FROM employee;
SELECT department, COUNT(*) FROM employee GROUP BY department;
SELECT department, AVG(salary) FROM employee GROUP BY department HAVING AVG(salary) > 20000;
```

## Q&A
**Q: Can aggregate functions be used with GROUP BY?**
A: Yes, to calculate values for each group.
**Q: What are aggregate functions?**
A: Functions that operate on sets of rows and return a single value.

**Q: Can you use aggregate functions with GROUP BY?**
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

