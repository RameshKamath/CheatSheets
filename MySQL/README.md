# **MySQL Cheat Sheet File**

**MySQL** is *Relational Database* that uses SQL query language and follows strict Relational schema. 

> **Note:** the variables with `<objectName>` should be replaced by appropriately named object.

# Terminologies:
* `database` - this is a collection of `tables` that can hold data.

* `tables` -  these have `columns` and `rows`.
    > tables hold the data in column and row as 2D grid space.

* `columns` - a place to store meta data of the data, The `columns` also tell what type of data it can store.

* `rows` - These are Data fields, the `columns` data of same `rows` can be related.

## Entity Relationship 
```
`database`
 |
 |   # tables in database
 |-`<table>` 
 |     |
 |     | #  table with columns and rows
 |     |-`<column>`, `<column>`, ...
 |          | `<row>`    | `<row>`
 |          | `<row>`    | `<row>`
 |          |    .       |    .
 |  
 |-`<table>` 
 |     |-`<column>`, `<column>`,...`<foreign key column>`
```
# Starting MySQL
## Shell
```sql
mysql
```
### Login
```sql
mysql -u root -p
```
### Login with *user name* = `<UserName>`
```sql
mysql -u <userName> -p
```
> `<userName>` is for user name of connection.


# Database Operations

* `SHOW DATABASES;` - Shows All available Databases in MySQL.

* `USE <databaseName>;` - Selects `<databaseName>` as current database.
    > when working with current database there is no need to mention the database name in operations

*   `SHOW SCHEMAS;` - Same as `SHOW DATABASES;`.

*   `SHOW DATABASES LIKE <pattern>;` - shows database that match `<pattern>`.

   > Example: `SHOW DATABASES LIKE '%schema';`

*   `DROP DATABASE <databaseName>;` - drops a database with name `<databaseName>`.

---

# CRUD Operations

## Create/Insert
Inserts `<values>` into `<fields>` in `<tableName>`.
```sql
INSERT INTO <tableName> ( <field1>, <field2>,...<fieldN> )
VALUES ( <value1>, <value2>,...<valueN> );  
```

## Read/Select
For getting `rows` of data on the  `<columnNames>` from `<tableName>` in `<databaseName>`
```sql
SELECT <columnNames>
FROM <databaseName>.<tableName>;
```

or when working with current database.

```sql
SELECT <columnNames>
FROM <tableName>;
```

### Complete SELECT query
```sql
SELECT DISTINCT <columnNames>, AGG_FUNC(<columnOrExpression>), …
FROM <tableName>
JOIN <anotherTable>
  ON <tableName>.<columnNames> = <anotherTable>.<columnNames>  -- join on row value in both column
WHERE <constraint_expression>
GROUP BY <columnNames>
HAVING <constraint_expression>
ORDER BY <columnNames> ASC || DESC
LIMIT <numLimit> OFFSET <numOffset>;
```

#### order of execution
> A table is built by the engine based on the following order of execution

1. `FROM` and `JOIN ON` - gets the tables for query
2. `WHERE` - uses condition to filter the rows
3. `GROUP BY` - groups by the column
4. `HAVING` - again filters on grouped table
5. `SELECT` - select only required columns and discards others
6. `DISTINCT` - keeps only unique rows for the selected columns
7. `ORDER BY` - orders the column in Ascending or Descending
8. `LIMIT / OFFSET` - allows only limited amount in table with offset from first row

    > To learn more about order of execution [click here](https://sqlbolt.com/lesson/select_queries_order_of_execution)



## Update

Updates the `<values>` in `<table>` for `<fields>` based on `<constrain>` in `WHERE` Clauses
```sql
UPDATE <tableName>
SET <field1>=<newValue1>, <field2>=<newValue2>, ...
WHERE <constraint_expression>;
```
> if WHERE clause is not used to filter for specific this will update entire table.

## Delete
Is used to delete data from the MySQL table within the database.
```sql
DELETE FROM <tableName>   
WHERE <constraint_expression>;
```  
deletes the data in table.
> WHERE clause is used to target data if not used all data in table will be deleted.

---

To know more about MySQL commands [go here](https://www.javatpoint.com/mysql-tutorial) or [here](https://sqlbolt.com/) for sql