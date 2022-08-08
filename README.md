# Pewlett-Hackard-Analysis

## Overview of the analysis

Purpose of the analysis is to determine the number of retiring employees per title, and identify employees who are eligible to participate in a mentorship program and create a report that summarizes analysis and help prepare Bobby’s manager for the “silver tsunami” as many current employees reach retirement age.


## Results

Summary of the Pewlett-Hackard is as show below: 

1. Looking at "Retirement Titles" table, there are total 90,398 emplooyees who are eligible to retire out of 300,024 total employees. That's a large number of employees who can retire.  
2. Looking at "Unique titles" table, out of 90,398 total employees 72,458 employees are currently employed by Pewlett-Hackard. 
3. Looking at the "Retiring Titles" table, we can see below titles are most eligible to retire. They are more senior or staff level engineers. Bobby's manager has to be ready to start hiring for those titles. 

| Count | Title |
|----------|----------|
|25916	|"Senior Engineer" |
|24926	|"Senior Staff" |
|9285	| "Engineer" |
|7636	| "Staff" |
|3603	| "Technique Leader" |
|1090	| "Assistant Engineer" |
|2	| "Manager" |

4. On a more concerning side, there are only 1,549 employees who are eligible for mentorship & they have experience to mentor new hires if they have to hire them. 

## Summary
1. How many roles will need to be filled as the "silver tsunami" begins to make an impact?
There are total 72,458 roles which needs to be filled in 7 titles which is huge number. 

2. Are there enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett Hackard employees?
There are total 1,549 employees who are ready to mentor and have experience and time to do that which is not a very huge number but still not bad. 

Below are the titles which are there that can be help to mentor & most of them are Senior staff engineers.  
```select COUNT(emp_no), title from mentorship_eligibilty
group by title 
order by COUNT(emp_no) desc;
```
| Count | Title |
|----------|----------|
|432	|"Senior Staff" |
|409	|"Engineer" |
|292	| "Staff" |
|275	| "Senior Engineer" |
|77	| "Technique Leader" |
|64	| "Assistant Engineer" |


Below are the departments which will be most impacted by this "silver Tsunami". Development, Production & Sales departments should be highly prepared for it and start hiring. 
```
select count(distinct u.emp_no), d.dept_name
from unique_titles as u
inner join dept_emp as de 
on u.emp_no = de.emp_no
inner join departments as d
on de.dept_no = d.dept_no
group by d.dept_name
order by count(distinct u.emp_no) desc
```
| Count |Department |
|----------|----------|
|20451	|"Development" |
|17784	|"Production" |
|12649	|"Sales" |
|5778	|"Customer Service" |
|5216	|"Research" |
|4865	|"Quality Management" |
|4816	|"Marketing" |
|4351	|"Human Resources" |
|4199	|"Finance" |
