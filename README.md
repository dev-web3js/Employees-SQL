# Employees-SQL
CREATE TABLE emp (
    EMPNO INT PRIMARY KEY,
    ENAME VARCHAR(20),
    JOB VARCHAR(20),
    MGR INT,
    HIREDATE DATE,
    SAL DECIMAL(7, 2),
    COMM DECIMAL(7, 2),
    DEPTNO INT
);

INSERT INTO emp (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO) VALUES
(7369, 'SMITH', 'CLERK', 7902, '1980-12-17', 800, null, 20),
(7499, 'ALLEN', 'SALESMAN', 7698, '1981-02-20', 1600, 300, 30),
(7521, 'WARD', 'SALESMAN', 7698, '1981-02-22', 1250, 500, 30),
(7566, 'JONES', 'MANAGER', 7839, '1981-04-02', 2975, null, 20),
(7654, 'MARTIN', 'SALESMAN', 7698, '1981-09-28', 1250, 1400, 30),
(7698, 'BLAKE', 'MANAGER', 7839, '1981-05-01', 2850, null, 30),
(7782, 'CLARK', 'MANAGER', 7839, '1981-06-09', 2450, null, 10),
(7788, 'SCOTT', 'ANALYST', 7566, '1981-11-17', null, 2000, 20),
(7596, 'ADAMS', 'CLERK', 7698, '1981-05-19', 1100, null, 30, 10),
(7752, 'JAMES', 'CLERK', 7698, '1981-05-23', 950, null, 30, 11),
(7436, 'FORD', 'ANALYST', 7566, '1981-12-03', null, 3000, 20, 12),
(7616, 'MILLER', 'CLERK', 7788, '1982-01-23', 1300, null, 30, 13),
(7725, 'JONES', 'SALESMAN', 7698, '1982-02-03', 1000, 500, 30, 14);


CREATE TABLE dept (
 DEPTNO INT PRIMARY KEY,
 DNAME VARCHAR(20),
 LOC VARCHAR(20)
 
 SELECT e.ename, d.dname, e.salary
FROM emp e
JOIN dept d ON e.deptno = d.deptno
WHERE e.salary > 1000 AND e.salary < 2000;
);

INSERT INTO dept (DEPTNO, DNAME, LOC) VALUES
(10, 'ACCOUNTING', 'NEW YORK'),
(20, 'RESEARCH', 'DALLAS'),
(30, 'SALES', 'CHICAGO'),
(40, 'OPERATIONS', 'BOSTON');

SELECT e.ename, d.dname, e.salary
FROM emp e
JOIN dept d ON e.deptno = d.deptno
WHERE e.salary > 1000 AND e.salary < 2000;

SELECT COUNT(*)
FROM EMP
WHERE DEPTNO = 30 AND SAL IS NOT NULL AND COMM IS NOT NULL;

SELECT e.ename, e.salary
FROM emp e
WHERE e.salary >= 1000 AND e.city = 'DALLAS';

SELECT d.deptno
FROM dept d
LEFT JOIN emp e ON d.deptno = e.deptno
WHERE e.deptno IS NULL;

SELECT d.deptno, AVG(e.salary) as average_salary, COUNT(e.empno) as employee_count
FROM dept d
JOIN emp e ON d.deptno = e.deptno
GROUP BY d.deptno;
