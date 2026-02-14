# DBMS Lab Experiment 05

> **Experiment:** Aggregate and String Functions on `EMPLOYEE` Table

---

## SQL Queries and Results

### 1) Display the total number of employee working in the company.
```sql
SELECT COUNT(*) AS TOTAL_EMPLOYEES
FROM EMPLOYEE;
```
**Result:** `14`

### 2) Display the total salary being paid to all employees.
```sql
SELECT SUM(SAL) AS TOTAL_SALARY
FROM EMPLOYEE;
```
**Result:** `29025`

### 3) Display the maximum salary from employee table.
```sql
SELECT MAX(SAL) AS MAX_SALARY
FROM EMPLOYEE;
```
**Result:** `5000`

### 4) Display the minimum salary from employee table.
```sql
SELECT MIN(SAL) AS MIN_SALARY
FROM EMPLOYEE;
```
**Result:** `800`

### 5) Display the average salary from employee table.
```sql
SELECT AVG(SAL) AS AVG_SALARY
FROM EMPLOYEE;
```
**Result:** `2073.2143` (approx)

### 6) Display the maximum salary being paid to clerk.
```sql
SELECT MAX(SAL) AS MAX_CLERK_SALARY
FROM EMPLOYEE
WHERE JOB = 'CLERK';
```
**Result:** `1300`

### 7) Display the maximum salary being paid in dept no 20.
```sql
SELECT MAX(SAL) AS MAX_SALARY_DEPT20
FROM EMPLOYEE
WHERE DEPTNO = 20;
```
**Result:** `5000`

### 8) Display the minimum salary paid to any salesman.
```sql
SELECT MIN(SAL) AS MIN_SALESMAN_SALARY
FROM EMPLOYEE
WHERE JOB = 'SALESMAN';
```
**Result:** `1250`

### 9) Display the average salary drawn by managers.
```sql
SELECT AVG(SAL) AS AVG_MANAGER_SALARY
FROM EMPLOYEE
WHERE JOB = 'MANAGER';
```
**Result:** `2758.3333` (approx)

### 10) Display the total salary drawn by analyst working in dept no 40.
```sql
SELECT SUM(SAL) AS TOTAL_ANALYST_SALARY_DEPT40
FROM EMPLOYEE
WHERE JOB = 'ANALYST' AND DEPTNO = 40;
```
**Result:** `3000`

### 11) Display the names of the employee in Uppercase.
```sql
SELECT UPPER(ENAME) AS EMP_NAME_UPPER
FROM EMPLOYEE;
```

### 12) Display the names of the employee in Lowercase.
```sql
SELECT LOWER(ENAME) AS EMP_NAME_LOWER
FROM EMPLOYEE;
```

### 13) Display the names of the employee in Proper case.
```sql
-- MySQL equivalent of INITCAP
SELECT CONCAT(UPPER(LEFT(ENAME, 1)), LOWER(SUBSTRING(ENAME, 2))) AS EMP_NAME_PROPER
FROM EMPLOYEE;
```

### 14) Display the length of your name using appropriate function.
```sql
SELECT LENGTH('PriyanshuYadav') AS NAME_LENGTH;
```
**Result:** `14`

### 15) Display the length of all the employee names.
```sql
SELECT ENAME, LENGTH(ENAME) AS NAME_LENGTH
FROM EMPLOYEE;
```

---

## Note
If your SQL engine supports `INITCAP`, you can use:
```sql
SELECT INITCAP(ENAME) AS EMP_NAME_PROPER
FROM EMPLOYEE;
```
