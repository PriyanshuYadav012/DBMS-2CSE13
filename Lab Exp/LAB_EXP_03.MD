# DBMS LAB ASSIGNMENT 03

> **Experiment:** Advanced Data Retrieval on `EMPLOYEE` Table  
> **Database:** `PriyanshuYadavDB`  
> **Focus:** `ORDER BY`, `LIKE`, `IN`, `IS NULL`, Calculated Columns

---

## Objective
Perform advanced SQL queries using sorting, pattern matching, set filtering, null checks, and computed values.

---

## SQL Queries & Solutions

### 1) List all employees and jobs in Department 30 in descending order of salary
```sql
SELECT ENAME, JOB
FROM EMPLOYEE
WHERE DEPTNO = 30
ORDER BY SAL DESC;
```

**Expected Output:**
```text
+--------+----------+
| ENAME  | JOB      |
+--------+----------+
| BLAKE  | MANAGER  |
| ALLEN  | SALESMAN |
| TURNER | SALESMAN |
| WARD   | SALESMAN |
| MARTIN | SALESMAN |
| JAMES  | CLERK    |
+--------+----------+
6 rows in set
```

---

### 2) List job and department number of employees whose name is five letters long, starts with 'A' and ends with 'N'
```sql
SELECT JOB, DEPTNO
FROM EMPLOYEE
WHERE ENAME LIKE 'A___N';
```

**Expected Output:**
```text
+----------+--------+
| JOB      | DEPTNO |
+----------+--------+
| SALESMAN |     30 |
+----------+--------+
1 row in set
```

---

### 3) Display the names of employees whose name starts with 'S'
```sql
SELECT ENAME
FROM EMPLOYEE
WHERE ENAME LIKE 'S%';
```

**Expected Output:**
```text
+-------+
| ENAME |
+-------+
| SMITH |
| SCOTT |
+-------+
2 rows in set
```

---

### 4) Display the names of employees whose name ends with 'S'
```sql
SELECT ENAME
FROM EMPLOYEE
WHERE ENAME LIKE '%S';
```

**Expected Output:**
```text
+-------+
| ENAME |
+-------+
| JONES |
| ADAMS |
| JAMES |
+-------+
3 rows in set
```

---

### 5) Display names of employees working in department 10, 20, or 40 OR working as clerk, salesman, or analyst
```sql
SELECT ENAME
FROM EMPLOYEE
WHERE DEPTNO IN (10, 20, 40)
   OR JOB IN ('CLERK', 'SALESMAN', 'ANALYST');
```

**Expected Output:**
```text
+--------+
| ENAME  |
+--------+
| SMITH  |
| ALLEN  |
| WARD   |
| JONES  |
| MARTIN |
| CLARK  |
| SCOTT  |
| KING   |
| TURNER |
| ADAMS  |
| JAMES  |
| FORD   |
| MILLER |
+--------+
13 rows in set
```

---

### 6) Display employee number and names for employees who earn commission
```sql
SELECT EMPNO, ENAME
FROM EMPLOYEE
WHERE COMM IS NOT NULL
  AND COMM > 0;
```

**Expected Output:**
```text
+-------+--------+
| EMPNO | ENAME  |
+-------+--------+
|  7499 | ALLEN  |
|  7521 | WARD   |
|  7654 | MARTIN |
+-------+--------+
3 rows in set
```

---

### 7) Display employee number and total salary for each employee
```sql
SELECT EMPNO, (SAL + IFNULL(COMM, 0)) AS TOTAL_SALARY
FROM EMPLOYEE;
```

**Expected Output:**
```text
+-------+--------------+
| EMPNO | TOTAL_SALARY |
+-------+--------------+
|  7369 |          800 |
|  7499 |         1900 |
|  7521 |         1550 |
|  7566 |         2975 |
|  7654 |         2650 |
|  7698 |         2850 |
|  7782 |         2450 |
|  7788 |         3000 |
|  7839 |         5000 |
|  7844 |         1500 |
|  7876 |         1100 |
|  7900 |          950 |
|  7902 |         3000 |
|  7934 |         1300 |
+-------+--------------+
14 rows in set
```

---

### 8) Display employee number and annual salary for each employee
```sql
SELECT EMPNO, (SAL * 12) AS ANNUAL_SALARY
FROM EMPLOYEE;
```

**Expected Output:**
```text
+-------+---------------+
| EMPNO | ANNUAL_SALARY |
+-------+---------------+
|  7369 |          9600 |
|  7499 |         19200 |
|  7521 |         15000 |
|  7566 |         35700 |
|  7654 |         15000 |
|  7698 |         34200 |
|  7782 |         29400 |
|  7788 |         36000 |
|  7839 |         60000 |
|  7844 |         18000 |
|  7876 |         13200 |
|  7900 |         11400 |
|  7902 |         36000 |
|  7934 |         15600 |
+-------+---------------+
14 rows in set
```

---

### 9) Display names of all employees working as clerks and earning more than 3000
```sql
SELECT ENAME
FROM EMPLOYEE
WHERE JOB = 'CLERK'
  AND SAL > 3000;
```

**Expected Output:**
```text
Empty set
```

---

### 10) Display names of employees working as clerk, salesman, or analyst and earning more than 3000
```sql
SELECT ENAME
FROM EMPLOYEE
WHERE JOB IN ('CLERK', 'SALESMAN', 'ANALYST')
  AND SAL > 3000;
```

**Expected Output:**
```text
Empty set
```

---

## Conclusion
All requested advanced retrieval queries were completed using sorting (`ORDER BY`), pattern matching (`LIKE`), list filters (`IN`), null handling (`IS NOT NULL`, `IFNULL`), and calculated columns.
