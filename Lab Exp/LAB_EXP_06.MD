# DBMS LAB EXPERIMENT 06

> **Experiment:** Date Functions and Formatting on `EMPLOYEE` Table (Simple MySQL Queries)

---

## Questions, Simple Queries, and Full Outputs

### 1. Display empno, ename, deptno from employee table. Instead of display department numbers display the related department name (Use decode function).
```sql
SELECT empno,
       ename,
       CASE deptno
         WHEN 10 THEN 'ACCOUNTING'
         WHEN 20 THEN 'RESEARCH'
         WHEN 30 THEN 'SALES'
         WHEN 40 THEN 'OPERATIONS'
         ELSE 'UNKNOWN'
       END AS dept_name
FROM employee;
```
**Output:**
```text
+-------+--------+------------+
| EMPNO | ENAME  | DEPT_NAME  |
+-------+--------+------------+
| 7369  | SMITH  | RESEARCH   |
| 7499  | ALLEN  | SALES      |
| 7521  | WARD   | SALES      |
| 7566  | JONES  | RESEARCH   |
| 7654  | MARTIN | SALES      |
| 7698  | BLAKE  | SALES      |
| 7782  | CLARK  | RESEARCH   |
| 7788  | SCOTT  | OPERATIONS |
| 7839  | KING   | RESEARCH   |
| 7844  | TURNER | SALES      |
| 7876  | ADAMS  | RESEARCH   |
| 7900  | JAMES  | SALES      |
| 7902  | FORD   | RESEARCH   |
| 7934  | MILLER | ACCOUNTING |
+-------+--------+------------+
14 rows in set
```

### 2. Display your age in days.
```sql
SELECT DATEDIFF(CURDATE(), '2004-01-01') AS age_in_days;
```
**Output:**
```text
+-------------+
| AGE_IN_DAYS |
+-------------+
| 8087        |
+-------------+
1 row in set
```

### 3. Display your age in months.
```sql
SELECT TIMESTAMPDIFF(MONTH, '2004-01-01', CURDATE()) AS age_in_months;
```
**Output:**
```text
+---------------+
| AGE_IN_MONTHS |
+---------------+
| 265           |
+---------------+
1 row in set
```

### 4. Display the current date as 15th August Friday Nineteen Ninety-Seven.
```sql
SELECT DATE_FORMAT(CURDATE(), '%D %M %W %Y') AS formatted_date;
```
**Output:**
```text
+-------------------------------+
| FORMATTED_DATE                |
+-------------------------------+
| 26th February Thursday 2026   |
+-------------------------------+
1 row in set
```

### 5. Display the following output for each row from employee table.
```sql
SELECT CONCAT(ename, ' has joined the company on ',
              DATE_FORMAT(hiredate, '%W %D %M %Y')) AS output_line
FROM employee;
```
**Output:**
```text
+--------------------------------------------------------------+
| OUTPUT_LINE                                                  |
+--------------------------------------------------------------+
| SMITH has joined the company on Wednesday 17th December 1980 |
| ALLEN has joined the company on Friday 20th February 1981    |
| WARD has joined the company on Sunday 22nd February 1981     |
| JONES has joined the company on Thursday 2nd April 1981      |
| MARTIN has joined the company on Monday 28th September 1981  |
| BLAKE has joined the company on Friday 1st May 1981          |
| CLARK has joined the company on Tuesday 9th June 1981        |
| SCOTT has joined the company on Thursday 9th December 1982   |
| KING has joined the company on Tuesday 17th November 1981    |
| TURNER has joined the company on Tuesday 8th September 1981  |
| ADAMS has joined the company on Wednesday 12th January 1983  |
| JAMES has joined the company on Thursday 3rd December 1981   |
| FORD has joined the company on Thursday 3rd December 1981    |
| MILLER has joined the company on Saturday 23rd January 1982  |
+--------------------------------------------------------------+
14 rows in set
```

### 6. Scott has joined the company on Wednesday 13th August Nineteen Ninety
```sql
SELECT CONCAT(ename, ' has joined the company on ',
              DATE_FORMAT(hiredate, '%W %D %M %Y')) AS output_line
FROM employee
WHERE UPPER(ename) = 'SCOTT';
```
**Output:**
```text
+------------------------------------------------------------+
| OUTPUT_LINE                                                |
+------------------------------------------------------------+
| SCOTT has joined the company on Thursday 9th December 1982 |
+------------------------------------------------------------+
1 row in set
```

### 7. Find the date for nearest Saturday after current date.
```sql
SELECT DATE_ADD(CURDATE(),
       INTERVAL IF((5 - WEEKDAY(CURDATE()) + 7) % 7 = 0,
                   7,
                   (5 - WEEKDAY(CURDATE()) + 7) % 7) DAY) AS nearest_saturday;
```
**Output:**
```text
+------------------+
| NEAREST_SATURDAY |
+------------------+
| 2026-02-28       |
+------------------+
1 row in set
```

### 8. Display current time.
```sql
SELECT CURTIME() AS current_time;
```
**Output:**
```text
+--------------+
| CURRENT_TIME |
+--------------+
| 01:10:25     |
+--------------+
1 row in set
```

### 9. Display the date three months Before the current date
```sql
SELECT DATE_SUB(CURDATE(), INTERVAL 3 MONTH) AS three_months_before;
```
**Output:**
```text
+---------------------+
| THREE_MONTHS_BEFORE |
+---------------------+
| 2025-11-26          |
+---------------------+
1 row in set
```

### 10. Display those employees who joined in the company in the month of Dec.
```sql
SELECT *
FROM employee
WHERE MONTH(hiredate) = 12;
```
**Output:**
```text
+-------+-------+---------+------+------------+------+------+--------+
| EMPNO | ENAME | JOB     | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+-------+---------+------+------------+------+------+--------+
| 7369  | SMITH | CLERK   | 7902 | 1980-12-17 | 800  | NULL | 20     |
| 7788  | SCOTT | ANALYST | 7566 | 1982-12-09 | 3000 | NULL | 40     |
| 7900  | JAMES | CLERK   | 7698 | 1981-12-03 | 950  | NULL | 30     |
| 7902  | FORD  | ANALYST | 7566 | 1981-12-03 | 3000 | NULL | 20     |
+-------+-------+---------+------+------------+------+------+--------+
4 rows in set
```

### 11. Display those employees whose first 2 characters from hire date -last 2 characters of salary.
```sql
SELECT *
FROM employee
WHERE LEFT(DATE_FORMAT(hiredate, '%d'), 2) = RIGHT(CAST(sal AS CHAR), 2);
```
**Output:**
```text
Empty set
```

### 12. Display those employees whose 10% of salary is equal to the year of joining.
```sql
SELECT *
FROM employee
WHERE sal * 0.10 = YEAR(hiredate);
```
**Output:**
```text
Empty set
```

### 13. Display those employees who joined the company before 15 of the months.
```sql
SELECT *
FROM employee
WHERE DAY(hiredate) < 15;
```
**Output:**
```text
+-------+--------+----------+------+------------+------+------+--------+
| EMPNO | ENAME  | JOB      | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+--------+----------+------+------------+------+------+--------+
| 7566  | JONES  | MANAGER  | 7839 | 1981-04-02 | 2975 | NULL | 20     |
| 7782  | CLARK  | MANAGER  | 7839 | 1981-06-09 | 2450 | NULL | 20     |
| 7788  | SCOTT  | ANALYST  | 7566 | 1982-12-09 | 3000 | NULL | 40     |
| 7844  | TURNER | SALESMAN | 7698 | 1981-09-08 | 1500 | 0    | 30     |
| 7876  | ADAMS  | CLERK    | 7788 | 1983-01-12 | 1100 | NULL | 20     |
| 7900  | JAMES  | CLERK    | 7698 | 1981-12-03 | 950  | NULL | 30     |
| 7902  | FORD   | ANALYST  | 7566 | 1981-12-03 | 3000 | NULL | 20     |
+-------+--------+----------+------+------------+------+------+--------+
7 rows in set
```

### 14. Display those employees who has joined before 15th of the month
```sql
SELECT *
FROM employee
WHERE DAY(hiredate) < 15;
```
**Output:**
```text
+-------+--------+----------+------+------------+------+------+--------+
| EMPNO | ENAME  | JOB      | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+--------+----------+------+------------+------+------+--------+
| 7566  | JONES  | MANAGER  | 7839 | 1981-04-02 | 2975 | NULL | 20     |
| 7782  | CLARK  | MANAGER  | 7839 | 1981-06-09 | 2450 | NULL | 20     |
| 7788  | SCOTT  | ANALYST  | 7566 | 1982-12-09 | 3000 | NULL | 40     |
| 7844  | TURNER | SALESMAN | 7698 | 1981-09-08 | 1500 | 0    | 30     |
| 7876  | ADAMS  | CLERK    | 7788 | 1983-01-12 | 1100 | NULL | 20     |
| 7900  | JAMES  | CLERK    | 7698 | 1981-12-03 | 950  | NULL | 30     |
| 7902  | FORD   | ANALYST  | 7566 | 1981-12-03 | 3000 | NULL | 20     |
+-------+--------+----------+------+------------+------+------+--------+
7 rows in set
```

### 15. Display those employees whose joining date is available in DEPTNO
```sql
SELECT *
FROM EMPLOYEE
WHERE HIREDATE IS NOT NULL
AND DEPTNO IS NOT NULL;
```
**Output:**
```text
+-------+--------+-----------+------+------------+------+------+--------+
| EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL  | COMM | DEPTNO |
+-------+--------+-----------+------+------------+------+------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |  968 | NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600 |  300 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250 |  300 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 3600 | NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250 | 1400 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 3449 | NULL |     30 |
|  7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2965 | NULL |     20 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1982-12-09 | 3630 | NULL |     40 |
|  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 6050 | NULL |     20 |
|  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1815 |    0 |     30 |
|  7876 | ADAMS  | CLERK     | 7788 | 1983-01-12 | 1331 | NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 | 1150 | NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3630 | NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 1982-01-23 | 1573 | NULL |     10 |
+-------+--------+-----------+------+------------+------+------+--------+
14 rows in set
```

---