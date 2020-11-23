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
Issues
1. How to export SQL query output to CSV (from PGADMIN4)