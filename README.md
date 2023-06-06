# Onlinesales
 
Task-1 SQL
In the attachment above, use each worksheet as a table in a relational database and write an SQL query that generates the output report


stepo 1:- first we need to create table 
  
CREATE TABLE asde (  ID INT(1), DEPT_NAME VARCHAR(25),   AVG_MONTHLY_SALARY FLOAT(25) );

step 2:- after creating table now we have to insert data inside TABLE asde 

	INSERT INTO asde (ID,DEPT_NAME, AVG_MONTHLY_SALARY) VALUES (1,'HR', 5000.00), (2,'Finance', 6000.00),  (3,'IT', 5500.00),(4,'ops',4000.0),(5,'sales',4575.0);
 
 step 3:- now we have to retrieve data according to given question 
 
	SELECT DEPT_NAME, AVG_MONTHLY_SALARY FROM asde 
    ORDER BY AVG_MONTHLY_SALARY DESC LIMIT 3	;


