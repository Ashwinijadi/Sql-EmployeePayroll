# Sql-EmployeePayroll

## UC1 - create payroll_service database

```
 create database payroll_service;
```

### To see database created 

```
 show databases;
```

### Go to the database created

```
 use payroll_service;
```

## UC2-Create EmployeePayroll_Table

```
 CREATE TABLE employee_payroll
 -> (
    -> id            INT unsigned NOT NULL AUTO_INCREMENT,
    -> name          VARCHAR(150) NOT NULL,
    -> salary        Double NOT NULL,
    -> start         DATE NOT NULL,
    -> PRIMARY KEY   (id)
    -> );
```
###see the table using database query

```
 DESCRIBE employee_payroll;
```

