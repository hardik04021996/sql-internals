# 18-SQL-WITH-clause-common-table-expression

## SQL WITH Clause (Common Table Expression - CTE)

The WITH clause lets you define a temporary result set, called a Common Table Expression (CTE), that you can reference within SELECT, INSERT, UPDATE, or DELETE statements. CTEs are especially useful for:
- Breaking down complex queries into logical, readable steps
- Reusing the same result set multiple times in a query
- Simplifying queries that involve filtering, joining, or aggregating data
- Handling hierarchical or recursive data (e.g., organization charts, tree structures)

CTEs are not stored as permanent tables; they exist only for the duration of the query.

### Syntax
```sql
WITH cte_name AS (
  SELECT ...
)
SELECT * FROM cte_name;
```

### Example

#### Example 1: Filtering and Reusing Results
```sql
WITH high_salary AS (
  SELECT * FROM employee WHERE salary > 20000
)
SELECT * FROM high_salary WHERE location = 'Bangalore';
```
This first filters employees with salary > 20000, then selects only those in Bangalore from the filtered set.

Sample input:
| name   | salary | location   |
|--------|--------|------------|
| Alice  | 25000  | Bangalore  |
| Bob    | 18000  | Mumbai     |
| Carol  | 30000  | Bangalore  |
| Dave   | 22000  | Delhi      |

Sample output:
| name   | salary | location   |
|--------|--------|------------|
| Alice  | 25000  | Bangalore  |
| Carol  | 30000  | Bangalore  |

## Q&A
**Q: What are practical use cases for CTEs?**
A: CTEs are great for:
- Breaking up multi-step queries (e.g., filter, then aggregate)
- Making queries easier to read and maintain
- Handling recursive problems (e.g., finding all employees in a management hierarchy)
- Reusing the same logic multiple times in a query

**Q: What is a recursive CTE?**
A: A recursive CTE references itself to solve problems like traversing hierarchies or generating sequences. For example, finding all subordinates of a manager.

**Example: Recursive CTE for Hierarchy**
```sql
WITH employee_hierarchy AS (
  SELECT id, name, manager_id
  FROM employee
  WHERE manager_id IS NULL
  UNION ALL
  SELECT e.id, e.name, e.manager_id
  FROM employee e
  JOIN employee_hierarchy eh ON e.manager_id = eh.id
)
SELECT * FROM employee_hierarchy;
```
This finds all employees under the top-level manager.

**Q: Why use a CTE?**

A: CTEs help simplify complex queries by allowing you to break them into logical building blocks. Instead of writing long, nested subqueries, you can define intermediate results with clear names, making your SQL easier to read, debug, and maintain. CTEs also allow you to reuse the same result set multiple times in a query, which is not possible with subqueries.

**Q: Can CTEs be recursive?**

A: Yes, CTEs can reference themselves, which is called a recursive CTE. Recursive CTEs are useful for problems like traversing organizational hierarchies, finding all descendants in a tree, or generating sequences. The recursive part repeatedly joins the CTE to itself until a condition is met, allowing you to process hierarchical data in a single query.

**Q: Difference between CTE and subquery?**

A: CTEs and subqueries both allow you to create temporary result sets, but CTEs are defined at the start of a query and can be referenced multiple times, making them more reusable and readable. Subqueries are written inline and can only be used once per query. CTEs are better for breaking up complex logic, especially when the same result set is needed in multiple places.

**Q: Can you use multiple CTEs in one query?**

A: Yes, you can define multiple CTEs in a single query by separating them with commas. Each CTE can build on the previous ones, allowing you to structure multi-step logic in a clear and organized way. This is especially useful for complex reporting or analytics queries where you need several intermediate results.

---
