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
### see the table using database query

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
## All employees who have joined in a particular data range from the payroll service database

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
### To find count using db query

```
mysql> SELECT gender, COUNT(name) FROM employee_payroll GROUP BY gender;
```

## UC8 - Add  Employee phoneNumber,address and Department to the table

### To add Employee PhoneNumber using database query

```
alter table employee_payroll add phoneNumber varchar(250) after name;

```

### To add Employee address using database query

```
alter table employee_payroll add address varchar(300) after phoneNumber;
```

### To add Employee department using database query

```
alter table employee_payroll add department varchar(250) NOT NULL after address;
```

## UC9 - Add  Employee Basic Pay, Deductions , Taxable Pay ,Income Tax ,Net Pay to the table

### To add Employee Employee Basic Pay using database query

```
alter table employee_payroll add basic_Pay double NOT NULL after gender;
```
### To add Employee Employee Deductions using database query

```
alter table employee_payroll add deductions double NOT NULL after basic_Pay;
```
### To add Employee Employee Taxable Pay using database query

```
alter table employee_payroll add taxable_pay double NOT NULL after deductions;
```
### To add Employee Employee Income Tax using database query

```
alter table employee_payroll add tax double NOT NULL after taxable_pay;
```

### To add Employee Employee Net Pay using database query

```
alter table employee_payroll add net_pay double NOT NULL after tax;
```
## UC-10.1 To make Terisa as part of Sales and Marketing Department

### To insert Terisa into sales department using database query

```
INSERT INTO employee_payroll(name ,phoneNumber,address,department,gender,basic_Pay,deductions,taxable_pay,tax,net_pay,start) VALUES
    -> ('Terisa','7894561230','Hyd','Sales','F',300000.0,0,300000,100000,200000,'2019-11-13');
```

### To insert Terisa into Marketing department using database query

```
INSERT INTO employee_payroll(name ,phoneNumber,address,department,gender,basic_Pay,deductions,taxable_pay,tax,net_pay,start) VALUES
    -> ('Terisa','7894561230','Hyd','Marketing','F',200000.0,0,200000,0,200000,'2019-11-13');
```

### To show table having name as terisa

```
select * from employee_payroll where name='Terisa';
```

## UC-11 create table Employee_department having Employee_Id and DEpartment_Id 

### To create employee table using db query

```
CREATE TABLE employee
-> (
-> id   INT unsigned NOT NULL AUTO_INCREMENT PRIMARY KEY,
-> name            varchar(150) NOT NULL,
-> phoneNumber    varchar(300),
-> address         varchar(250),
-> gender          char(1),
-> start         date NOT NULL,
-> company_id     INT ,
-> FOREIGN KEY (company_id) REFERENCES company (company_id)
```
### To create payroll table using db query

```
CREATE TABLE payroll
-> (
-> id   INT unsigned NOT NULL AUTO_INCREMENT PRIMARY KEY,
-> basic_pay    DOUBLE NOT NULL,
-> deductions   DOUBLE NOT NULL,
-> taxable_pay  DOUBLE NOT NULL,
-> tax          DOUBLE NOT NULL,
-> net_pay      DOUBLE NOT NULL,
-> FOREIGN KEY (id) REFERENCES employee (id),
-> )
```
### To create department table using db query

```
CREATE TABLE department(
-> Dept_ int NOT NULL PRIMARY KEY,
-> Dept_Name varchar(150) NOT NULL
-> )
```
### To create employee_department table using db query

```
create table employee_department(
-> id  INT unsigned NOT NULL AUTO_INCREMENT,
-> Dept_id int NOT NULL,
-> FOREIGN KEY (id) REFERENCES employee (id),
-> FOREIGN KEY (Dept_id) REFERENCES department (Dept_id)
-> )
```

