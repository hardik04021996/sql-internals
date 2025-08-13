# 11-CASE-WHEN-statements

## CASE WHEN in SQL
The CASE statement is used for conditional logic in SQL queries, similar to if-else in programming.

### Syntax
```sql
SELECT column,
  CASE
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
    ELSE resultN
  END AS alias_name
FROM table_name;
```

### Example
```sql
SELECT name, salary,
  CASE
    WHEN salary > 20000 THEN 'High'
    WHEN salary > 10000 THEN 'Medium'
    ELSE 'Low'
  END AS salary_category
FROM employee;
```

## Q&A
**Q: What is the use of CASE WHEN?**
A: To implement conditional logic in SQL queries.

---
*Extracted from transcript session 2.*
