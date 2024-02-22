# Apply filters to SQL queries

## Project description

[Describe what you accomplish through SQL.]

## Retrieve after hours failed login attempts

To get the login attempts that occurred after 6 pm, the time when working hours finish for this company, I will use a query that gets all the columns in the login attempts table by using `SELECT *` with a filter, this filter will get those login attempts that have a login time greater than 18:00, which means those login attempts are registered after 6 pm, it can be done enabling filtering by using the word `WHERE` and using the specific filter greater than `>`, that code will read as follows:

    SELECT * 
    FROM log_in_attempts
    WHERE login_time > '18:00';


## Retrieve login attempts on specific dates
 
[Add content here.]

## Retrieve login attempts outside of Mexico

[Add content here.]

## Retrieve employees in Marketing

[Add content here.]

## Retrieve employees in Finance or Sales

[Add content here.]

## Retrieve all employees not in IT

[Add content here.]

## Summary

[Add content here.]