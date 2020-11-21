## Basic DB Operations
1. Change Database `USE <Databasename>;`
2. Get all tablenames `SHOW TABLES;`
3. Get columns of table `SHOW columns FROM <table-name>;` or `desc <table-name>;` or `DESCRIBE <table-name>`. This command also provides datatypes, null type, default type, if any of the columns are key (`PRI` -> PRIMARY, `UNI` -> unique, `MUL`). The `<table-name> ` is case-sensitive.
4. Query Data
    `SELECT <col-name> FROM <table-name> ORDER BY <col-name>`
   1. The `<col-name>` are case insensitive in mysql.
   2. `ORDER BY <col-name> [ASC|DESC]` can be either ascending(`ASC`) or descending (`DESC`). Default is ascending.
   3. If an unknown column name is provided, it throws `ERROR 1054 (42S22): Unknown column '<col-name>' in 'field list'`
   4. Limit the number of records by using `LIMIT <n>`
   5. Use `DISTINCT` to get only unique records
   6. `SELECT DISTINCT(<col-name>) AS <col-alias> FROM <table>` gets the unique values of a column.
   7. To sort by a column with catergorical values (numeric or string) use `FIELD(unqval1, unqval2, . unqvaln)` which returns index of these categorical values        
      1. \# Question: How to sort by a column with categorical value without explicit enumeration.
   8. `SELECT COUNT(<colname>) FROM <table>` will only give the counts and not the actual records.
   9. `LIKE` can go along with what types of wildcards and regex
      1.  `WHERE firstName LIKE 'a%' ` gives you names like Anthony, Andy (Case insensitive)
      2.  `WHERE lastName LIKE '%on'`  gives: Patterson, Thompson
      3.  `WHERE lastName LIKE '%on%'` gives: Jones, Bondur, Patterson, Thomposon
      4.  `WHERE firstname LIKE 'T_m'` gives: Tim, Tom (only one missing character)
      5.  `NOT LIKE` to select without the pattern. Use escape to search for wildcard type productCode `WHERE LIKE '%\_20%'` or `WHERE productCode LIKE '%$_20%' ESCAPE '$'`
   10. `LIMIT [offset], rowcount`
   11. Operator Precedence: 
       1.  Without explicit precedebce (through brackets), MySQL evaluates the OR operators after the AND operators
   12. Comparison operators (`IS NULL, <, >, BETWEEN` can be used in `FROM` clause and `WHERE` clause).
       1. If a `DATE` or `DATETIME` column has a `NOT NULL` constraint and contains a special date `0000-00-00`, you can use the `IS NULL` operator to find such rows.
       2. If the variable @@sql_auto_is_null is set to 1, you can get the value of an auto_increment column after executing an INSERT statement by using the IS NULL operator. More details [here](https://www.mysqltutorial.org/mysql-is-null/)
   13. Type Casting:
       1.  `CAST(expression as TYPE)`. The CAST() function converts a value of any type into a value that has a specified type. The target type can be any one of the following types: BINARY, CHAR, DATE, DATETIME, TIME,DECIMAL, SIGNED, UNSIGNED. More Info [here](https://www.mysqltutorial.org/mysql-cast/).
   14. `` SELECT  CONCAT_WS(', ', lastName, firstname) AS `Full name` FROM employees ORDER BY `Full name`; `` create a new full name column and sort by that column
   15. returns a concatenated column of lastname and firstname separated by comma
   16. Operational Sequence:
       1.  `FROM -> WHERE -> SELECT -> ORDER BY -> LIMIT`
   17. 
   18. 
   19. Questions
       1.  Select only columns that allow Null from Table. More info [SO-Link](https://dba.stackexchange.com/a/19113/209913)
            ```sql
            SELECT COLUMN_NAME 
            FROM information_schema.COLUMNS 
            WHERE TABLE_SCHEMA='db name' 
            AND TABLE_NAME='table Name' 
            AND IS_NULLABLE='YES';
            ```

