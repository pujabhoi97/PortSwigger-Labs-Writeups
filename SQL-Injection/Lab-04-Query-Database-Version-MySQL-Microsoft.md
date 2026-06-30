Lab 04: SQL Injection Attack, Querying The Database Type And Version On MySQL And Microsoft

## Lab Details

- Catagory: SQL Injection 
- Difficulty: Practitioner

## Objective 

- Use a SQL injection vulnerability to determine the version of the MySQL or Microsoft database used by the application.

## Vulnerability Explanation

- The application is vulnerable to SQL injection in the product catagory filter.
- By using a UNION attack, additional queries can be combined with the original query to retrieve information from the database.

## Finding the Vulnerability

- When selecting a product catagory, the URL contains a parameter similar to:

  /filter?catagory=Gifts 

- The value of the 'catagory' parameter is processed by a SQL query on the backend.

## Exploitation Steps 

1. Determine the number of columns returned by the query.
2. Identify which columns can display text data.
3. Use the following payload:
   
   '+UNION+SELECT+@@version,NULL--
4. Submit the payload in the catagory parameter.

## Result

- The application displays the database version information.
- The version of the MySQL or Microsoft database is successfully retrieved, which completes the lab.

## Impact

- Database information can be disclosed.
- Attackers can identify the backend database technology.
- Version information may help attackers find known vulnerabilities.

## Remediation

- Use parameterized queries.
- Validate and sanitize user input.
- Prevent unnecessary database information disclosure.

## Key Learning

- UNION-based SQL injection can be used to extract information from the database. Determining the database version helps attackers understand the target environment and plan further attacks.

## Lab Status

- Solved✅ 
