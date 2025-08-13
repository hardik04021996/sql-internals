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

## Example
```sql
SELECT COUNT(*) FROM employee;
SELECT AVG(salary) FROM employee;
```

## Q&A
**Q: Can aggregate functions be used with GROUP BY?**
A: Yes, to calculate values for each group.

---
*Extracted from transcript session 3.*
