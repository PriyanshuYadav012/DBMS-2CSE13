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

---

### 🔹 2) Display employees whose names have second alphabet A
```sql
SELECT *
FROM EMPLOYEE
WHERE ENAME LIKE '_A%';
```

---

### 🔹 3) Display employees whose name is exactly five characters in length
```sql
SELECT *
FROM EMPLOYEE
WHERE CHAR_LENGTH(ENAME) = 5;
```

---

### 🔹 4) Display the names of employees whose name has second-last letter as A
```sql
SELECT ENAME
FROM EMPLOYEE
WHERE ENAME LIKE '%A_';
```

---

### 🔹 5) Display employees who are not working as salesman, clerk, or analyst
```sql
SELECT *
FROM EMPLOYEE
WHERE JOB NOT IN ('SALESMAN', 'CLERK', 'ANALYST');
```

---

### 🔹 6) Display employee name along with annual salary (`SAL * 12`), ordered by highest salary first
```sql
SELECT ENAME, (SAL * 12) AS ANNUAL_SALARY
FROM EMPLOYEE
ORDER BY SAL DESC;
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

---

### 🔹 8) Update salary by 10% for employees not eligible for commission
```sql
UPDATE EMPLOYEE
SET SAL = SAL * 1.10
WHERE IFNULL(COMM, 0) = 0;
```

**Verification:**
```sql
SELECT EMPNO, ENAME, SAL, COMM
FROM EMPLOYEE
WHERE IFNULL(COMM, 0) = 0;
```

---

### 🔹 9) Display employees whose salary is more than 3000 after giving 20% increment
```sql
SELECT EMPNO, ENAME, SAL, (SAL * 1.20) AS INCREMENTED_SALARY
FROM EMPLOYEE
WHERE (SAL * 1.20) > 3000;
```

---

### 🔹 10) Display employees whose salary contains at least 3 digits
```sql
SELECT *
FROM EMPLOYEE
WHERE CHAR_LENGTH(CAST(SAL AS CHAR)) >= 3;
```

---

## ✅ Conclusion
These queries cover advanced retrieval and modification tasks using date comparisons, `LIKE` patterns, string length checks, computed salary columns, and `UPDATE` operations in MariaDB/MySQL.
