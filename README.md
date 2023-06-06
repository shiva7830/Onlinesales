# Onlinesales
 
Task-1 SQL
In the attachment above, use each worksheet as a table in a relational database and write an SQL query that generates the output report


stepo 1:- first we need to create table 
  
CREATE TABLE asde (  ID INT(1), DEPT_NAME VARCHAR(25),   AVG_MONTHLY_SALARY FLOAT(25) );

step 2:- after creating table now we have to insert data inside TABLE asde 

	INSERT INTO asde (ID,DEPT_NAME, AVG_MONTHLY_SALARY) VALUES (1,'HR', 5000.00), (2,'Finance', 6000.00),  (3,'IT', 5500.00),(4,'ops',4000.0),(5,'sales',4575.0);
 
 step 3:- now we have to retrieve data according to given question 
 
	SELECT DEPT_NAME, AVG_MONTHLY_SALARY FROM asde 
    ORDER BY AVG_MONTHLY_SALARY DESC LIMIT 3 ;

Task-2 Scripting
With the same attachment, use each worksheet as a CSV file and write a script (Bash or Nodejs) that generates the same report. Data is to be read from the CSV files not from a database



step 1:- To generate the same report using data from CSV files in a Node.js script, you can utilize the csv-parser and fs modules.

step2:- 
const fs = require('fs');
const csv = require('csv-parser');

const filePaths = ['path/to/file1.csv', 'path/to/file2.csv', 'path/to/file3.csv']; // Replace with the actual file paths

const departments = [];

filePaths.forEach((filePath) => {
  fs.createReadStream(filePath)
    .pipe(csv())
    .on('data', (row) => {
      departments.push(row);
    })
    .on('end', () => {
      // Sort the departments by AVG_MONTHLY_SALARY in descending order
      departments.sort((a, b) => b.AVG_MONTHLY_SALARY - a.AVG_MONTHLY_SALARY);

      // Generate the report
      console.log('DEPT_NAME    AVG_MONTHLY_SALARY (USD)');
      console.log('-------------------------------------');
      departments.slice(0, 3).forEach((dept) => {
        console.log(`${dept.NAME}\t\t${dept.AVG_MONTHLY_SALARY}`);
      });
    });
});

step 3:- Make sure to replace 'path/to/file1.csv', 'path/to/file2.csv', etc., with the actual file paths of your CSV files.

step 4:- This script reads each CSV file, parses the data, and stores it in the departments array. Then, it sorts the departments based on the AVG_MONTHLY_SALARY column in descending order. Finally, it generates the report by printing the top 3 departments along with their names and average monthly salaries.

You'll need to install the required packages by running npm install csv-parser fs before executing the script.

Note: Ensure that the CSV files follow the same structure, with columns named ID, NAME, and AVG_MONTHLY_SALARY matching the script's field names.

Task 3:- Debugging
Given below is a Bash / Python script that performs following computation on an integer input (n):
   1.If n is less than 10: Calculate its Square
     Example: 4 => 16
   2. If n is between 10 and 20: Calculate the factorial of (n-10)
     Example: 15 => 120
   3.If n is greater than 20: Calculate the sum of all integers between 1 and (n-20)
     Example: 25 => 15

The task is to identify the bugs in the script, fix them and share the new script. Only one of the two scripts required Bash or Python. Hint: You can correct the script by only changing 3-4 characters.

sol:-

Script (Bash):

#!/bin/bash
N=$1
if [ $N -lt 10 ]
then
OUT=$((N*N))
elif [ $N -lt 20 ]
then
OUT=1
LIM=$((N - 10))
for (( i=1; i<=$LIM; i++ ))
do
OUT=$((OUT * i))
done
else
LIM=$((N - 20))
SUM=0
for (( i=1; i<=$LIM; i++ ))
do
SUM=$((SUM + i))
done
OUT=$SUM
fi
echo $OUT

Script (Python):

def compute(n):
if n < 10:
out = n ** 2
elif n < 20:
out = 1
for i in range(1, n-10+1):
out *= i
else:
lim = n - 20
out = sum(range(1, lim+1))
print(out)

n = int(input("Enter an integer: "))
compute(n)

Explanation:

In the Bash script, the condition for the second if statement should be changed from for (( i=1; i<$LIM; i++ )) to for (( i=1; i<=$LIM; i++ )). This ensures that the loop runs for the correct number of iterations.

In the Bash script, when N is greater than 20, the computation of the sum of integers should be fixed. The variable SUM should be initialized to 0, and the loop should iterate from 1 to $LIM (not $N) using for (( i=1; i<=$LIM; i++ )). Additionally, the output variable should be set to OUT=$SUM.

In the Python script, the loop condition in the second elif statement should be changed from for i in range(1, n-10) to for i in range(1, n-10+1). This ensures that the loop runs for the correct number of iterations.

In the Python script, when n is greater than 20, the computation of the sum of integers can be simplified using the sum() function. The variable lim should be used to define the range in the sum() function: out = sum(range(1, lim+1)).

These modifications address the bugs in the provided scripts.
