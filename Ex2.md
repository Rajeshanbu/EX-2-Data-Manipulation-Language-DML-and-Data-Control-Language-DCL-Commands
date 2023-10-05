# EX 2 Data Manipulation Language (DML) Commands and built in functions in SQL
## AIM:
To create a manager database and execute DML queries using SQL.


## DML(Data Manipulation Language)
<div align="justify">
The SQL commands that deal with the manipulation of data present in the database belong to DML or Data Manipulation Language and this includes most of the SQL statements. It is the component of the SQL statement that controls access to data and to the database. Basically, DCL statements are grouped with DML statements.
</div>

## List of DML commands: 
<div align="justify">
INSERT: It is used to insert data into a table.<br>
UPDATE: It is used to update existing data within a table.<br>
DELETE: It is used to delete records from a database table.<br>
</div>

## Create the table as given below:
```sql
create table manager(enumber number(6),ename char(15),salary number(5),commission number(4),annualsalary number(7),Hiredate date,designation char(10),deptno number(2),reporting char(10));
```
## insert the following values into the table
```sql
insert into manager values(7369,'Dharsan',2500,500,30000,'30-June-81','clerk',10,'John');
insert into manager values(7839,'Subu',3000,400,36000,'1-Jul-82','manager',null,'James');
insert into manager values(7934,'Aadhi',3500,300,42000,'1-May-82','manager',30,NULL);
insert into manager values(7788,'Vikash',4000,0,48000,'12-Aug-82','clerk',50,'Bond');
```

### Q1) Update all the records of manager table by increasing 10% of their salary as bonus.

### QUERY:
```sql
update manager set salary=salary+(salary*10/100);
```
### OUTPUT:
![1](https://github.com/Rajeshanbu/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118924713/9244d178-2ba3-4f1f-810a-f614aa512e23)

### Q2) Delete the records from manager table where the salary less than 2750.


### QUERY:
```sql
delete from manager where salary <2750;
```
### OUTPUT:
![2](https://github.com/Rajeshanbu/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118924713/b79498c1-4f70-461c-a6f3-8bcc9d5fdf1a)

### Q3) Display each name of the employee as “Name” and annual salary as “Annual Salary” (Note: Salary in emp table is the monthly salary)


### QUERY:
 ```sql
select ename as "NAME" ,salary*12 as"ANNUAL SALARY" from manager;
```
### OUTPUT:
![3](https://github.com/Rajeshanbu/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118924713/6411196d-fa96-466b-a59b-c9de9c8779a4)

### Q5)	List the names of Clerks from emp table.


### QUERY:
```sql
select ename from manager where designation='clerk';
```
### OUTPUT:
![4](https://github.com/Rajeshanbu/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118924713/613c2907-adb6-458d-9abe-e403bf0a289f)


### Q6)	List the names of employee who are not Managers.


### QUERY:
```sql
select ename from manager where designation !='manager';
```
### OUTPUT:
![5](https://github.com/Rajeshanbu/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118924713/20caa3f7-aedf-4210-bb6c-8b58282a7b41)


### Q7)	List the names of employees not eligible for commission.


### QUERY:
```sql
select ename from manager where commission =0;
```
### OUTPUT:
![6](https://github.com/Rajeshanbu/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118924713/77174dc0-2b4c-41f8-a5fc-601f5cb7a992)


### Q8)	List employees whose name either start or end with ‘s’.


### QUERY:
```sql
select ename from manager where ename like 's%' or ename like '%s';
```
### OUTPUT:
![7](https://github.com/Rajeshanbu/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118924713/a297d71a-a14c-4cf6-9153-cc089dc93ff8)


### Q9) Sort emp table in ascending order by hire-date and list ename, job, deptno and hire-date.


### QUERY:
```sql
select ename,designation,deptno,hiredate from manager order by hiredate asc;
```
### OUTPUT:
![8](https://github.com/Rajeshanbu/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118924713/ba24c83e-84cd-41ed-b872-f275daa28326)


### Q10) List the Details of Employees who have joined before 30 Sept 81.


### QUERY:
```sql
select * from manager where hiredate < to_date('1981-09-30','yyyy-mm-dd');
```
### OUTPUT:
![9](https://github.com/Rajeshanbu/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118924713/eb685f90-c89b-4aff-b99d-d5f9827f52b0)


### Q11)	List ename, deptno and sal after sorting emp table in ascending order by deptno and then descending order by sal.


### QUERY:
```sql
select ename,deptno,salary from manager order by deptno asc;
select ename,deptno,salary from manager order by deptno desc;
```
### OUTPUT:
![10](https://github.com/Rajeshanbu/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118924713/94e95613-d79e-4b70-ac5a-376e5abcca47)


### Q12) List the names of employees not belonging to dept no 30,40 & 10


### QUERY:
```sql
SELECT ename FROM manager WHERE deptno NOT IN (10,30,40);
```
### OUTPUT:
![11](https://github.com/Rajeshanbu/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118924713/06ab7499-4b8c-45b8-9723-75aeab901baa)

### Q13) Find number of rows in the table EMP

### QUERY:
```sql
select count(*) from manager;
```
### OUTPUT:
![12](https://github.com/Rajeshanbu/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118924713/6c1bec42-202a-4bbd-be4d-96e1647b9ec0)


### Q14) Find maximum, minimum and average salary in EMP table.

### QUERY:
```sql
select ename,salary,annualsalary from manager where salary=(select max(salary) from manager);
select ename,salary,annualsalary from manager where salary=(select min(salary) from manager);
select avg(salary) from manager;
```
### OUTPUT:
![13](https://github.com/Rajeshanbu/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118924713/96c9af2b-9774-4f5a-8459-e96e39bfa883)


### Q15) List the jobs and number of employees in each job. The result should be in the descending order of the number of employees.

### QUERY:
```sql
SELECT designation, count(*) AS "Number of Employees" FROM manager GROUP BY designation ORDER BY count(*) DESC;
```
### OUTPUT:
![14](https://github.com/Rajeshanbu/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118924713/ff655320-0d8b-4f74-8029-5622ba4a8676)
