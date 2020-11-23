# PostgreSQL
## Learning Notes
1. Get column names of tables
```sql
select column_name, data_type 
from information_schema.columns
where table_name = '<table-name';
```
2. You use `--` to start a comment in SQL. It can be in the beginning of the line or from between.
3. COUNT
    1. `COUNT` is a function which needs braces as it acts on other values
    2. `COUNT(column1)` will ignore null values in column1. It will only consider not null values in that column.
    3. Get null and not null values of column `a` from table `us`.
        ```sql
        -- Approach 1
        select sum(case when a is null then 1 else 0 end) count_nulls
        , count(a) count_not_nulls 
        from us;
        -- Approach 2
        select count(*) - count(a), count(a) from us;
        ```
5. WHERE
   1. PosgreSQL comparison is case sensitive. For example a name comparison must have same case.
   ```sql
   -- For a name Nancy Thomas
   -- This will Pass
    SELECT email FROM customer
    WHERE last_name='Thomas' AND
    first_name='Nancy';
    -- This will Fail
    SELECT email FROM customer
    WHERE last_name='THOMAS' AND
    first_name='Nancy';
    ```
    Use `ILIKE` to case insensitive comparison. More Details [SO-Link](https://stackoverflow.com/a/4482340/1652217)
    ```sql
    SELECT email FROM customer
    WHERE last_name ILIKE 'THOMAS' AND
    first_name ILIKE 'NaNCy';
    ```
6. How to get primary key(s) of a table. More Details here [SO-LINK](https://stackoverflow.com/a/20537829/1652217)
    ```sql
    SELECT               
    pg_attribute.attname, 
    format_type(pg_attribute.atttypid, pg_attribute.atttypmod) 
    FROM pg_index, pg_class, pg_attribute, pg_namespace 
    WHERE 
    pg_class.oid = 'foo'::regclass AND 
    indrelid = pg_class.oid AND 
    nspname = 'public' AND 
    pg_class.relnamespace = pg_namespace.oid AND 
    pg_attribute.attrelid = pg_class.oid AND 
    pg_attribute.attnum = any(pg_index.indkey)
    AND indisprimary
    ```
7. 

## Questions & Issues
1. How to export SQL query output to CSV (from PGADMIN4)
2. How to select n1 to n2 records (say record number 100 to 200)
3. How to use `ILIKE` in a string with spaces and special characters (since LIKE doesnt seem to work with spaces)
4. Compare strings using `LIKE` (or anything else) by removing leading and trailing spaces.
5. Find Duplicate Records in PostgreSQL. More info [SO-Link](https://stackoverflow.com/q/28156795/1652217)
6. How to create a copy of a table with another name.