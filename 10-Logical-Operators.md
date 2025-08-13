# 10-Logical-Operators

## Logical Operators in SQL
| Operator | Description                  |
|----------|------------------------------|
| AND      | True if both conditions true |
| OR       | True if either condition true|
| NOT      | Reverses the condition       |

## Example
```sql
SELECT * FROM employee WHERE age > 25 AND location = 'Bangalore';
SELECT * FROM employee WHERE age < 30 OR salary > 20000;
SELECT * FROM employee WHERE NOT location = 'Delhi';
```

## Q&A
**Q: Can logical operators be combined?**
A: Yes, you can use parentheses to group conditions.

---

