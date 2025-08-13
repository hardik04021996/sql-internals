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

**Q: What is a composite index?**
A: An index on multiple columns; improves queries filtering on those columns.

**Q: Can indexes slow down performance?**
A: Yes, indexes speed up reads but slow down writes/updates.

**Q: What is a covering index?**
A: An index that contains all columns needed for a query, allowing the database to avoid reading the table.

**Q: Why is understanding order of execution important?**
A: It helps write efficient queries and avoid logical errors.

---

