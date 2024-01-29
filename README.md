# EXPLORING EMPLOYEE DATASET 

##STRING PATTERNS,SORTING AND GROUPING
```sql
USE HR;
---Retreive all employees whose address is in Elgin,IL
SELECT f_name,l_name
FROM Employees
WHERE address LIKE '%Elgin,IL%';

---Retreive all employees who were born during the 1970's
SELECT f_name,
       l_name
FROM employees
WHERE b_date LIKE '%197%';

---Retrieve all employees in department 5 whose salary is between 60000 and 70000;
SELECT f_name,
       l_name
FROM Employees
WHERE dep_id = 5
AND salary BETWEEN 60000 AND 70000;

---Retrieve a list of employees ordered by departmentID. 
SELECT dep_id,
       f_name,
	   l_name
FROM employees
ORDER BY dep_id;

/*Retrive alist of employees ordered in descending order by departmentID 
and within each department ordered alphabetically in descending order by last name*/
SELECT dep_id,
       f_name,
	   l_name
FROM Employees
ORDER BY dep_id DESC, l_name DESC;

---For each department ID retrieve the number of employees in the department. 
SELECT dep_id,
	   COUNT(*)AS employee_count
FROM employees
GROUP BY dep_id;

---For each department retrieve the number of employees in the department, and the average employee salary in the department
SELECT dep_id,
       COUNT(*) AS emp_count,
	   AVG(salary) AS avg_salary
FROM Employees
GROUP BY dep_id;

---Order the above result set by Average Salary
SELECT dep_id,
       COUNT(*) AS emp_count,
	   AVG(salary) AS avg_salary
FROM Employees
GROUP BY dep_id
ORDER BY avg_salary;

---Limit the result to departments with fewer than 4 employees
SELECT dep_id,
       COUNT(*) AS emp_count,
	   AVG(salary) AS avg_salary
FROM Employees
GROUP BY dep_id
HAVING COUNT(*) < 4
ORDER BY avg_salary;

        
```
