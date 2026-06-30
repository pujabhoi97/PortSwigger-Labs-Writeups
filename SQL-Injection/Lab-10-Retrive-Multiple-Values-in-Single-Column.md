Lab 10: SQL Injection UNION Attack, Retrieving Multiple Values in a Single Column

## Lab Details 

- Catagory: SQL Injection 
- Difficulty: Practitioner

## Objective

- Use a UNION-based SQL injection attack to retrieve the username and passwords from the 'users' table when only one column in the query can display text.

## Vulnerability Explanation

- The application is vulnerable to SQL injection in the product catagory filter.
- Since only one column can display text, multiple values must be combined into a single string before being displayed. This is done using the database's string concatenation operator.

## Finding the Vulnerability

- When selecting a product catagory, the URL contains a parameter similar to:

  /filter?catagory=Gifts

- The value of the 'catagory' parameter is used in a SQL query without proper validation.

## Explanation Steps 

Step 1: Determine the Number of Columns 

- Use a UNION SELECT statement with NULL values until the page loads successfully.

Example:

 '+UNION+SELECT+NULL,NULL--

Step 2: Identify the Text Column

- Replace each NULL with a text value to determine which column supports text data.

Step 3: Retrieve Multiple Values

- Use the following payload:
 
 '+UNION+SELECT+NULL,username||'~'||password+FROM+users--

- The || operator joins the username and password into a single string, while ~ separates the two values for easy reading.

Step 4: Log In as Administrator

= Copy the administrator's password from the response and use it to log in as the administrator.

## Result

- The usernames and passwords were successfully displayed in a single column.
- The administrator account was accessed successfully, completing the lab.

## Impact

- Sensitive user credentials can be exposed.
- Attackers can gain unauthorized access to user accounts.
- Administrative privileges may be compromised.

## Remediation

- Use parameterized queries.
- Validate and sanitize user input.
- Avoid directly including user input in SQL queries.

## Key Learning 

- When only one column can display text, multiple values can be combined into a single string using a string concatenation operator.
This technique allows attackers to extract multiple pieces of information from the database through a single column.

## Lab Status
- Solved✅ 
