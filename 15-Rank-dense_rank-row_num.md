# Window Functions: ROW_NUMBER(), RANK(), DENSE_RANK()

This note covers three important SQL window functions: `ROW_NUMBER()`, `RANK()`, and `DENSE_RANK()`. These functions allow you to assign numbers or ranks to rows in a result set, either globally or within partitions (groups), and are essential for advanced analytics, deduplication, and ranking scenarios.

## ROW_NUMBER()
Assigns a unique sequential integer to each row within a partition of a result set. Useful for ordering, pagination, and removing duplicates.

### Example: ROW_NUMBER() by Department
```sql
SELECT name, salary, department,
  ROW_NUMBER() OVER (PARTITION BY department ORDER BY salary DESC) AS row_num
FROM employee;
```

## RANK() and DENSE_RANK()
- **RANK()**: Assigns a rank to each row within a partition, with gaps for ties.
- **DENSE_RANK()**: Assigns a rank to each row within a partition, without gaps for ties.

### Example: RANK(), DENSE_RANK() and ROW_NUMBER() together
```sql
SELECT name, salary,
  RANK() OVER (ORDER BY salary DESC) AS rank,
  DENSE_RANK() OVER (ORDER BY salary DESC) AS dense_rank,
  ROW_NUMBER() OVER (ORDER BY salary DESC) AS row_num
FROM employee;
```

Sample input:
| name   | salary | department |
|--------|--------|------------|
| Alice  | 25000  | HR         |
| Bob    | 30000  | IT         |
| Carol  | 25000  | HR         |
| Dave   | 20000  | IT         |

Sample output:
| name   | salary | rank | dense_rank | row_num |
|--------|--------|------|------------|---------|
| Bob    | 30000  | 1    | 1          | 1       |
| Alice  | 25000  | 2    | 2          | 2       |
| Carol  | 25000  | 2    | 2          | 3       |
| Dave   | 20000  | 4    | 3          | 4       |

---

## Q&A
**Q: What does ROW_NUMBER() do?**

A: It gives a unique row number for each row within a partition.

**Q: What happens if ORDER BY is omitted in ROW_NUMBER()?**

A: ROW_NUMBER() will assign numbers arbitrarily; always specify ORDER BY for predictable results.

**Q: Can ROW_NUMBER() be used to remove duplicates?**

A: Yes, you can use ROW_NUMBER() in a subquery to filter out duplicate rows.

***Example:***

```sql
SELECT name, salary
FROM (
  SELECT name, salary,
    ROW_NUMBER() OVER (PARTITION BY name ORDER BY salary DESC) AS rn
  FROM employee
) t
WHERE rn = 1;
```
Sample input:
| name   | salary |
|--------|--------|
| Alice  | 25000  |
| Alice  | 20000  |
| Bob    | 15000  |
| Bob    | 18000  |
| Carol  | 30000  |

Sample output:
| name   | salary |
|--------|--------|
| Alice  | 25000  |
| Bob    | 18000  |
| Carol  | 30000  |

**Q: Difference between ROW_NUMBER() and RANK()?**

A: ROW_NUMBER() always gives unique numbers; RANK() gives same rank for ties.

**Q: What is the difference between RANK() and DENSE_RANK()?**

A: RANK() leaves gaps after ties; DENSE_RANK() does not.

**Q: Can RANK() and DENSE_RANK() be used with PARTITION BY?**

A: Yes, you can partition data and rank within each partition.

---
