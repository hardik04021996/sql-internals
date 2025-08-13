# 18-SQL-WITH-clause-common-table-expression

## SQL WITH Clause (Common Table Expression - CTE)
The WITH clause allows you to define a temporary result set (CTE) that can be referenced within a SELECT, INSERT, UPDATE, or DELETE statement.

### Syntax
```sql
WITH cte_name AS (
  SELECT ...
)
SELECT * FROM cte_name;
```

### Example
```sql
WITH high_salary AS (
  SELECT * FROM employee WHERE salary > 20000
)
SELECT * FROM high_salary WHERE location = 'Bangalore';
```

## Q&A
**Q: Why use a CTE?**
A: To simplify complex queries and improve readability by breaking them into logical building blocks.

---
*Extracted from transcript session 3.*
