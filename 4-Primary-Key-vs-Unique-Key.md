# 4-Primary-Key-vs-Unique-Key


## Primary Key
- Uniquely identifies each record in a table.
- Cannot have NULL values.
- Only one primary key per table (can be composite, i.e., multiple columns).
- Automatically creates a unique index for fast lookups.
- Used for establishing relationships (foreign keys) with other tables.


## Unique Key
- Ensures all values in a column (or set of columns) are unique.
- Can have NULL values (except in some databases).
- Multiple unique keys allowed per table.
- Does not automatically create a clustered index (depends on DBMS).

## Comparison Table
| Feature         | Primary Key         | Unique Key           |
|-----------------|--------------------|----------------------|
| Uniqueness      | Yes                | Yes                  |
| NULL Allowed    | No                 | Yes (usually)        |
| Count per Table | One (can be multi) | Multiple             |
| Purpose         | Row identification | Enforce uniqueness   |

## Example
```sql
CREATE TABLE employee (
  id INT PRIMARY KEY,
  email VARCHAR(100) UNIQUE
);
```


## Q&A
**Q: Can a table have more than one primary key?**
A: No, but it can have a composite primary key (multiple columns together as the unique identifier).

**Q: Can a table have more than one unique key?**
A: Yes, multiple unique keys are allowed.

**Q: Can a primary key be NULL?**
A: No, primary key columns must always have a value.

**Q: Can a unique key be NULL?**
A: Yes, unique key columns can be NULL (except in some databases), but each NULL is treated as a unique value.

**Q: What happens if you try to insert a duplicate value in a primary or unique key column?**
A: The database will throw an error and prevent the insert or update.

---
*Extracted from transcript session 3.*
