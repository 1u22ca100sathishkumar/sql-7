# sql-7
1. Single-Row Subquery

A single-row subquery returns only one value.

Example
SELECT *
FROM Employees
WHERE Salary >
      (SELECT Salary
       FROM Employees
       WHERE Employee_ID = 101);


Explanation:
The subquery returns the salary of employee 101 (one value).
The main query displays employees whose salary is greater than that value.

2. Multi-Row Subquery

A multi-row subquery returns more than one row.
Operators like IN, ANY, ALL are used.

Example
SELECT *
FROM Employees
WHERE Department_ID IN
      (SELECT Department_ID
       FROM Departments
       WHERE Location = 'Chennai');


Explanation:
The subquery returns multiple department IDs located in Chennai.
The main query fetches employees working in those departments.

3. Correlated Subquery

A correlated subquery depends on the outer query and is executed once for each row.

Example
SELECT *
FROM Employees e
WHERE Salary >
      (SELECT AVG(Salary)
       FROM Employees
       WHERE Department_ID = e.Department_ID);


Explanation:
For each employee, the subquery calculates the average salary of that employee’s department and compares it with the employee’s salary.

Summary Table
Subquery Type	Rows Returned	Common Operators
Single Row	One row	=, >, <
Multi Row	Multiple rows	IN, ANY, ALL
Correlated	Row by row	Uses outer query reference
