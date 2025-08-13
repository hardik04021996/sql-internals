# 13-Important-SQL-Interview-Questions

## Sample Interview Questions
1. What is the difference between SQL and MySQL?
   - SQL is a language for querying and managing databases; MySQL is a popular open-source database management system that uses SQL as its query language.

2. Explain the difference between primary key and unique key.
   - Primary key uniquely identifies each row and cannot be NULL. Unique key also enforces uniqueness but can have one NULL value. Only one primary key per table, but multiple unique keys are allowed.

3. What is a foreign key and why is it used?
   - A foreign key is a column or set of columns in one table that refers to the primary key in another table. It enforces referential integrity, ensuring that relationships between tables remain consistent.

4. What is normalization?
   - Normalization is the process of organizing data in a database to reduce redundancy and improve data integrity. It involves dividing tables into smaller tables and defining relationships between them (1NF, 2NF, 3NF, etc.).

5. What are aggregate functions? Give examples.
   - Aggregate functions perform calculations on multiple rows and return a single value. Examples: COUNT, SUM, AVG, MIN, MAX.

6. Explain different types of joins in SQL.
   - INNER JOIN returns matching rows from both tables. LEFT JOIN returns all rows from the left table and matching rows from the right. RIGHT JOIN returns all rows from the right table and matching rows from the left. FULL JOIN returns all rows when there is a match in either table. CROSS JOIN returns the Cartesian product. SELF JOIN joins a table to itself.

7. What is a subquery?
   - A subquery is a query nested inside another query. It can be used in SELECT, INSERT, UPDATE, or DELETE statements for filtering, calculations, or returning values to the outer query.

8. What is the use of the GROUP BY clause?
   - GROUP BY groups rows that have the same values in specified columns, allowing aggregate functions to be applied to each group.

9. What is a view in SQL?
   - A view is a virtual table based on the result of a SELECT query. It does not store data itself but provides a way to simplify complex queries and enhance security.

10. What is the difference between WHERE and HAVING clause?
    - WHERE filters rows before grouping and aggregation; HAVING filters groups after aggregation. WHERE cannot be used with aggregate functions, but HAVING can.

11. What is a window function?
    - Window functions (e.g., ROW_NUMBER, RANK, DENSE_RANK, SUM OVER) perform calculations across a set of table rows related to the current row, without collapsing rows like GROUP BY.

12. Explain transaction isolation levels.
    - Isolation levels control how/when changes made by one transaction become visible to others. Common levels: Read Uncommitted (least strict), Read Committed, Repeatable Read, Serializable (most strict). Higher isolation reduces concurrency issues but may impact performance.

13. What is the difference between DELETE and TRUNCATE?
    - DELETE removes rows one by one and can be rolled back; TRUNCATE quickly removes all rows and may not be rolled back in some databases. DELETE can have WHERE clause, TRUNCATE cannot.

14. What is indexing and why is it important?
    - Indexes are special data structures that speed up data retrieval operations. They can be single-column, composite, or covering indexes. Indexes improve read performance but can slow down writes and take up extra space.

---

