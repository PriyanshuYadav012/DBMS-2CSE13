# 📘 DBMS LAB ASSIGNMENT 02

> **Experiment:** SQL Query Practice on `EMPLOYEE` Table  
> **Database:** `PriyanshuYadavDB`  
> **Focus:** Selection, Filtering, Pattern Matching, `IN`, `BETWEEN`, `DISTINCT`

---

## 🎯 Objective
Perform queries using the `EMPLOYEE` table to retrieve data using various SQL clauses.

---

## 🧩 SQL Queries & Solutions

### 🔹 1) List all distinct jobs in `EMPLOYEE`
```sql
SELECT DISTINCT JOB
FROM EMPLOYEE;
```
**Output:**
```text
+-----------+
| JOB       |
+-----------+
| CLERK     |
| SALESMAN  |
| MANAGER   |
| ANALYST   |
| PRESIDENT |
+-----------+
5 rows in set
```

---

### 🔹 2) List all information about employees in Department Number 30
```sql
SELECT *
FROM EMPLOYEE
WHERE DEPTNO = 30;
```
**Output:**
```text
+-------+--------+----------+------+------------+------+------+--------+
| EMPNO | ENAME  | JOB      | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+--------+----------+------+------------+------+------+--------+
| 7499  | ALLEN  | SALESMAN | 7698 | 1981-02-20 | 1600 | 300  | 30     |
| 7521  | WARD   | SALESMAN | 7698 | 1981-02-22 | 1250 | 300  | 30     |
| 7654  | MARTIN | SALESMAN | 7698 | 1981-09-28 | 1250 | 1400 | 30     |
| 7698  | BLAKE  | MANAGER  | 7839 | 1981-05-01 | 2850 | NULL | 30     |
| 7844  | TURNER | SALESMAN | 7698 | 1981-09-08 | 1500 | 0    | 30     |
| 7900  | JAMES  | CLERK    | 7698 | 1981-12-03 | 950  | NULL | 30     |
+-------+--------+----------+------+------------+------+------+--------+
6 rows in set
```

---

### 🔹 3) Find all department numbers with department names where department number is greater than 20
```sql
SELECT DEPTNO, DNAME
FROM DEPARTMENT
WHERE DEPTNO > 20;
```
**Output:**
```text
+--------+------------+
| DEPTNO | DNAME      |
+--------+------------+
| 30     | SALES      |
| 40     | OPERATIONS |
+--------+------------+
2 rows in set
```

---

### 🔹 4) Find all information about managers and clerks in Department 30
```sql
SELECT *
FROM EMPLOYEE
WHERE DEPTNO = 30
  AND JOB IN ('MANAGER', 'CLERK');
```
**Output:**
```text
+-------+-------+---------+------+------------+------+------+--------+
| EMPNO | ENAME | JOB     | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+-------+---------+------+------------+------+------+--------+
| 7698  | BLAKE | MANAGER | 7839 | 1981-05-01 | 2850 | NULL | 30     |
| 7900  | JAMES | CLERK   | 7698 | 1981-12-03 | 950  | NULL | 30     |
+-------+-------+---------+------+------------+------+------+--------+
2 rows in set
```

---

### 🔹 5) List Employee name, Employee number, and department of all clerks
```sql
SELECT ENAME, EMPNO, DEPTNO
FROM EMPLOYEE
WHERE JOB = 'CLERK';
```
**Output:**
```text
+--------+-------+--------+
| ENAME  | EMPNO | DEPTNO |
+--------+-------+--------+
| SMITH  | 7369  | 20     |
| ADAMS  | 7876  | 20     |
| JAMES  | 7900  | 30     |
| MILLER | 7934  | 10     |
+--------+-------+--------+
4 rows in set
```

---

### 🔹 6) Find all managers not in Department 30
```sql
SELECT *
FROM EMPLOYEE
WHERE JOB = 'MANAGER'
  AND DEPTNO <> 30;
```
**Output:**
```text
+-------+-------+---------+------+------------+------+------+--------+
| EMPNO | ENAME | JOB     | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+-------+---------+------+------------+------+------+--------+
| 7566  | JONES | MANAGER | 7839 | 1981-04-02 | 2975 | NULL | 20     |
| 7782  | CLARK | MANAGER | 7839 | 1981-06-09 | 2450 | NULL | 20     |
+-------+-------+---------+------+------------+------+------+--------+
2 rows in set
```

---

### 🔹 7) List information about employees in Department 10 who are not managers or clerks
```sql
SELECT *
FROM EMPLOYEE
WHERE DEPTNO = 10
  AND JOB NOT IN ('MANAGER', 'CLERK');
```
**Output:**
```text
Empty set
```

---

### 🔹 8) Find employees and jobs earning between 1200 and 1400
```sql
SELECT ENAME, JOB
FROM EMPLOYEE
WHERE SAL BETWEEN 1200 AND 1400;
```
**Output:**
```text
+--------+----------+
| ENAME  | JOB      |
+--------+----------+
| WARD   | SALESMAN |
| MARTIN | SALESMAN |
| MILLER | CLERK    |
+--------+----------+
3 rows in set
```

---

### 🔹 9) List Name and Department Number of employees who are clerks, analysts, or salesmen
```sql
SELECT ENAME, DEPTNO
FROM EMPLOYEE
WHERE JOB IN ('CLERK', 'ANALYST', 'SALESMAN');
```
**Output:**
```text
+--------+--------+
| ENAME  | DEPTNO |
+--------+--------+
| SMITH  | 20     |
| ALLEN  | 30     |
| WARD   | 30     |
| MARTIN | 30     |
| SCOTT  | 40     |
| TURNER | 30     |
| ADAMS  | 20     |
| JAMES  | 30     |
| FORD   | 20     |
| MILLER | 10     |
+--------+--------+
10 rows in set
```

---

### 🔹 10) List Name and Department Number of employees whose names begin with M
```sql
SELECT ENAME, DEPTNO
FROM EMPLOYEE
WHERE ENAME LIKE 'M%';
```
**Output:**
```text
+--------+--------+
| ENAME  | DEPTNO |
+--------+--------+
| MARTIN | 30     |
| MILLER | 10     |
+--------+--------+
2 rows in set
```

---

## ✅ Conclusion
All required SQL queries were written and organized using appropriate clauses: `DISTINCT`, `WHERE`, `IN`, `NOT IN`, `BETWEEN`, and `LIKE`.

---

## 📝 Observations

- `DISTINCT` removes duplicate values from the selected column(s).
- `WHERE` clause filters rows based on given conditions.
- `IN` simplifies checking multiple possible values in a single condition.
- `NOT IN` excludes rows matching listed values.
- `BETWEEN` is useful for inclusive range-based filtering.
- `LIKE 'M%'` performs prefix-based pattern matching.
- Combining conditions with `AND` provides precise filtering of records.

---
