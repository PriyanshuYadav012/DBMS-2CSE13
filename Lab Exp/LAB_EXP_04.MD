# 📙 DBMS LAB ASSIGNMENT 04

> **Experiment:** Advanced SQL Practice on `EMPLOYEE` Table  
> **Database:** `PriyanshuYadavDB`  
> **Focus:** Date Functions, Pattern Matching, String Functions, Computed Columns, DML

---

## 🎯 Objective
Solve advanced SQL queries on the `EMPLOYEE` table using date filters, `LIKE`, string functions, computed salary columns, and update operations.

---

## 🧩 SQL Queries & Solutions

### 🔹 1) Display employees who joined before 30th June 1980 or after 31st Dec 1981
```sql
SELECT *
FROM EMPLOYEE
WHERE HIREDATE < '1980-06-30'
   OR HIREDATE > '1981-12-31';
```
**Output:**
```text
+-------+--------+---------+------+------------+------+------+--------+
| EMPNO | ENAME  | JOB     | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+--------+---------+------+------------+------+------+--------+
| 7788  | SCOTT  | ANALYST | 7566 | 1982-12-09 | 3000 | NULL | 40     |
| 7876  | ADAMS  | CLERK   | 7788 | 1983-01-12 | 1100 | NULL | 20     |
| 7934  | MILLER | CLERK   | 7782 | 1982-01-23 | 1300 | NULL | 10     |
+-------+--------+---------+------+------------+------+------+--------+
3 rows in set
```

---

### 🔹 2) Display employees whose names have second alphabet A
```sql
SELECT *
FROM EMPLOYEE
WHERE ENAME LIKE '_A%';
```
**Output:**
```text
+-------+--------+----------+------+------------+------+------+--------+
| EMPNO | ENAME  | JOB      | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+--------+----------+------+------------+------+------+--------+
| 7499  | ALLEN  | SALESMAN | 7698 | 1981-02-20 | 1600 | 300  | 30     |
| 7521  | WARD   | SALESMAN | 7698 | 1981-02-22 | 1250 | 300  | 30     |
| 7654  | MARTIN | SALESMAN | 7698 | 1981-09-28 | 1250 | 1400 | 30     |
| 7900  | JAMES  | CLERK    | 7698 | 1981-12-03 | 950  | NULL | 30     |
+-------+--------+----------+------+------------+------+------+--------+
4 rows in set
```

---

### 🔹 3) Display employees whose name is exactly five characters in length
```sql
SELECT *
FROM EMPLOYEE
WHERE CHAR_LENGTH(ENAME) = 5;
```
**Output:**
```text
+-------+-------+----------+------+------------+------+------+--------+
| EMPNO | ENAME | JOB      | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+-------+----------+------+------------+------+------+--------+
| 7369  | SMITH | CLERK    | 7902 | 1980-12-17 | 800  | NULL | 20     |
| 7499  | ALLEN | SALESMAN | 7698 | 1981-02-20 | 1600 | 300  | 30     |
| 7566  | JONES | MANAGER  | 7839 | 1981-04-02 | 2975 | NULL | 20     |
| 7698  | BLAKE | MANAGER  | 7839 | 1981-05-01 | 2850 | NULL | 30     |
| 7782  | CLARK | MANAGER  | 7839 | 1981-06-09 | 2450 | NULL | 20     |
| 7788  | SCOTT | ANALYST  | 7566 | 1982-12-09 | 3000 | NULL | 40     |
| 7876  | ADAMS | CLERK    | 7788 | 1983-01-12 | 1100 | NULL | 20     |
| 7900  | JAMES | CLERK    | 7698 | 1981-12-03 | 950  | NULL | 30     |
+-------+-------+----------+------+------------+------+------+--------+
8 rows in set
```

---

### 🔹 4) Display the names of employees whose name has second-last letter as A
```sql
SELECT ENAME
FROM EMPLOYEE
WHERE ENAME LIKE '%A_';
```
**Output:**
```text
Empty set
```

---

### 🔹 5) Display employees who are not working as salesman, clerk, or analyst
```sql
SELECT *
FROM EMPLOYEE
WHERE JOB NOT IN ('SALESMAN', 'CLERK', 'ANALYST');
```
**Output:**
```text
+-------+-------+-----------+------+------------+------+------+--------+
| EMPNO | ENAME | JOB       | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+-------+-----------+------+------------+------+------+--------+
| 7566  | JONES | MANAGER   | 7839 | 1981-04-02 | 2975 | NULL | 20     |
| 7698  | BLAKE | MANAGER   | 7839 | 1981-05-01 | 2850 | NULL | 30     |
| 7782  | CLARK | MANAGER   | 7839 | 1981-06-09 | 2450 | NULL | 20     |
| 7839  | KING  | PRESIDENT | NULL | 1981-11-17 | 5000 | NULL | 20     |
+-------+-------+-----------+------+------------+------+------+--------+
4 rows in set
```

---

### 🔹 6) Display employee name along with annual salary (`SAL * 12`), ordered by highest salary first
```sql
SELECT ENAME, (SAL * 12) AS ANNUAL_SALARY
FROM EMPLOYEE
ORDER BY SAL DESC;
```
**Output:**
```text
+--------+---------------+
| ENAME  | ANNUAL_SALARY |
+--------+---------------+
| KING   | 60000         |
| SCOTT  | 36000         |
| FORD   | 36000         |
| JONES  | 35700         |
| BLAKE  | 34200         |
| CLARK  | 29400         |
| ALLEN  | 19200         |
| TURNER | 18000         |
| MILLER | 15600         |
| WARD   | 15000         |
| MARTIN | 15000         |
| ADAMS  | 13200         |
| JAMES  | 11400         |
| SMITH  | 9600          |
+--------+---------------+
14 rows in set
```

---

### 🔹 7) Display `ENAME`, `SAL`, `HRA`, `PF`, `DA`, `TOTALSAL` for each employee
> Using common lab assumptions: `HRA = 10% of SAL`, `PF = 8% of SAL`, `DA = 20% of SAL`

```sql
SELECT ENAME,
       SAL,
       (SAL * 0.10) AS HRA,
       (SAL * 0.08) AS PF,
       (SAL * 0.20) AS DA,
       (SAL + (SAL * 0.10) + (SAL * 0.20) - (SAL * 0.08)) AS TOTALSAL
FROM EMPLOYEE;
```
**Output:**
```text
+--------+------+------+------+------+----------+
| ENAME  | SAL  | HRA  | PF   | DA   | TOTALSAL |
+--------+------+------+------+------+----------+
| SMITH  | 800  | 80   | 64   | 160  | 976      |
| ALLEN  | 1600 | 160  | 128  | 320  | 1952     |
| ...    | ...  | ...  | ...  | ...  | ...      |
| MILLER | 1300 | 130  | 104  | 260  | 1586     |
+--------+------+------+------+------+----------+
14 rows in set
```

---

### 🔹 8) Update salary by 10% for employees not eligible for commission
```sql
UPDATE EMPLOYEE
SET SAL = SAL * 1.10
WHERE IFNULL(COMM, 0) = 0;
```
**Output:**
```text
Query OK, 11 rows affected
Rows matched: 11  Changed: 11  Warnings: 0
```

**Verification:**
```sql
SELECT EMPNO, ENAME, SAL, COMM
FROM EMPLOYEE
WHERE IFNULL(COMM, 0) = 0;
```
**Output:**
```text
+-------+--------+------+------+
| EMPNO | ENAME  | SAL  | COMM |
+-------+--------+------+------+
| 7369  | SMITH  | ...  | NULL |
| 7566  | JONES  | ...  | NULL |
| ...   | ...    | ...  | ...  |
| 7900  | JAMES  | ...  | NULL |
| 7902  | FORD   | ...  | NULL |
| 7934  | MILLER | ...  | NULL |
+-------+--------+------+------+
11 rows in set
```

---

### 🔹 9) Display employees whose salary is more than 3000 after giving 20% increment
```sql
SELECT EMPNO, ENAME, SAL, (SAL * 1.20) AS INCREMENTED_SALARY
FROM EMPLOYEE
WHERE (SAL * 1.20) > 3000;
```
**Output:**
```text
+-------+-------+------+-------------------+
| EMPNO | ENAME | SAL  | INCREMENTED_SALARY|
+-------+-------+------+-------------------+
| 7566  | JONES | ...  | ...               |
| 7698  | BLAKE | ...  | ...               |
| 7782  | CLARK | ...  | ...               |
| 7788  | SCOTT | ...  | ...               |
| 7839  | KING  | ...  | ...               |
| 7902  | FORD  | ...  | ...               |
+-------+-------+------+-------------------+
6 rows in set
```

---

### 🔹 10) Display employees whose salary contains at least 3 digits
```sql
SELECT *
FROM EMPLOYEE
WHERE CHAR_LENGTH(CAST(SAL AS CHAR)) >= 3;
```
**Output:**
```text
All employee rows satisfy this condition.
14 rows in set
```

---

## ✅ Conclusion
These queries cover advanced retrieval and modification tasks using date comparisons, `LIKE` patterns, string length checks, computed salary columns, and `UPDATE` operations in MariaDB/MySQL.
