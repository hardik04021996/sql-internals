# 17-Indexes-and-Order-of-Execution-in-SQL

## Indexes
Indexes are special lookup tables that the database search engine can use to speed up data retrieval.
- Improve query performance.
- Can be created on one or more columns.

### Example
```sql
CREATE INDEX idx_employee_name ON employee(name);
```

## Order of Execution in SQL
The typical order in which SQL clauses are executed:
1. FROM
2. WHERE
3. GROUP BY
4. HAVING
5. SELECT
6. ORDER BY
7. LIMIT

| Step | Clause     | Purpose                        |
|------|------------|--------------------------------|
| 1    | FROM       | Choose and join tables         |
| 2    | WHERE      | Filter rows                    |
| 3    | GROUP BY   | Group rows                     |
| 4    | HAVING     | Filter groups                  |
| 5    | SELECT     | Choose columns/expressions     |
| 6    | ORDER BY   | Sort results                   |
| 7    | LIMIT      | Limit number of rows           |

## Q&A
**Q: Why use indexes?**
A: To speed up data retrieval operations.

**Q: What is the order of SQL execution?**
A: See the table above for the standard order.

---
*Extracted from transcript session 3.*
