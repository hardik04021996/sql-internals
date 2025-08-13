# 7-Distinct-OrderBy-Limit-Like-clause-in-SQL

## DISTINCT
Removes duplicate records from the result set.
```sql
SELECT DISTINCT column_name FROM table_name;
// DISTINCT can be used with multiple columns:
```sql
SELECT DISTINCT column1, column2 FROM table_name;
```
This returns unique combinations of column1 and column2.
```

## ORDER BY
Sorts the result set by one or more columns.
```sql
SELECT * FROM table_name ORDER BY column_name ASC|DESC;
// You can sort by multiple columns:
```sql
SELECT * FROM table_name ORDER BY department ASC, salary DESC;
```
This sorts first by department, then by salary within each department.
```

## LIMIT
Restricts the number of records returned.
```sql
SELECT * FROM table_name LIMIT 10;
// LIMIT with OFFSET for pagination:
```sql
SELECT * FROM table_name LIMIT 10 OFFSET 20;
```
This skips the first 20 records and returns the next 10.
```

## LIKE
Used for pattern matching in WHERE clause.
```sql
SELECT * FROM table_name WHERE column_name LIKE 'A%';
// More LIKE patterns:
```sql
SELECT * FROM table_name WHERE name LIKE '%son'; -- ends with 'son'
SELECT * FROM table_name WHERE name LIKE '_a%'; -- second letter is 'a'
```
```

## Q&A
**Q: What does DISTINCT do?**

**Q: Can DISTINCT be used with multiple columns?**
A: Yes, it returns unique combinations of the selected columns.

A: Removes duplicate values from the result set.


**Q: Can you sort by more than one column?**
A: Yes, separate columns with commas in ORDER BY.

**Q: How do you sort results?**
A: Use ORDER BY with ASC (ascending) or DESC (descending).

**Q: How do you paginate results?**
A: Use LIMIT with OFFSET.


**Q: How to limit results?**

**Q: What do % and _ mean in LIKE?**
A: % matches any sequence of characters; _ matches a single character.
A: Use LIMIT with the desired number.

**Q: How to search for patterns?**
A: Use LIKE with wildcards (% or _).

**Q: What is the order of execution of SQL clauses?**
A: The typical order is: FROM, WHERE, GROUP BY, HAVING, SELECT, ORDER BY, LIMIT. This affects how queries are processed and can impact results.

**Q: Why does SELECT DISTINCT with ORDER BY sometimes fail?**
A: If you use SELECT DISTINCT on one column and ORDER BY another, SQL may throw an error because DISTINCT is applied before ORDER BY, and the ORDER BY column may not be available after projection. This is a common interview question about SQL internals.

---

