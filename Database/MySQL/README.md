# MySQL

## Scenario 1: Invalid default value for '...'

1. Check the current sql_modes by command:
```mysql
show variables like 'sql_mode'; 
```
2. Modify `sql_mode`:
```mysql
SET sql_mode = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION';
```

## Scenario 2: Disable autocommit

1. Check the status of `autocommit`:
```mysql
show variables like 'autocommit';
```
2. Disable `autocommit`:
```mysql
SET AUTOCOMMIT = 0;
```