# 12-Joins

## What are Joins?
Joins are used to combine rows from two or more tables based on a related column between them.

### Types of Joins
| Join Type   | Description                                      |
|-------------|--------------------------------------------------|
| INNER JOIN  | Returns records with matching values in both tables |
| LEFT JOIN   | Returns all records from the left table, and matched records from the right table |
| RIGHT JOIN  | Returns all records from the right table, and matched records from the left table |
| FULL JOIN   | Returns all records when there is a match in either table |

### Example
```sql
SELECT e.name, d.dept_name
FROM employee e
INNER JOIN department d ON e.dept_id = d.dept_id;
```

## Q&A
**Q: What is the difference between INNER JOIN and LEFT JOIN?**
A: INNER JOIN returns only matching records; LEFT JOIN returns all records from the left table and matching records from the right.

**Q: What is a CROSS JOIN?**
A: Returns the Cartesian product of two tables.

**Q: What is a SELF JOIN?**
A: A table joined with itself.

**Q: Can you join more than two tables?**
A: Yes, you can join multiple tables in a single query.

**Q: What is an equi join?**
A: A join using equality comparison in the ON clause.

---

