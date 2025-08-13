# 15-Windows-function-row_num

## ROW_NUMBER() Window Function
Assigns a unique sequential integer to rows within a partition of a result set.

### Example
```sql
SELECT name, salary,
  ROW_NUMBER() OVER (PARTITION BY department ORDER BY salary DESC) AS row_num
FROM employee;
```

## Q&A
**Q: What does ROW_NUMBER() do?**
A: It gives a unique row number for each row within a partition.

---
*Extracted from transcript session 3.*
