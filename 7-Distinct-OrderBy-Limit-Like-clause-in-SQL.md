# 7-Distinct-OrderBy-Limit-Like-clause-in-SQL

## DISTINCT
Removes duplicate records from the result set.
```sql
SELECT DISTINCT column_name FROM table_name;
```

## ORDER BY
Sorts the result set by one or more columns.
```sql
SELECT * FROM table_name ORDER BY column_name ASC|DESC;
```

## LIMIT
Restricts the number of records returned.
```sql
SELECT * FROM table_name LIMIT 10;
```

## LIKE
Used for pattern matching in WHERE clause.
```sql
SELECT * FROM table_name WHERE column_name LIKE 'A%';
```

## Q&A
**Q: What does DISTINCT do?**
A: Removes duplicate values from the result set.

**Q: How do you sort results?**
A: Use ORDER BY with ASC (ascending) or DESC (descending).

**Q: How to limit results?**
A: Use LIMIT with the desired number.

**Q: How to search for patterns?**
A: Use LIKE with wildcards (% or _).

---

