Lab 03: SQL Injection Attack, Querying The Database Type And Version On Oracle

## Lab Details

- Catagory: SQL Injection
- Difficulty: Practitioner

## Objective


- Use a SQL injection vulnerability to determine the version of the Oracle database used by the application.

## Vulnerability Explanation

- The application is vulnerable to SQL injection in the product catagory filter.
- By using a UNION attack, additional SQL queries can be appended to the original query and information can be retrieved from the database.

## Finding the Vulnerability 

- When selecting a product catagory, the URL contains a parameter similar to:
  /filter?catagory=Gifts
- The value of the 'catagory' parameter is reflected in a SQL query executed by the application.

## Exploitation Steps

1. Determine the number of columns returned by the query.
2. Identify a column that can display text data.
3. Use the following payload:
   '+UNION+SELECT+BANNER,NULL+FROM+v$version--
4. Submit the payload in the catagory parameter.

## Result
- The application displays information from the Oracle database version table.
- The database version is successfully retrieved, which completes the lab.

## Impact

- Database information can be disclosed.
- Attackers can gather details about the backend technology.
- Version information may help attackers identify known vulnerabilities.

## Remediation

- Use parameterized queries.
- Validate and sanitize user input.
- Restrict database error messages and information disclosure.

## Key Learning

- UNION-based SQL injection can be used to retrieve information directly from the database. Identifying the database version is often an important step in further exploitation.

## Lab Status
- Solved✅ 
