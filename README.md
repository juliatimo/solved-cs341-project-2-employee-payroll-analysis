Download Link: https://assignmentchef.com/product/solved-cs341-project-2-employee-payroll-analysis
<br>
Part of running a business is keeping track of the books, having a record of sales, costs, profits, employees and goods.  This data can be stored in a variety of formats, one of which is the humble csv file.  Having the data stored is important to keep track of the assets of the company, but has additional use beyond just record keeping.  The field of data analysis has widespread popularity in the world today, and can be accomplished in a variety of methods.

This analysis generally does not involve changing the initial data, and so a language without side effects and with a mathematical basis will enable us to cleanly produce an analysis and be confident in the correctness of the produced results.




The various departments employed by the City of Chicago have their payrolls part of the public record.  This data is available as part of Chicago’s open data <a href="https://data.cityofchicago.org/Administration-Finance/Current-Employee-Names-Salaries-and-Position-Title/xzkq-xp2w">portal</a><a href="https://data.cityofchicago.org/Administration-Finance/Current-Employee-Names-Salaries-and-Position-Title/xzkq-xp2w">.</a>




The goal in this assignment is to input the payroll information for a number of employees and perform some analysis of the data:  # of employees, the % of salaried and hourly workers, the average salary, and each of these statistics filtered by condition such as by department, etc.  Here’s a screenshot of the program analyzing the <strong>payroll_01.csv </strong>data file




What follows is a list of functions and descriptions of their behavior you may find useful in producing an analysis of this data.







<ol>

 <li><strong>isSalary employee, isHourly employee, getSalary employee and getDeparment employee: </strong></li>

</ol>

The functions isSalary, isHourly , getSalary and getDepartment access specific fields of the employee tuple and return either a boolean (in the case of the is functions) or a value (in the case of the get functions).




<ol start="2">

 <li><strong>calcSalary employee: </strong></li>

</ol>

The function calcSalary calculates the annual salary, either by returning the directly recorded annual salary or calculating it by finding the average weekly salary by multiplying the hours per week by hourly wage, and then multiplying that by 52 to get the average annual salary for that hourly worker.




<ol start="3">

 <li><strong>getNumberOfEmployees AllData </strong></li>

</ol>

The function getNumberOfEmployees returns the number of employees in the data set.




<h2>4. getNumberOfSalariedEmployees AllData</h2>

The function getNumberOfSalariedEmployees returns the number of employees who have an annual salary in the data set.




<h2>5. getNumberOfHourlyEmployees AllData</h2>

The function getNumberOfSalariedEmployees returns the number of employees who are paid hourly in the data set.




<h2>6. findHighestPaidEmployee AllData</h2>

The function findHighestPaidEmployee returns the name and salary of the highest paid employee.  Use the computed salary for hourly employees.




<h2>7. findHighestPaidEmployeeInDept AllData DeptName</h2>

The function findHighestPaidEmployee returns the salary of the highest paid employee within a specific department.  Use the computed salary for hourly employees.




<ol start="8">

 <li><strong> getAverageSalary AllData </strong></li>

</ol>

The function getAverageSalary calculates the average of the computed salary field.




<h2>9. getAverageSalaryInDept AllData DeptName</h2>

The function getAverageSalary calculates the average of the computed salary field for a specific department.




The function getUniqueDepartmentNames has been provided for you, searching through the data set to generate a list of department names.




<h2>10. howManyEmployeesInEachDepartment AllData DeptNames</h2>

This function computes the number of employees in every department.  This function should return a list of tuples, pairs between the department name and number of employees.




<h2>11. findTotalSalaryByDepartment AllData DeptNames</h2>

This function computes the overall annual salary budget for every department.

The calculated salary should include the average annual salary for hourly employees.

This function should return a list of tuples, pairs between the department name and total annual salary.




<h2>12. findHighestPaidDept AllData DeptNames</h2>

This function returns the name and total annual salary of the department with the largest overall annual salary paid to employees in that department.

The calculated salary should include the average annual salary for hourly employees.

This function should return a single tuple, containing the department name and total annual salary.













<h2>13. printOneHistogram label value amountPerStar</h2>

The function printOneHistogram implements generating a histogram of number of items in a particular group, printing out a number of stars equal to value/amountPerStar after a right shifted standard length label field to line up the graph.




<h2>14. withinSalaryRange lower upper L</h2>

The function withinSalaryRange returns the number of employees whose calculated salary is greater than the lower bound and less than or equal to the upper bound.




The function printOneHistogram is used to generate two histograms.

In one, a histogram used to output the number of employees in each department

The department names form the labels and the number of employees determine the number of stars.




In the second, employees are grouped by salary range.

The range description forms the label, and the number of employees with a salary in that range determines the number of stars.




The salary ranges used in the output of this program are

0            &lt; salary &lt;= 60000

60000   &lt; salary &lt;= 80000

80000   &lt; salary &lt;= 100000      100000 &lt; salary &lt;= 120000      salary &gt; = 120000




The program starts by inputting the filename, and a specific department name to analyze.

The program proceeds to output statistics analyzed from the data set, using the functions listed above.  A skeleton F# program is provided with the code to open the data file and input the data.  Your job is to add the analysis.




You can solve recursively, or using a higher-order approach (I’d recommend using higher order functions where possible).  You cannot use loops, no mutable variables.  You should add additional functions as you see fit and may use a different data format in your program if you wish, though you should still only be using lists and tuples.

<h2>File format</h2>

The input file consists of at most 10,000 employees.  The files are not large, which allows the use of recursion without the risk of stack overflow.  The file is in CSV format (“comma-separated values”), and each line of the file represents one employee.  Here’s an example:




JORDAN M,HARTFIELD,POLICE OFFICER,POLICE,Salary,,76266,

JOHN R,KEATING,FOREMAN OF ELECTRICAL MECHANICS,GENERAL

SERVICES,Hourly,40,,52.35

CHRISTOPHER H,MAROSI,SENIOR PERFORMANCE ANALYST,POLICE,Salary,,72120, …




Each line contains exactly 8 values, in this order:




<ul>

 <li>First Name:                 string, First Name of employee, often includes middle initial</li>

 <li>Last Name:                 string, Last Name of employee</li>

 <li>Occupation:                 string, title of position held</li>

 <li>Department:                 string, name of the department employing this person</li>

 <li>Wage Type:                 string, Salary or Hourly</li>

 <li>Hours Per Week: integer, Number of hours worked on average, generally 20 or 40, not applicable to</li>

</ul>

salaried workers

<ul>

 <li>Salary:                 integer, Annual Salary, not applicable to hourly workers</li>

 <li>Hourly Wage:                 double, wage per hour, only applicable to hourly workers, not applicable to salaried</li>

</ul>




For testing purposes we are providing two input files:  “<strong>payroll_01.csv</strong>” and “<strong>payroll_02.csv</strong>”.  The first is small so you can inspect the results and compare them with your computations by hand.  The second is somewhat larger so you can test whether your solution scales.  These files are in the box folder under Projects/Project 02.







<h2>Getting Started</h2>

To help you get started, we are providing an F# console program that opens the input file, parses the CSV data, and builds a list of lists.  This code is provided (along with sample input files) in the Box page under Projects/Project 02.  Here’s the main program as given:




//

// F# program to analyze employee salary data.

//

// &lt;&lt; YOUR NAME HERE &gt;&gt;

// U. of Illinois, Chicago

// CS 341, Spring 2020 // Project #02

//  module project02




//

// doubleOrNothing

//

// Given a string containing a double numeric value

// or being an empty string

// returns the double equivalent, with the empty string

// treated as the value 0.0

//

let doubleOrNothing s =      match s with

| “” -&gt; 0.0

| x -&gt; double x




//

// ParseCSVLine and ParseCSVDatabase

//

// Given a sequence of strings representing payroll data,

// parses the strings and returns a list of tuples.  Each // sub-list denotes one employee.  Example:

//

//[ (“JESSE A”, “ACOSTA”, “POLICE OFFICER”, “POLICE”, “Salary”, 0.0, 93354.0, 0.0); … ] //

// The values are first name, last name, occupation,

// department, salary type, hours per week, annual salary,

// and hourly wage.

// Depending on the salary type,

// either hours per week and hourly wage

// or annual salary will be filled in with 0.0,

// since the field is empty in the csv

//

let ParseCSVLine (line:string) =      let tokens = line.Split(‘,’)     let listOfValues = Array.toList tokens

let fName::lName::Occupation::Department::SalaryType

::HoursPerWeek::AnnualSalary::HourlyWage::[] = listOfValues

(fName,lName,Occupation,Department,SalaryType,       (doubleOrNothing HoursPerWeek),

(doubleOrNothing AnnualSalary),

(doubleOrNothing HourlyWage)

)  let rec ParseCSVDatabase lines =

let employees = Seq.map ParseCSVLine lines

Seq.toList employees




[&lt;EntryPoint&gt;] let main argv =

//

// input file name, then input divvy ride data and build   // a list of lists:

//   printf “Enter name of the csv file containing employee data: ”

let filename = System.Console.ReadLine()   let contents = System.IO.File.ReadLines(filename)   let data = ParseCSVDatabase contents




printfn “This is the data you have loaded.”   List.iter (printfn “%A”) data




0




Notice that the <strong>main</strong> function inputs the filename, then opens the file and inputs the data.  Each line of the file

— one employee — is turned into a list of 8 items as described earlier.  The resulting data structure is a list of tuples.  I have included an output so you can see the format of the input after parsing.  Here’s what you’ll see working with the smaller input file <strong>payroll_01.csv</strong> (at least this is the start of the output you’ll see):













You are free to use whatever F# programming environment you prefer; submissions will be collected using Gradescope.   Then you’ll probably need to place the input files — payroll_01.csv and payroll_02.csv — where .NET is looking for them.  This may be in the sub-folder <strong>bin/Debug </strong>and possibly a folder deeper such as<strong> /netcoreapp2.2</strong> (note that the digits might be 2.1 or 2.0 or 1.1 depending on what version of .NET core you have installed).  Also, depending on your operating system, you may need to change the line endings of the file from Windows to Mac or Linux.




<h1>Requirements</h1>

No imperative programming.  In particular, this means no mutable variables, no loops, and no data structures other than F# lists and tuples.  We haven’t talked about classes, feel free to experiment with them after the project is done but limit yourself to lists and tuples to practice for the exam.  Use recursion and higher-order approaches only.

<h1>A few F# hints / gotchas…</h1>

When computing the average or percentage, you’ll need to convert your integer values to real numbers.

Use the <strong>double</strong> function:  (double integer_value).  When a percentage is output, the output contains “%”.  Since % is a special formatting character of the printf and printfn functions, you need to escape “%” in order to output this character:  to escape, simply put two in a row, i.e. printf “%%”.  Need to print a blank line?  Use printfn “”.




When outputting the *’s for the histogram, it’s a little tricky to do recursively because the printf function doesn’t return a value — it’s a void function.  Here’s a recursive function that prints n *’s:




let rec printstars n =

match n with

| 0 -&gt; ()

| 1 -&gt; printf “*”   | _ -&gt; printf “*”          printstars (n-1)




The return value ( ) for the base case of 0 denotes no return value, i.e. void (“unit” in F#).





