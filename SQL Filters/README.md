# Apply filters to SQL queries

## Project description

This activity provided by Google in its cybersecurity course lets me showcase my knowledge of SQL, through the activity I am handling some security tasks inside a company using SQL.

## Retrieve after hours failed login attempts

To get the login attempts that occurred after 6 pm, the time when working hours finish for this company, I will use a query that gets all the columns in the login attempts table by using `SELECT *` with a filter, this filter will get those login attempts that have a login time greater than 18:00, it can be done enabling filtering by using the word `WHERE` and using the specific filter greater than `>`. The issue also requires filtering those login attempts that failed, I will be appending an extra filter using the `AND` operator, and that code will read as follows:

    SELECT * 
    FROM log_in_attempts
    WHERE login_time > '18:00' AND SUCCESS = 0;


## Retrieve login attempts on specific dates
 
An incident happened on 2022-05-09, I will be checking all login attempts that occurred that day and the one before, to look into those specific days I can use the `OR` operator and include both days:

    SELECT * 
    FROM log_in_attempts
    WHERE login_date = '2022-05-08' OR login_date = '2022-05-09';

## Retrieve login attempts outside of Mexico

This time a new incident occurred and it is known it happened outside of Mexico, to include only events outside of Mexico, we must exclude it from our search, I will do it by using the `NOT` operator, also the database saves Mexico with no specific notation, it could be "MEX" or the whole name "MEXICO" and also other options, to make sure we include all options, we can use the `LIKE` operator that will let us some flexibility when searching by looking for similar patterns, in this case, we will look for any country name that starts with "MEX" this will be done by adding `%` after `MEX`, with all this added the code will look like this:

    SELECT * 
    FROM log_in_attempts
    WHERE country LIKE "MEX%";

## Retrieve employees in Marketing

We need to retrieve the information of users in the Marketing department to update their machines, we will be using the same command as the previous point, but we will be looking in the `department` column of the employee's table, we will also need to locate this machines only for the East building, we will include that in our search with the `LIKE` operator as did before so it give us a more specified location:

    SELECT * 
    FROM employees
    WHERE department = "Marketing" AND office LIKE "East%";

## Retrieve employees in Finance or Sales

Later we will also need an update for machines in the Sales and the Finance departments, to include both departments in our search we will use the `OR` operator like this: 

    SELECT * 
    FROM employees
    WHERE department = "Sales" OR department = "Finance";

## Retrieve all employees not in IT

This time there is a different update that was only made on machines from the IT department and we will exclude it from our search, this will be done with the `NOT` operator as follows:

    SELECT * 
    FROM employees
    WHERE NOT department = "IT";

## Summary

I have just shown how I would resolve some specific tasks using SQL, I have also shown different filters and operators to refine any search activity performed with SQL.

These examples clearly show I know the structure of a query in SQL, how to filter my queries with the `WHERE` operators and how to refine these filters with different options such as logical operators like `AND`, `NOT` and `OR`.

Besides logical operators, I've shown knowledge about mathematical operators used across different programming languages like `=`, `<`, `>` and others.