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

## 📝 Observations

- `DISTINCT` removes duplicate values from the selected column(s).
- `WHERE` clause filters rows based on given conditions.
- `IN` simplifies checking multiple possible values in a single condition.
- `NOT IN` excludes rows matching listed values.
- `BETWEEN` is useful for inclusive range-based filtering.
- `LIKE 'M%'` performs prefix-based pattern matching.
- Combining conditions with `AND` provides precise filtering of records.

---

## 🎓 Viva Questions

### ❓ 1) What is the difference between `DISTINCT` and `GROUP BY`?
**Answer:** `DISTINCT` removes duplicate rows in the selected output, while `GROUP BY` groups rows for aggregation (like `COUNT`, `SUM`, etc.).

### ❓ 2) Is `BETWEEN` inclusive in SQL?
**Answer:** Yes. `BETWEEN a AND b` includes both boundary values `a` and `b`.

### ❓ 3) Why is `IN` preferred over multiple `OR` conditions?
**Answer:** `IN` is shorter, cleaner, and easier to read/maintain when checking one column against multiple values.

### ❓ 4) What does `LIKE 'M%'` mean?
**Answer:** It selects rows where the value starts with the letter `M`.

### ❓ 5) What is the role of `WHERE` clause in SQL?
**Answer:** It filters rows returned by a query based on specified conditions.

### ❓ 6) Can we combine `IN` with `AND` in one query?
**Answer:** Yes. `IN` can be combined with `AND`/`OR` to build complex filtering conditions.
