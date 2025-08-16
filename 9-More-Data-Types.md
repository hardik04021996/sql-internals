# 9-More-Data-Types


## Common SQL Data Types
| Data Type | Description                        | Example Usage                |
|-----------|------------------------------------|------------------------------|
| INT       | Integer numbers                    | age INT                      |
| VARCHAR   | Variable-length string (up to 255) | name VARCHAR(50)             |
| CHAR      | Fixed-length string                | code CHAR(3)                 |
| DATE      | Date values                        | birthdate DATE               |
| FLOAT     | Floating point numbers             | price FLOAT                  |
| BOOLEAN   | True/False values                  | is_active BOOLEAN            |
| TEXT      | Large variable-length string       | description TEXT             |
| TIMESTAMP | Date and time                      | created_at TIMESTAMP         |


## Q&A
**Q: What is the difference between VARCHAR and CHAR?**

A: VARCHAR is variable-length (saves space for short values), CHAR is fixed-length (always uses the defined size).

**Q: What happens if you exceed the defined length?**

A: The database will throw an error (e.g., 'data too long for column').

**Q: What is the default length for VARCHAR if not specified?**

A: Most databases require you to specify a length; otherwise, a default may be used (e.g., 255).

**Q: When should you use TEXT instead of VARCHAR?**

A: Use TEXT for very large strings (e.g., descriptions, comments) that may exceed VARCHAR limits.

**Q: What is NOT NULL constraint?**

A: NOT NULL ensures that a column cannot have NULL values. It is used to enforce mandatory fields in a table.

**Q: What is DEFAULT value in SQL?**

A: DEFAULT sets a value to be used when no explicit value is provided during insert. Useful for common values like location or status.

**Q: What happens if you insert a value with a data type mismatch?**

A: SQL will throw an error and prevent the insert, ensuring data integrity.

---

