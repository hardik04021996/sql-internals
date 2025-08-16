# 4-Primary-Key-vs-Unique-Key


## Primary Key
- Uniquely identifies each record in a table.
- Cannot have NULL values.
- Only one primary key per table (can be composite, i.e., multiple columns).
- When you define a primary key on a table, the database automatically creates a unique index on that column (or columns). This index ensures that all values in the primary key are unique and allows the database to quickly search, retrieve, or join records based on the primary key.

### How Indexing Helps in Retrieving Data

Indexes are special data structures (often B-trees [Balanced Trees] or hash tables) that store references to the actual rows in a table, organized by the indexed column values.

When you run a query that searches for a specific value in an indexed column (like a primary key), the database:
1. Looks up the value in the index structure (e.g., traverses a B-tree), which is much faster than scanning every row.
2. Finds the reference (pointer) to the actual row(s) in the table.
3. Retrieves only the relevant row(s) directly, skipping all others.


#### What Happens Internally
- Without an index: The database performs a full table scan, checking every row to find matches. This is slow for large tables.
- With an index: The database uses the index to quickly locate the position of the desired row(s), often in logarithmic time (O(log n)), rather than linear time (O(n)).
- For example, in a B-tree index, the database starts at the root, follows branches based on the search value, and quickly narrows down to the leaf node containing the reference to the row.

---
#### B-tree Example and Diagram

Suppose you have a table with a primary key column containing values: 10, 20, 30, 40, 50, 60, 70, 80, 90.

The B-tree index might look like this:

```text
        [30 | 60]
       /    |    \
 [10,20] [40,50] [70,80,90]
```

- The root node contains keys 30 and 60.
- To search for 50:
  - Start at root: 50 > 30 but < 60, so go to the middle child.
  - In [40,50], find 50 and get the pointer to the actual row.

**Why is this fast?**
- Each step eliminates large portions of the data, so only a few comparisons are needed.
- For large tables, this means finding a value in milliseconds instead of seconds.

**SQL Example:**
```sql
SELECT * FROM employee WHERE id = 50;
```
With a B-tree index on `id`, the database quickly finds 50 without scanning all rows.

---
This process makes queries using indexed columns (especially primary keys) extremely fast and efficient, which is critical for large databases and frequent lookups.
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
