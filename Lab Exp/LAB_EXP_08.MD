# DBMS LAB EXPERIMENT 08

> **Experiment:** Joins, Self Joins, and Grouping Queries on `EMPLOYEE`, `DEPT`, `SALGRADE`

---

## SQL Queries and Solutions

### 1) Display all employees with their department name
```sql
SELECT e.empno,
       e.ename,
       e.deptno,
       d.dname AS dept_name
FROM employee e
JOIN dept d ON d.deptno = e.deptno;
```

### 2) Display employees whose manager name is JONES, and display their manager name too
```sql
SELECT e.empno,
       e.ename,
       m.ename AS manager_name
FROM employee e
JOIN employee m ON e.mgr = m.empno
WHERE UPPER(m.ename) = 'JONES';
```

### 3) Display employee name, job, department name, manager name, and grade (department-wise)
```sql
SELECT d.dname AS dept_name,
       e.ename AS employee_name,
       e.job,
       IFNULL(m.ename, 'NO MANAGER') AS manager_name,
       s.grade
FROM employee e
JOIN dept d ON d.deptno = e.deptno
LEFT JOIN employee m ON e.mgr = m.empno
JOIN salgrade s ON e.sal BETWEEN s.losal AND s.hisal
ORDER BY d.dname, e.ename;
```

### 4) List employee name, job, salary grade, and department name for all except CLERK; sort by salary so highest appears first
```sql
SELECT e.ename,
       e.job,
       s.grade,
       d.dname AS dept_name,
       e.sal
FROM employee e
JOIN dept d ON d.deptno = e.deptno
JOIN salgrade s ON e.sal BETWEEN s.losal AND s.hisal
WHERE UPPER(e.job) <> 'CLERK'
ORDER BY e.sal DESC;
```

### 5) Display employee name, job, and manager name; include employees without manager
```sql
SELECT e.ename AS employee_name,
       e.job,
       IFNULL(m.ename, 'NO MANAGER') AS manager_name
FROM employee e
LEFT JOIN employee m ON e.mgr = m.empno;
```

### 6) List employee name, job, annual salary, deptno, dept name, and grade who earn 36000/year or who are not CLERKS
```sql
SELECT e.ename,
       e.job,
       (e.sal * 12) AS annual_salary,
       e.deptno,
       d.dname,
       s.grade
FROM employee e
JOIN dept d ON d.deptno = e.deptno
JOIN salgrade s ON e.sal BETWEEN s.losal AND s.hisal
WHERE (e.sal * 12) = 36000
   OR UPPER(e.job) <> 'CLERK';
```

### 7) List ename, job, annual salary, deptno, dname, and grade who earn 30000/year and are not CLERKS
```sql
SELECT e.ename,
       e.job,
       (e.sal * 12) AS annual_salary,
       e.deptno,
       d.dname,
       s.grade
FROM employee e
JOIN dept d ON d.deptno = e.deptno
JOIN salgrade s ON e.sal BETWEEN s.losal AND s.hisal
WHERE (e.sal * 12) = 30000
  AND UPPER(e.job) <> 'CLERK';
```

### 8) List all employees by name and number with their manager's name and number; show 'NO MANAGER' where missing
```sql
SELECT e.empno AS employee_no,
       e.ename AS employee_name,
       IFNULL(m.empno, 0) AS manager_no,
       IFNULL(m.ename, 'NO MANAGER') AS manager_name
FROM employee e
LEFT JOIN employee m ON e.mgr = m.empno;
```

### 9) Select department name, department number, and sum of salary
```sql
SELECT d.dname,
       d.deptno,
       SUM(e.sal) AS total_salary
FROM dept d
LEFT JOIN employee e ON e.deptno = d.deptno
GROUP BY d.dname, d.deptno;
```

### 10) Display employee number, employee name, and location of the department in which employee works
```sql
SELECT e.empno,
       e.ename,
       d.loc
FROM employee e
JOIN dept d ON d.deptno = e.deptno;
```

### 11) Display employee name and department name for each employee
```sql
SELECT e.ename,
       d.dname AS department_name
FROM employee e
JOIN dept d ON d.deptno = e.deptno;
```
