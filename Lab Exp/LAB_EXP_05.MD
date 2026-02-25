# DBMS Lab Experiment 05

> **Experiment:** Aggregate and String Functions on `EMPLOYEE` Table

---

## SQL Queries and Results

### 1) Display the total number of employee working in the company.
```sql
SELECT COUNT(*) AS TOTAL_EMPLOYEES
FROM EMPLOYEE;
```
**Output:**
```text
+-----------------+
| TOTAL_EMPLOYEES |
+-----------------+
| 14              |
+-----------------+
1 row in set
```

### 2) Display the total salary being paid to all employees.
```sql
SELECT SUM(SAL) AS TOTAL_SALARY
FROM EMPLOYEE;
```
**Output:**
```text
+--------------+
| TOTAL_SALARY |
+--------------+
| 29025        |
+--------------+
1 row in set
```

### 3) Display the maximum salary from employee table.
```sql
SELECT MAX(SAL) AS MAX_SALARY
FROM EMPLOYEE;
```
**Output:**
```text
+------------+
| MAX_SALARY |
+------------+
| 5000       |
+------------+
1 row in set
```

### 4) Display the minimum salary from employee table.
```sql
SELECT MIN(SAL) AS MIN_SALARY
FROM EMPLOYEE;
```
**Output:**
```text
+------------+
| MIN_SALARY |
+------------+
| 800        |
+------------+
1 row in set
```

### 5) Display the average salary from employee table.
```sql
SELECT AVG(SAL) AS AVG_SALARY
FROM EMPLOYEE;
```
**Output:**
```text
+------------+
| AVG_SALARY |
+------------+
| 2073.2143  |
+------------+
1 row in set
```

### 6) Display the maximum salary being paid to clerk.
```sql
SELECT MAX(SAL) AS MAX_CLERK_SALARY
FROM EMPLOYEE
WHERE JOB = 'CLERK';
```
**Output:**
```text
+------------------+
| MAX_CLERK_SALARY |
+------------------+
| 1300             |
+------------------+
1 row in set
```

### 7) Display the maximum salary being paid in dept no 20.
```sql
SELECT MAX(SAL) AS MAX_SALARY_DEPT20
FROM EMPLOYEE
WHERE DEPTNO = 20;
```
**Output:**
```text
+-------------------+
| MAX_SALARY_DEPT20 |
+-------------------+
| 5000              |
+-------------------+
1 row in set
```

### 8) Display the minimum salary paid to any salesman.
```sql
SELECT MIN(SAL) AS MIN_SALESMAN_SALARY
FROM EMPLOYEE
WHERE JOB = 'SALESMAN';
```
**Output:**
```text
+---------------------+
| MIN_SALESMAN_SALARY |
+---------------------+
| 1250                |
+---------------------+
1 row in set
```

### 9) Display the average salary drawn by managers.
```sql
SELECT AVG(SAL) AS AVG_MANAGER_SALARY
FROM EMPLOYEE
WHERE JOB = 'MANAGER';
```
**Output:**
```text
+--------------------+
| AVG_MANAGER_SALARY |
+--------------------+
| 2758.3333          |
+--------------------+
1 row in set
```

### 10) Display the total salary drawn by analyst working in dept no 40.
```sql
SELECT SUM(SAL) AS TOTAL_ANALYST_SALARY_DEPT40
FROM EMPLOYEE
WHERE JOB = 'ANALYST' AND DEPTNO = 40;
```
**Output:**
```text
+-----------------------------+
| TOTAL_ANALYST_SALARY_DEPT40 |
+-----------------------------+
| 3000                        |
+-----------------------------+
1 row in set
```

### 11) Display the names of the employee in Uppercase.
```sql
SELECT UPPER(ENAME) AS EMP_NAME_UPPER
FROM EMPLOYEE;
```
**Output:**
```text
+----------------+
| EMP_NAME_UPPER |
+----------------+
| SMITH          |
| ALLEN          |
| ...            |
| MILLER         |
+----------------+
14 rows in set
```

### 12) Display the names of the employee in Lowercase.
```sql
SELECT LOWER(ENAME) AS EMP_NAME_LOWER
FROM EMPLOYEE;
```
**Output:**
```text
+----------------+
| EMP_NAME_LOWER |
+----------------+
| smith          |
| allen          |
| ...            |
| miller         |
+----------------+
14 rows in set
```

### 13) Display the names of the employee in Proper case.
```sql
-- MySQL equivalent of INITCAP
SELECT CONCAT(UPPER(LEFT(ENAME, 1)), LOWER(SUBSTRING(ENAME, 2))) AS EMP_NAME_PROPER
FROM EMPLOYEE;
```
**Output:**
```text
+-----------------+
| EMP_NAME_PROPER |
+-----------------+
| Smith           |
| Allen           |
| ...             |
| Miller          |
+-----------------+
14 rows in set
```

### 14) Display the length of your name using appropriate function.
```sql
SELECT LENGTH('PriyanshuYadav') AS NAME_LENGTH;
```
**Output:**
```text
+-------------+
| NAME_LENGTH |
+-------------+
| 14          |
+-------------+
1 row in set
```

### 15) Display the length of all the employee names.
```sql
SELECT ENAME, LENGTH(ENAME) AS NAME_LENGTH
FROM EMPLOYEE;
```
**Output:**
```text
+--------+-------------+
| ENAME  | NAME_LENGTH |
+--------+-------------+
| SMITH  | 5           |
| ALLEN  | 5           |
| ...    | ...         |
| MILLER | 6           |
+--------+-------------+
14 rows in set
```

---

## Note
If your SQL engine supports `INITCAP`, you can use:
```sql
SELECT INITCAP(ENAME) AS EMP_NAME_PROPER
FROM EMPLOYEE;
```
