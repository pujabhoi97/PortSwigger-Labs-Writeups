Lab 09: SQL Injection UNION Attack, Retrieving Data From Other Tables

## Lab Details

- Catagory: SQL Injection
- Difficulty: Practitioner

## Objective 

- Use a UNION-based SQL injection attack to retrieve the administrator's username and password from another database table.

## Vulnerability Explanation

- The application is vulnerable to SQL injection in the product catagory filter.
- By using  UNION attack, data can be retrieved from tables that are not normally accessible through the application.

## Finding the Vulnerability

- When selecting a product catagory, the URL contains a parameter similar to:

  /filter?catagory=Gifts

- The value of the 'catagory' parameter is used in a SQL query without proper validation.

## Explanation Steps

Step 1: Determine the Number of Columns

- Use a UNION SELECT statement with NULL values until the page loads successfully.

Example:

'+UNION+SELECT+NULL,NULL--

Step 2: Identify the Columns That Supports Text

- Replace each NULL with a text value one at a time until the value is displayed on the page.

Step 3: Retrieve User Credentials 

- After identifying the correct columns, use the following payload:

  '+UNION+SELECT+username,password+FROM+users--

- This retrieves the username and passwords stored in the 'users' table.

Step 4: Log In as Administrator

- Copy the administrator's password from the results and use it to log in as the administrator.

## Result

- The administrator's username and password were accessed successfully retrieved from the database.
- The administrator account was accessed successfully, completing the lab.

## Impact

- Sensitive user credentials can be exposed.
- Unauthorized access to user accounts is possible.
- Attackers may gain administrator privileges.

## Remediation

- Use parameterized queries.
- Validate and sanitize user input.
- Restrict database permissions.
- Never build SQL queries by directly concatenating user input.

## Key Learning 

- UNION-based SQL injection can be used to retrieve sensitive information from other database tables when the number of columns and compatible data types are known.

## Lab Status
- Solved✅ 
