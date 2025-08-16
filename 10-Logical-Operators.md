# 10-Logical-Operators

## Logical Operators in SQL
| Operator | Description                  |
|----------|------------------------------|
| AND      | True if both conditions true |
| OR       | True if either condition true|
| NOT      | Reverses the condition       |
| BETWEEN  | True if value is within a range |
| IN       | True if value matches any value in a list |

## Example
```sql
SELECT * FROM employee WHERE age > 25 AND location = 'Bangalore';
SELECT * FROM employee WHERE age < 30 OR salary > 20000;
SELECT * FROM employee WHERE NOT location = 'Delhi';
SELECT * FROM employee WHERE age BETWEEN 20 AND 30;
SELECT * FROM employee WHERE location IN ('Bangalore', 'Delhi');
```

## Q&A
**Q: Can logical operators be combined?**

A: Yes, you can use parentheses to group conditions.

**Example:**

```sql
SELECT * FROM employee WHERE (age > 25 AND location = 'Bangalore') OR salary > 20000;
```
This query selects employees who are older than 25 and located in Bangalore, or whose salary is greater than 20,000. Parentheses ensure the AND condition is evaluated before the OR.

**Q: What is the precedence of logical operators in SQL?**

A: The order is: NOT > AND > OR. Use parentheses to control evaluation order in complex conditions.

**Q: What does BETWEEN do?**

A: Checks if a value is within a specified range (inclusive).

**Q: What does IN do?**

A: Checks if a value matches any value in a list.

---

