# Module-7
Employee Database with SQL

## Overview of the analysis 
The purpose of this analysis is to determine a strategy for the retiring employees from the Pewlett Hackard company, for this purpose, we identified the retiring employees and who might be eligible for a mentorship program to fulfill those positions. 

## Results 
* We have 33,118 current employees in retirement process 
* We have 1,549 employees that are suitable for te mentorship program
* | Department   | Employees retiring |
  | ---      | ---      
  |Marketing	|2,199|
  |Finance|	1,908|
  |Human Resources|	1,953|	
  |Production	| 8,174|	
  |Development|	9,281|	
  |Quality Managment|2,234|	
  |Sales|	5,860|	
  |Research|	2,413|	
  |Customer Service|	2,597|	

* There's an important effort to be made in order to fulfill all the positions that will be available

  	
## Summary 
How many roles will need to be filled as the "silver tsunami" begins to make an impact? 33,118

Are there enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett Hackard employees? 

That's hard to say, we would need to understand from which departments we have employees suitable for training the next generation, for example, Production may have a lot of employees that are retiring, maybe not all the positions require a lot of training, we would need to understand how many employees can a mentor train and in what time, there are a lot of open questions still 

Two more tables that could help to understand better the strategy would be the eligible for mentorship program by department & the time it takes to train for each position and the number of employees that can be trained at the same time. That would actually define the approach the company would have. 

```
SELECT DISTINCT ON (e.emp_no)
        e.emp_no,
        e.first_name,
        e.last_name,
        e.birth_date,
        de.from_date,
        de.to_date,
		de.dept_no,
        ti.title
INTO mentorship_eligibilty_by_dept
FROM employees AS e
INNER JOIN dept_emp AS de
ON (e.emp_no = de.emp_no)
INNER JOIN titles AS ti
ON (e.emp_no = ti.emp_no)
WHERE (de.to_date = '9999-01-01')
AND (e.birth_date BETWEEN '1965-01-01' AND '1965-12-31')
ORDER BY e.emp_no

SELECT COUNT(emp_no), dept_no
FROM mentorship_eligibilty_by_dept
GROUP BY dept_no
ORDER BY dept_no;
```
