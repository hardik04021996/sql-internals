# 7-Distinct-OrderBy-Limit-Like-clause-in-SQL

## DISTINCT
Removes duplicate records from the result set.

```sql
SELECT DISTINCT column_name FROM table_name;
SELECT DISTINCT column1, column2 FROM table_name; -- unique combinations
```

## ORDER BY
Sorts the result set by one or more columns.

```sql
SELECT * FROM table_name ORDER BY column_name ASC; -- ascending
SELECT * FROM table_name ORDER BY column_name DESC; -- descending
SELECT * FROM table_name ORDER BY department ASC, salary DESC; -- multi-column sort
```
This sorts first by department, then by salary within each department.

## LIMIT
Restricts the number of records returned.

```sql
SELECT * FROM table_name LIMIT 10;
SELECT * FROM table_name LIMIT 10 OFFSET 20; -- pagination
```
This skips the first 20 records and returns the next 10.

## LIKE
Used for pattern matching in WHERE clause.

```sql
SELECT * FROM table_name WHERE column_name LIKE 'A%'; -- starts with 'A'
SELECT * FROM table_name WHERE name LIKE '%son'; -- ends with 'son'
SELECT * FROM table_name WHERE name LIKE '_a%'; -- second letter is 'a'
```

## Q&A
**Q: What does DISTINCT do?**

A: Removes duplicate values from the result set.

**Q: Can DISTINCT be used with multiple columns?**

A: Yes, it returns unique combinations of the selected columns.

**Q: Can you sort by more than one column?**

A: Yes, separate columns with commas in ORDER BY.

**Q: How do you sort results?**

A: Use ORDER BY with ASC (ascending) or DESC (descending).

**Q: How do you paginate results?**

A: Use LIMIT with OFFSET.

**Q: How to limit results?**

A: Use LIMIT with the desired number.

**Q: What do % and _ mean in LIKE?**

A: % matches any sequence of characters; _ matches a single character.

**Q: How to search for patterns?**

A: Use LIKE with wildcards (% or _).

**Q: What is the order of execution of SQL clauses?**

A: The typical order is: FROM, WHERE, GROUP BY, HAVING, SELECT, ORDER BY, LIMIT. This affects how queries are processed and can impact results.

**Q: Why does SELECT DISTINCT with ORDER BY sometimes fail?**

A: If you use SELECT DISTINCT on one column and ORDER BY another, SQL may throw an error because DISTINCT is applied before ORDER BY, and the ORDER BY column may not be available after projection. This is a common interview question about SQL internals.

**Example:**

```sql
SELECT DISTINCT department FROM employee ORDER BY salary DESC;
```
This query fails because after applying DISTINCT, only the 'department' column remains, and 'salary' is not available for ORDER BY. To fix this, include 'salary' in the SELECT list or use a subquery:

```sql
SELECT department FROM (
  SELECT department, salary FROM employee
  ORDER BY salary DESC
) AS sub
GROUP BY department;
```
Or, if you want to order departments by their highest salary:
```sql
SELECT department, MAX(salary) AS max_salary
FROM employee
GROUP BY department
ORDER BY max_salary DESC;
```
This way, the column used in ORDER BY is present in the result set.
If you want only the department names ordered by their highest salary, you can use a subquery:

```sql
SELECT department FROM (
  SELECT department, MAX(salary) AS max_salary
  FROM employee
  GROUP BY department
  ORDER BY max_salary DESC
) AS ranked_departments;
```
This will return just the department names, ordered by their highest salary. The ORDER BY in the subquery ensures the departments are ranked before projection.

**Note:**

If you use GROUP BY without any aggregate function (like in the example below):

```sql
SELECT department FROM (
  SELECT department, salary FROM employee
  ORDER BY salary DESC
) AS sub
GROUP BY department;
```
Most SQL databases will return one row per group (department), but which row is chosen is not guaranteed unless you use an aggregate function. The result may be unpredictable, and some databases (like MySQL in certain modes) allow this, but others (like PostgreSQL, SQL Server) will throw an error. Always use an aggregate function to specify which value you want from each group.

---

