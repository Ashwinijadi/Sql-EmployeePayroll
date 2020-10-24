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

## UC3-Create Employee Payroll data in the Payroll Service database

```
INSERT INTO employee_payroll(name , salary , start) VALUES
    -> ('Bill' , 100000.00 , '2018-01-03' ),
    -> ('Mark' , 200000.00 , '2019-11-13' ),
    -> ('Charlie',300000.00, '2020-05-21' );
```
### see the data using database query

```
SELECT * FROM employee_payroll;
```

## UC4-To retrieve all EmployeePayroll data added to Payroll Service

```
SELECT * FROM employee_payroll;
```

