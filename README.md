# Pewlett-Hackard-Analysis

#Overview 
Pewlett-Hackard is a company with a high number of senior employees that are coming up on retirement. To ensure that as these senior employees transition out of the company, there is no large gaps in knowledge that could negativley impact work flow the company rquested that we analyze the expertise of the emplyees retiring. This will allow Pewlett-Hackard to implement a mentorship program to ensure that the senior emplyees are able to hand off their knowledge and expertice to junior employees. 

##Results
-There are 300024 employees at Pewlett-Hackard 
-There are 90398 that will soon be reaching retirement age.
-A majority of these retiring employees are senior engineers 
-The minority of these retiring emplyees are managers 

Pewlett-Hackard should prioritize the training/mentorship of engineers due to the high volume of personel they will be losing in the engineering deparment. The mentorship program in the management department likely isn't necessary due to the low number of retiring employees.

###Summary 
About 3% of Pewlett-Hackard's workforce is coming due for retirment. That doesn't sound concerning but once you group by job titles and realize that ~25% of those emplyees are engineers it becomes clear that Pewlett-Hackard is in danger of "brain drain" where their highly skilled employees that keep their systems running may soon be gone. This can be corrected by implementing a mentorship program where these more experienced individuals can pass down their skills to more junior employees to ensure that there are no large gaps in knowledge after this group of retirees are gone. 

There are 209626 employees at Pewlet-Hackard that are not of retirement age. About 90988 of these emplyees are in the engineering department. So it does appear that there are enough non-retiring engineering employees to fill the shoes of the 23340 senior engineers retiring. This can be found using the query below:
--Find non-retirement age emplyees 
SELECT * 
INTO non_retirement_age_emp
FROM employees 
WHERE birth_date > '1955-12-31'

SELECT n.emp_no,
t.title
INTO non_retiring_groups
FROM non_retirement_age_emp as n
INNER JOIN titles as t 
ON n.emp_no = t.emp_no

SELECT COUNT(emp_no), title
FROM non_retiring_groups
GROUP BY title;

Count Title 
10544	"Assistant Engineer"
80444	"Engineer"
18	"Manager"
68335	"Senior Engineer"
64597	"Senior Staff"
74939	"Staff"
10655	"Technique Leader"

