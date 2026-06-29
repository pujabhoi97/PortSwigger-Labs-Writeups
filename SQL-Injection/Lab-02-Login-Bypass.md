Lab 02: SQL Injection Vulnerability Allowing Login Bypass

## Lab Details
- Catagory: SQL Injection
- Difficulty: Apprentice

## Objective

- Exploit a SQL injection vulnerability in the login form to gain access to the administrator account without knowing the password.

## Vulnerability Explanation

- The application does not properly validate user input in the login form.
-User input is directly included in the SQL query, making it possible to manipulate the query and bypass authentication.

## Finding the Vulnerability

- The application provides a login page where users can enter a username and password.

## Exploitation Steps

1. Open the login page.
2. Enter the following payload in the 'Username' field:
   administrator'--
3. Enter any value in the 'Password' field.
4. Click 'Log in'.

## Result

- You are successfully logged in as the administrator user. 
- This happens because:
  i. ' closes the username string.
  ii. -- comments out the rest of the SQL query, including the password check.

## Impact

- Authentication can be bypassed.
- Unauthorized access can be gained.
- Administrator accounts may be compromised.

## Remediation 

- Use parameterized queries.
- Validate and sanitize user input.
- Avoid directly including user input in SQL queries.

## Key Learning

- SQL injection vulnerabilities in login forms can allow attackers to bypass authentication and gain unauthorized access to accounts.

## Lab Status

- Solved✅ 
