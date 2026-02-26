## SQL Queries with Outputs

```sql
-- 1) Compute number of days remaining in this year
SELECT DATEDIFF(STR_TO_DATE(CONCAT(YEAR(CURDATE()), '-12-31'), '%Y-%m-%d'), CURDATE()) AS days_remaining_in_year;
```

```text
+------------------------+
| days_remaining_in_year |
+------------------------+
| 308                    |
+------------------------+
```

```sql
-- 2) Find highest salary, lowest salary, and difference
SELECT
    MAX(sal) AS highest_salary,
    MIN(sal) AS lowest_salary,
    MAX(sal) - MIN(sal) AS salary_difference
FROM emp;
```

```text
+----------------+---------------+-------------------+
| highest_salary | lowest_salary | salary_difference |
+----------------+---------------+-------------------+
| 5000           | 800           | 4200              |
+----------------+---------------+-------------------+
```

```sql
-- 3) List employees whose commission is greater than 25% of salary
SELECT empno, ename, sal, comm
FROM emp
WHERE IFNULL(comm, 0) > 0.25 * sal;
```

```text
+-------+--------+------+------+
| empno | ename  | sal  | comm |
+-------+--------+------+------+
| 7521  | WARD   | 1250 | 500  |
| 7654  | MARTIN | 1250 | 1400 |
+-------+--------+------+------+
```

```sql
-- 4) Display salary in dollar format
SELECT empno, ename, CONCAT('$', FORMAT(sal, 2)) AS salary_in_dollars
FROM emp;
```

```text
+-------+-------+-------------------+
| empno | ename | salary_in_dollars |
+-------+-------+-------------------+
| 7369  | SMITH | $800.00           |
| 7499  | ALLEN | $1,600.00         |
| 7839  | KING  | $5,000.00         |
+-------+-------+-------------------+
```

```sql
-- 5) Matrix query: job-wise salary by department and total salary for all departments
SELECT
    job AS job_title,
    SUM(CASE WHEN deptno = 10 THEN sal ELSE 0 END) AS dept_10_salary,
    SUM(CASE WHEN deptno = 20 THEN sal ELSE 0 END) AS dept_20_salary,
    SUM(CASE WHEN deptno = 30 THEN sal ELSE 0 END) AS dept_30_salary,
    SUM(sal) AS total_salary_all_departments
FROM emp
GROUP BY job;
```

```text
+-----------+----------------+----------------+----------------+------------------------------+
| job_title | dept_10_salary | dept_20_salary | dept_30_salary | total_salary_all_departments |
+-----------+----------------+----------------+----------------+------------------------------+
| ANALYST   | 0              | 6000           | 0              | 6000                         |
| CLERK     | 1300           | 1900           | 950            | 4150                         |
| MANAGER   | 2450           | 2975           | 2850           | 8275                         |
| PRESIDENT | 5000           | 0              | 0              | 5000                         |
| SALESMAN  | 0              | 0              | 5600           | 5600                         |
+-----------+----------------+----------------+----------------+------------------------------+
```

```sql
-- 6) Total employees and count hired in 1980, 1981, 1982, 1983
SELECT
    COUNT(*) AS total_employees,
    SUM(CASE WHEN YEAR(hiredate) = 1980 THEN 1 ELSE 0 END) AS hired_1980,
    SUM(CASE WHEN YEAR(hiredate) = 1981 THEN 1 ELSE 0 END) AS hired_1981,
    SUM(CASE WHEN YEAR(hiredate) = 1982 THEN 1 ELSE 0 END) AS hired_1982,
    SUM(CASE WHEN YEAR(hiredate) = 1983 THEN 1 ELSE 0 END) AS hired_1983
FROM emp;
```

```text
+-----------------+------------+------------+------------+------------+
| total_employees | hired_1980 | hired_1981 | hired_1982 | hired_1983 |
+-----------------+------------+------------+------------+------------+
| 14              | 1          | 10         | 1          | 0          |
+-----------------+------------+------------+------------+------------+
```

```sql
-- 7) Get last Sunday of any month (replace date with any date in target month)
SELECT DATE_SUB(
         LAST_DAY('2026-02-10'),
         INTERVAL (DAYOFWEEK(LAST_DAY('2026-02-10')) - 1) DAY
       ) AS last_sunday_of_month;
```

```text
+----------------------+
| last_sunday_of_month |
+----------------------+
| 2026-02-22           |
+----------------------+
```

```sql
-- 8) Display department numbers and total employees in each department
SELECT deptno AS department_no, COUNT(*) AS employee_count
FROM emp
GROUP BY deptno;
```

```text
+---------------+----------------+
| department_no | employee_count |
+---------------+----------------+
| 10            | 3              |
| 20            | 5              |
| 30            | 6              |
+---------------+----------------+
```

```sql
-- 9) Display various jobs and total employees within each job group
SELECT job AS job_title, COUNT(*) AS employee_count
FROM emp
GROUP BY job;
```

```text
+-----------+----------------+
| job_title | employee_count |
+-----------+----------------+
| ANALYST   | 2              |
| CLERK     | 4              |
| MANAGER   | 3              |
| PRESIDENT | 1              |
| SALESMAN  | 4              |
+-----------+----------------+
```

```sql
-- 10) Display department numbers and total salary for each department
SELECT deptno AS department_no, SUM(sal) AS total_salary
FROM emp
GROUP BY deptno;
```

```text
+---------------+--------------+
| department_no | total_salary |
+---------------+--------------+
| 10            | 8750         |
| 20            | 10875        |
| 30            | 9400         |
+---------------+--------------+
```

```sql
