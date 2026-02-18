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

---

### 🔹 2) List all information about employees in Department Number 30
```sql
SELECT *
FROM EMPLOYEE
WHERE DEPTNO = 30;
```

---

### 🔹 3) Find all department numbers with department names where department number is greater than 20
```sql
SELECT DEPTNO, DNAME
FROM DEPARTMENT
WHERE DEPTNO > 20;
```

---

### 🔹 4) Find all information about managers and clerks in Department 30
```sql
SELECT *
FROM EMPLOYEE
WHERE DEPTNO = 30
  AND JOB IN ('MANAGER', 'CLERK');
```

---

### 🔹 5) List Employee name, Employee number, and department of all clerks
```sql
SELECT ENAME, EMPNO, DEPTNO
FROM EMPLOYEE
WHERE JOB = 'CLERK';
```

---

### 🔹 6) Find all managers not in Department 30
```sql
SELECT *
FROM EMPLOYEE
WHERE JOB = 'MANAGER'
  AND DEPTNO <> 30;
```

---

### 🔹 7) List information about employees in Department 10 who are not managers or clerks
```sql
SELECT *
FROM EMPLOYEE
WHERE DEPTNO = 10
  AND JOB NOT IN ('MANAGER', 'CLERK');
```

---

### 🔹 8) Find employees and jobs earning between 1200 and 1400
```sql
SELECT ENAME, JOB
FROM EMPLOYEE
WHERE SAL BETWEEN 1200 AND 1400;
```

---

### 🔹 9) List Name and Department Number of employees who are clerks, analysts, or salesmen
```sql
SELECT ENAME, DEPTNO
FROM EMPLOYEE
WHERE JOB IN ('CLERK', 'ANALYST', 'SALESMAN');
```

---

### 🔹 10) List Name and Department Number of employees whose names begin with M
```sql
SELECT ENAME, DEPTNO
FROM EMPLOYEE
WHERE ENAME LIKE 'M%';
```

---

## ✅ Conclusion
All required SQL queries were written and organized using appropriate clauses: `DISTINCT`, `WHERE`, `IN`, `NOT IN`, `BETWEEN`, and `LIKE`.

---


