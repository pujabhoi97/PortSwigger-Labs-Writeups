Lab 01: SQL Injection Vulnerability in WHERE Clause Allowing Retrieval of Hidden Data

## Lab Details
- Catagory: SQL Injection
- Difficulty: Apprentice

## Objective
- Exploit a SQL injection vulnerability to view hidden product on the website.

## Vulnerability Explanation
- The application filters product using a SQL query based on the catagory selected by the user.
- The query also checks whether a product is released or not.
- User input is directly added to the SQL query without proper validation.

## Finding the Vulnerability
- When clicking on a product catagory, the URL looks like:
 /filter?catagory=Gifts
- This 'catagory' parameter is vulnerable to Sql injection.

## Explanation Steps
1. Open any product catagory.
2. Modify the URL parameter to:
 /filter?catagory=Gifts' OR 1=1
3. Press Enter.

## Result
- All products are displayed, including hidden or unreleased products.
- This happens because:
  i. 'OR 1=1' is always true
  ii. '--' comments out the rest of the SQL query

## Impact
- Hidden data can be accessed
- Business logic can be bypassed
- Sensitive information may be exposed

## Remediation
- Use prepared statements
- Validate user input
- Avoid directly inserting user input SQL queries 

## Key Learning
- Improper input validation can allow attackers to manipulate SQL queries and access unauthorized data.

## Lab Status
- Solved✅




























  












