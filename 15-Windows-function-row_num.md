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

**Q: What happens if ORDER BY is omitted in ROW_NUMBER()?**
A: ROW_NUMBER() will assign numbers arbitrarily; always specify ORDER BY for predictable results.

**Q: Can ROW_NUMBER() be used to remove duplicates?**
A: Yes, you can use ROW_NUMBER() in a subquery to filter out duplicate rows.

**Q: Difference between ROW_NUMBER() and RANK()?**
A: ROW_NUMBER() always gives unique numbers; RANK() gives same rank for ties.

---

