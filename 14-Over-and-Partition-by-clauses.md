# 14-Over-and-Partition-by-clauses


## OVER() and PARTITION BY in SQL
These clauses are used with window functions to perform calculations across a set of table rows related to the current row. They allow you to perform aggregations and analytics without collapsing rows like GROUP BY does.


### OVER()
Defines the window (set of rows) for the function. It can be used alone or with PARTITION BY and ORDER BY to control how the function is applied.


### PARTITION BY
Divides the result set into partitions (groups of rows) to which the window function is applied. Each partition is processed separately.


### Example 1: Average Salary by Department
```sql
SELECT name, department, salary,
  AVG(salary) OVER (PARTITION BY department) AS avg_dept_salary
FROM employee;
```
This shows each employee's salary and the average salary for their department.

Sample output:
| name   | department | salary | avg_dept_salary |
|--------|------------|--------|-----------------|
| Alice  | HR         | 25000  | 20000           |
| Bob    | HR         | 15000  | 20000           |
| Carol  | IT         | 30000  | 30000           |

### Example 2: Running Total with ORDER BY
```sql
SELECT name, salary,
  SUM(salary) OVER (ORDER BY salary) AS running_total
FROM employee;
```
This calculates a running total of salaries ordered by salary.

Sample output:
| name   | salary | running_total |
|--------|--------|---------------|
| Bob    | 15000  | 15000         |
| Alice  | 25000  | 40000         |
| Carol  | 30000  | 70000         |

### Example 3: Partition and Order
```sql
SELECT name, department, salary,
  RANK() OVER (PARTITION BY department ORDER BY salary DESC) AS dept_rank
FROM employee;
```
This ranks employees within each department by salary.

Sample output:
| name   | department | salary | dept_rank |
|--------|------------|--------|-----------|
| Alice  | HR         | 25000  | 1         |
| Bob    | HR         | 15000  | 2         |
| Carol  | IT         | 30000  | 1         |


## Q&A
**Q: What is the use of PARTITION BY?**

A: It divides the result set into groups for window functions, so calculations like averages or ranks are done within each group.

**Q: How is OVER() different from GROUP BY?**

A: OVER() with window functions does not collapse rows; it adds calculated columns to each row. GROUP BY collapses rows into groups.

**Q: Can you use ORDER BY inside OVER()?**

A: Yes, ORDER BY inside OVER() defines the order for calculations like running totals or row numbers.

**Q: Can you use both PARTITION BY and ORDER BY together?**

A: Yes, you can partition the data and then order within each partition for advanced analytics.

**Q: What is a window frame?**

A: It defines the subset of rows for window calculations, e.g., ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW.

**Q: Can you use window functions with aggregate functions?**

A: Yes, window functions can be used with aggregates for advanced analytics.

---

