# 16-Windows-function-rank-dense_rank

## RANK() and DENSE_RANK() Window Functions
- **RANK()**: Assigns a rank to each row within a partition, with gaps for ties.
- **DENSE_RANK()**: Assigns a rank to each row within a partition, without gaps for ties.

### Example
```sql
SELECT name, salary,
  RANK() OVER (ORDER BY salary DESC) AS rank,
  DENSE_RANK() OVER (ORDER BY salary DESC) AS dense_rank
FROM employee;
```

## Q&A
**Q: What is the difference between RANK() and DENSE_RANK()?**
A: RANK() leaves gaps after ties; DENSE_RANK() does not.

---
*Extracted from transcript session 3.*
