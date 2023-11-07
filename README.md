# EX 3 SubQueries, Views and Joins 

## Create employee Table
```sql
CREATE TABLE EMP (EMPNO NUMBER(4) PRIMARY KEY,ENAME VARCHAR2(10),JOB VARCHAR2(9),MGR NUMBER(4),HIREDATE DATE,SAL NUMBER(7,2),COMM NUMBER(7,2),DEPTNO NUMBER(2));
```
![1](https://github.com/ASHWINKUMAR2903/EX-3-SubQueries-Views-and-Joins/assets/119407186/29d67132-91b5-4bbb-a8bc-628120a37d12)


## Insert the values
```sql
INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7369, 'SMITH', 'CLERK', 7902, '17-DEC-80', 800, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7499, 'ALLEN', 'SALESMAN', 7698, '20-FEB-81', 1600, 300, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7521, 'WARD', 'SALESMAN', 7698, '22-FEB-81', 1250, 500, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7566, 'JONES', 'MANAGER', 7839, '02-APR-81', 2975, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7654, 'MARTIN', 'SALESMAN', 7698, '28-SEP-81', 1250, 1400, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7698, 'BLAKE', 'MANAGER', 7839, '01-MAY-81', 2850, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7782, 'CLARK', 'MANAGER', 7839, '09-JUN-81', 2450, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7788, 'SCOTT', 'ANALYST', 7566, '19-APR-87', 3000, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7839, 'KING', 'PRESIDENT', NULL, '17-NOV-81', 5000, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7844, 'TURNER', 'SALESMAN', 7698, '08-SEP-81', 1500, 0, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7876, 'ADAMS', 'CLERK', 7788, '23-MAY-87', 1100, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7900, 'JAMES', 'CLERK', 7698, '03-DEC-81', 950, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7902, 'FORD', 'ANALYST', 7566, TO_DATE('03-DEC-81', 'DD-MON-RR'), 3000, 20, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7934, 'MILLER', 'CLERK', 7782, TO_DATE('23-JAN-82', 'DD-MON-RR'), 1300, 10, 10);
```
![2](https://github.com/ASHWINKUMAR2903/EX-3-SubQueries-Views-and-Joins/assets/119407186/75e44b7b-ddae-4d2e-ae0c-2bd1bc435bc6)

## Create department table
```sql
CREATE TABLE DEPT (DEPTNO NUMBER(2) PRIMARY KEY,DNAME VARCHAR2(14),LOC VARCHAR2(13));
```
![3](https://github.com/ASHWINKUMAR2903/EX-3-SubQueries-Views-and-Joins/assets/119407186/2800aa92-1abb-4daf-8698-42eed376cccf)

## Insert the values in the department table
```sql
INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (10, 'ACCOUNTING', 'NEW YORK');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (20, 'RESEARCH', 'DALLAS');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (30, 'SALES', 'CHICAGO');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (40, 'OPERATIONS', 'BOSTON');
```

### Q1) List the name of the employees whose salary is greater than that of employee with empno 7566.


### QUERY:
``` select ename from emp where sal > (select sal from emp where empno = 7566);```

### OUTPUT:
![4](https://github.com/ASHWINKUMAR2903/EX-3-SubQueries-Views-and-Joins/assets/119407186/90c03b62-a547-40f1-95ed-70a84fe7b9a8)

### Q2) List the ename,job,sal of the employee who get minimum salary in the company.

### QUERY:
```select ename,job,sal from emp where sal = (select min(sal) from emp);```

### OUTPUT:
![5](https://github.com/ASHWINKUMAR2903/EX-3-SubQueries-Views-and-Joins/assets/119407186/6d777c14-cc81-4900-a2ff-d296376956b2)

### Q3) List ename, job of the employees who work in deptno 10 and his/her job is any one of the job in the department ‘SALES’.

### QUERY:
```select ename, job from emp where deptno =10 and job in(select job from emp where job = 'SALES');```

### OUTPUT:
![6](https://github.com/ASHWINKUMAR2903/EX-3-SubQueries-Views-and-Joins/assets/119407186/6e9c539c-262f-4e0f-bbe8-894d5ec12311)


### Q4) Create a view empv5 (for the table emp) that contains empno, ename, job of the employees who work in dept 10.

### QUERY:
```create view emp_V5_ as select empno , ename, job from emp where deptno = 10;```

### OUTPUT:
![7](https://github.com/ASHWINKUMAR2903/EX-3-SubQueries-Views-and-Joins/assets/119407186/ce251119-3378-41a1-a187-ebec0b174170)

### Q5) Create a view with column aliases empv30 that contains empno, ename, sal of the employees who work in dept 30. Also display the contents of the view.

### QUERY:
```
create or replace view empv30 as select empno as "EMployee Number", ename as "Employee Name", sal as "Salary" from
emp where deptno = 30;

select * from empv30;
```
### OUTPUT:
![8](https://github.com/ASHWINKUMAR2903/EX-3-SubQueries-Views-and-Joins/assets/119407186/5809161f-f1c0-43bf-b5fc-6d99511e1119)

### Q6) Update the view empv5 by increasing 10% salary of the employees who work as ‘CLERK’. Also confirm the modifications in emp table

### QUERY:
```
update emp set sal = sal*1.1 where job='CLERK';
create view empV5_ as select empno,ename,sal,job from emp;
select * from empV5_;
```

### OUTPUT:
![9](https://github.com/ASHWINKUMAR2903/EX-3-SubQueries-Views-and-Joins/assets/119407186/be319db2-7966-4651-be38-5332db325025)
![10](https://github.com/ASHWINKUMAR2903/EX-3-SubQueries-Views-and-Joins/assets/119407186/e71bda45-12c4-473b-a5b3-978485379ab4)

## Create a Customer1 Table
```sql
CREATE TABLE Customer1 (customer_id INT,cust_name VARCHAR(20),city VARCHAR(20),grade INT,salesman_id INT);
```
## Inserting Values to the Table
```sql
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3002, 'Nick Rimando', 'New York', 100, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3007, 'Brad Davis', 'New York', 200, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3005, 'Graham Zusi', 'California', 200, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3008, 'Julian Green', 'London', 300, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3004, 'Fabian Johnson', 'Paris', 300, 5006);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3009, 'Geoff Cameron', 'Berlin', 100, 5003);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3003, 'Jozy Altidor', 'Moscow', 200, 5007);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3001, 'Brad Guzan', 'London', NULL, 5005);
```
## Create a Salesperson1 table
```sql
CREATE TABLE Salesman1 (salesman_id INT,name VARCHAR(20),city VARCHAR(20),commission DECIMAL(4,2));
```
## Inserting Values to the Table
```sql
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5001, 'James Hoog', 'New York', 0.15);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5002, 'Nail Knite', 'Paris', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5005, 'Pit Alex', 'London', 0.11);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5006, 'Mc Lyon', 'Paris', 0.14);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5007, 'Paul Adam', 'Rome', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5003, 'Lauson Hen', 'San Jose', 0.12);
```
![1](https://github.com/ASHWINKUMAR2903/EX-3-SubQueries-Views-and-Joins/assets/119407186/793a0e05-8af7-4f8d-ad7f-dd5d476a9e55)
![2](https://github.com/ASHWINKUMAR2903/EX-3-SubQueries-Views-and-Joins/assets/119407186/bddd7e5f-f3a9-441d-a1b3-f8fab0b1a9c3)

### Q7) Write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.

### QUERY:
``` select s.name as Salesman, c.cust_name, s.city from Salesman1 s  join customer1 c on s.city = c.city;```

### OUTPUT:
![3](https://github.com/ASHWINKUMAR2903/EX-3-SubQueries-Views-and-Joins/assets/119407186/0d8849ae-d11e-41e0-b06d-88639d634497)

### Q8) Write a SQL query to find salespeople who received commissions of more than 13 percent from the company. Return Customer Name, customer city, Salesman, commission.


### QUERY:
```select c.cust_name as "Customer Name", c.city as "Customer City", s.name as "Salesman", S.commission AS "Commission"FROM Customer1 C JOIN Salesman1 S ON C.salesman_id = S.salesman_id WHERE S.commission > 0.13;```

### OUTPUT:
![4](https://github.com/ASHWINKUMAR2903/EX-3-SubQueries-Views-and-Joins/assets/119407186/84b797c4-5a1b-4f95-b0c5-b4fc0b7e6b10)

### Q9) Perform Natural join on both tables

### QUERY:
```select * from customer1 natural join salesman1 s;```

### OUTPUT:
![5](https://github.com/ASHWINKUMAR2903/EX-3-SubQueries-Views-and-Joins/assets/119407186/30e498d3-a14a-45c6-9e35-fca2173751a8)

### Q10) Perform Left and right join on both tables

### QUERY:
```select * from customer1 left join salesman1 on customer1.city=salesman1.city;```
```select * from customer1 right join salesman1 on customer1.city=salesman1.city;```

### OUTPUT:
![6](https://github.com/ASHWINKUMAR2903/EX-3-SubQueries-Views-and-Joins/assets/119407186/3edcf297-904f-43e7-a32f-27cbc136465f)

## RESULT :
the SubQueries, Views and Joins commands have been executed successfully.
