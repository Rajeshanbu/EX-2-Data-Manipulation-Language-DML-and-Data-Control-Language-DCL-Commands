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
```
update manager set salary=salary+(salary*10/100);
```
### OUTPUT:
![1](https://github.com/dineshgl/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118924713/32cd1b1b-633f-4079-b767-d686628cce24)

### Q2) Delete the records from manager table where the salary less than 2750.


### QUERY:
```
delete from manager where salary <2750;
```
### OUTPUT:
![2](https://github.com/dineshgl/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118924713/d57d320f-5d42-4607-ad73-1278570ccb47)


### Q3) Display each name of the employee as “Name” and annual salary as “Annual Salary” (Note: Salary in emp table is the monthly salary)


### QUERY:
```
select ename as "NAME" ,salary*12 as"ANNUAL SALARY" from manager;
```
### OUTPUT:
![3](https://github.com/dineshgl/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118924713/74ac52fd-9077-422b-a783-2db5a19ff31a)


### Q5)	List the names of Clerks from emp table.


### QUERY:
```
select ename from manager where designation='clerk';
```
### OUTPUT:

![4](https://github.com/dineshgl/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118924713/f0cd6a8f-4cc1-4b44-8ec2-ac5668143e9e)

### Q6)	List the names of employee who are not Managers.


### QUERY:
```
select ename from manager where designation !='manager';
```
### OUTPUT:
![5](https://github.com/dineshgl/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118924713/9e6bfae4-b27e-491e-8145-7e9ac1923f67)



### Q7)	List the names of employees not eligible for commission.


### QUERY:
```
select ename from manager where commission =0;
```
### OUTPUT:
![6](https://github.com/dineshgl/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118924713/7c45ca40-1a84-4df6-9ebe-9d55b58fa992)


### Q8)	List employees whose name either start or end with ‘s’.


### QUERY:
```
select ename from manager where ename like 's%' or ename like '%s';
```
### OUTPUT:
![7](https://github.com/dineshgl/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118924713/9c02f6b6-5373-4535-941c-2772bd0a8074)


### Q9) Sort emp table in ascending order by hire-date and list ename, job, deptno and hire-date.


### QUERY:
```
select ename,designation,deptno,hiredate from manager order by hiredate asc;
```
### OUTPUT:

![8](https://github.com/dineshgl/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118924713/72c01700-3e01-4ae7-a46b-df3a377fd04c)

### Q10) List the Details of Employees who have joined before 30 Sept 81.


### QUERY:
```
select * from manager where hiredate < to_date('1981-09-30','yyyy-mm-dd');
````
### OUTPUT:
![9](https://github.com/dineshgl/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118924713/c926abc1-891b-410f-9587-5cb6e2edb764)


### Q11)	List ename, deptno and sal after sorting emp table in ascending order by deptno and then descending order by sal.


### QUERY:
```
select ename,deptno,salary from manager order by deptno asc;
select ename,deptno,salary from manager order by deptno desc;
```
### OUTPUT:

![10](https://github.com/dineshgl/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118924713/510abb78-794a-431c-8edf-2fd8467838ce)

### Q12) List the names of employees not belonging to dept no 30,40 & 10


### QUERY:
```
SELECT ename FROM manager WHERE deptno NOT IN (10,30,40);
```
### OUTPUT:
![11](https://github.com/dineshgl/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118924713/d0567158-6ad6-411e-84aa-376c3e626c92)

### Q13) Find number of rows in the table EMP

### QUERY:
```
select count(*) from manager;
```
### OUTPUT:
![12](https://github.com/dineshgl/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118924713/0caf0d26-5e7d-4d86-aebf-4f38d0859a3d)


### Q14) Find maximum, minimum and average salary in EMP table.

### QUERY:
```
select ename,salary,annualsalary from manager where salary=(select max(salary) from manager);
select ename,salary,annualsalary from manager where salary=(select min(salary) from manager);
select avg(salary) from manager;
```
### OUTPUT:
![13](https://github.com/dineshgl/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118924713/1d27990a-7541-4be6-b0bb-eb898c3bee55)


### Q15) List the jobs and number of employees in each job. The result should be in the descending order of the number of employees.

### QUERY:
```
SELECT designation, count(*) AS "Number of Employees" FROM manager GROUP BY designation ORDER BY count(*) DESC;i
```
### OUTPUT:
![14](https://github.com/dineshgl/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118924713/3362f884-0d7b-4548-aa95-6ddc27732ec0)
