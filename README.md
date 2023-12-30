# Filter-with-AND-OR-and-NOT-in-SQL

<h2>Activity overview</h2>

As a security analyst, I’ll likely need to analyze data. And often finding the specific data I’ll need depends on more than one factor.

To retrieve specific pieces of information from the database, I can filter for multiple conditions. I can also filter for what does not match a particular condition.

In this lab activity, I’ll use the ```AND```, ```OR```, and ```NOT``` operators to create more complex filters for SQL queries.

<h2>Scenario</h2>

In this scenario, I need to obtain specific information about employees, their machines, and the departments they belong to from the database.

My team needs data to investigate potential security issues and to update computers.

I am responsible for filtering the required information from the database.

Here’s how I’ll do this task: First, I’ll retrieve all failed login attempts after business hours. Second, I’ll retrieve all login attempts that occurred on specific dates. Third, I’ll retrieve logins that didn't originate in Mexico. Fourth, I’ll retrieve information about certain employees in the Marketing department. Fifth, I’ll retrieve information about employees in the Finance or the Sales department. Finally, I’ll obtain information about employees who are not in the Information Technology department.

<h2>Task 1. Retrieve after hours failed login attempts</h2>

My team is investigating failed login attempts that were made after business hours. I want to retrieve this information from the login activity. I’ll identify all unsuccessful attempts after 18:00.

The ```login_time``` column in the ```log_in_attempts``` table contains information on when login attempts were made. Office hours end at '18:00'.

The ```success``` column in the ```log_in_attempts``` table contains values of ```TRUE``` or ```FALSE``` to indicate whether the login was successful. MySQL stores Boolean values as 1 for TRUE, and 0 for FALSE. This means that TRUE is represented as 1, and FALSE is represented as 0 in the success column.

- Use the ```AND``` operator to retrieve the failed login attempts that occurred after business hours. Replace the X and Y with the correct values to filter for the records I need:

```SELECT *```

```FROM log_in_attempts```

```WHERE login_time > '18:00' AND success = 0;```

Note: Values of TRUE and FALSE are not placed in single quotes because they are not string data. They are Boolean data, which is another data type.

There were 19 failed login attempts after 18:00:

![image](https://github.com/n8som/Filter-with-AND-OR-and-NOT-in-SQL/assets/110139109/f4fcf5ed-8435-425a-ae93-179c0ec9b67b)

<h2>Task 2. Retrieve login attempts on specific dates</h2>

My team is investigating a suspicious event that occurred on '2022-05-09'. I want to retrieve all login attempts that occurred on this day and the day before ('2022-05-08').

The ```login_date``` column in the ```log_in_attempts``` table contains information on the dates when login attempts were made.

- Use the ```OR``` operator to retrieve the failed login attempts on the specified days. Replace the X and Y with the correct values to filter for the records I need:

```SELECT *```
 
```FROM log_in_attempts```

```WHERE login_date = '2022-05-09' OR login_date = '2022-05-08';```

There were 75 login attempts made on these two days:

![image](https://github.com/n8som/Filter-with-AND-OR-and-NOT-in-SQL/assets/110139109/3aa78174-a25f-4cd0-bc26-09002eec39ba)

<h2>Task 3. Retrieve login attempts outside of Mexico</h2>

Now, my team is investigating logins that did not originate in Mexico, and I need to find this information. Note that the country field includes entries with 'MEX' and 'MEXICO'. I should use the ```NOT``` and ```LIKE``` operators and the matching pattern ```'MEX%'```.

- Run the following SQL query to retrieve login attempts that did not originate in Mexico. Replace X with the correct operator and Y with the correct pattern to filter for the information I need:

```SELECT *```
 
```FROM log_in_attempts```

```WHERE NOT country LIKE 'MEX%';```

There were 144 login attempts made outside of Mexico:

![image](https://github.com/n8som/Filter-with-AND-OR-and-NOT-in-SQL/assets/110139109/401c6c69-3dc4-4d91-a54d-fcac7d41a538)

<h2>Task 4. Retrieve employees in Marketing</h2>

For tasks 4, 5, and 6 I need to retrieve the information from the department and office columns in the employees table.

I can run the following SQL query if I need to view the columns and values in the employees table:

```SELECT *```
 
```FROM employees;```

My team is updating employee machines, and I need to obtain information about employees in the 'Marketing' department who are located in all offices in the East building (such as 'East-170' or 'East-320').

- Write a SQL query to retrieve this information from the employees table. Select all columns and include filters on the department and office columns to return only the needed records.

Note: I’ll need to use the AND and LIKE operators to satisfy both of these criteria.

```SELECT *```

```FROM employees```

```WHERE department = 'Marketing' AND office LIKE 'East%';```

elarson is the username of the first employee in the Marketing department in the East building:

![image](https://github.com/n8som/Filter-with-AND-OR-and-NOT-in-SQL/assets/110139109/c1545627-b4d7-49ac-af55-d3853e0b3a07)

<h2>Task 5. Retrieve employees in Finance or Sales</h2>

Now, my team needs to perform a different update to the computers of all employees in the Finance or the Sales department, and I need to locate information on these employees.

- Write a SQL query to retrieve records for employees in the 'Finance' or the 'Sales' department.

Note: Even though both conditions are based on the same column, I need to write out both full conditions. This means that I must specify the department as the column in both conditions.

```SELECT *```

```FROM employees```

```WHERE department = 'Sales' OR 'Finance';```

lrodriqu is the username of the first employee in the Sales department returned by the query:

![image](https://github.com/n8som/Filter-with-AND-OR-and-NOT-in-SQL/assets/110139109/fdb33f1f-1b3b-4e56-b45b-b5484c38cd7d)

<h2>Task 6. Retrieve all employees not in IT</h2>

My team needs to make one more update. This update was already made to employee computers in the Information Technology department. The team needs information about employees who are not in that department. I should use the NOT operator to identify these employees.

- Write a SQL query to retrieve records for employees who are not in the 'Information Technology' department.

```SELECT *```

```FROM employees```

```WHERE NOT department = 'Information Technology';```

There are 161 employees NOT in the IT department:

![image](https://github.com/n8som/Filter-with-AND-OR-and-NOT-in-SQL/assets/110139109/f137c1be-c738-47a1-a617-ec2113ba99c7)

<h2>Conclusion</h2>

I now have practical experience in using SQL to

- run SQL queries to retrieve information from a database and
- apply ```AND```, ```OR```, and ```NOT``` operators to filter SQL queries.

I’m well on my way to running complex SQL queries to get specific data from a database.

