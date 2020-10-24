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

## UC5-Ability to retrieve salary data for a particular employee 
##All employees who have joined in a particular data range from the payroll service database

```
 SELECT salary FROM employee_payroll WHERE name ='Bill';
```
### show employee payroll Between 2018 to now using db query
```
 SELECT * FROM employee_payroll WHERE start BETWEEN CAST('2018-01-01' AS DATE) AND DATE(NOW());
```

### show employee payroll Between 2019 to now using db query
```
 SELECT * FROM employee_payroll WHERE start BETWEEN CAST('2019-01-01' AS DATE) AND DATE(NOW());
```

## UC6-Ability to add Gender to EmployeePayroll Table and Update the Rows to Employee Gender

```
 ALTER TABLE employee_payroll ADD gender CHAR(1) AFTER name;
```

```
update employee_payroll set gender ='F' where name ='Terisa';
```

```
update employee_payroll set gender ='M' where name ='Bill' or name ='Charlie' or name ='Mark';
```

### see updated gender using db query
```
SELECT * FROM employee_payroll;
```
## UC7-Ability to find sum, average, min, max and number of male and female employees

### To find sum using db query

```
SELECT gender, SUM(salary) FROM employee_payroll GROUP BY gender;
```
### To find average using db query

```
SELECT gender, AVG(salary) FROM employee_payroll GROUP BY gender;
```
### To find minimum using db query

```
SELECT gender, MIN(salary) FROM employee_payroll GROUP BY gender;
```
### To find maximum using db query

```
mysql> SELECT gender, MAX(salary) FROM employee_payroll GROUP BY gender;
```
### To find count using db query

```
mysql> SELECT gender, COUNT(salary) FROM employee_payroll GROUP BY gender;
```
### To find countusing db query

```
mysql> SELECT gender, COUNT(name) FROM employee_payroll GROUP BY gender;
```