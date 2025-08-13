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

**Q: Can RANK() and DENSE_RANK() be used with PARTITION BY?**
A: Yes, you can partition data and rank within each partition.

**Q: When would you use DENSE_RANK() over RANK()?**
A: Use DENSE_RANK() when you want consecutive ranking without gaps.

**Q: How do ties affect RANK() and DENSE_RANK()?**
A: RANK() skips numbers for ties; DENSE_RANK() does not.

---

