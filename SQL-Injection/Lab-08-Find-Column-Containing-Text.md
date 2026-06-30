Lab 08: SQL Injection UNION Attack, Finding a Column Containing Text

## Lab Details

- Catagory: SQL Injection
- Difficulty: Practitioner

## Objective

- Identify which columns in the database query can hold text data and display the results on the page.

## Vulnerability Explanation

- The application is vulnerable to UNION-based SQL injection in the product catagory filter.
- To retrieve useful information from the database, it is important to determine which columns can store text values.

## Finding the Vulnerability

- When selecting a product catagory, the URL contains a parameter similar to:

  /filter?catagory=Gifts

- The value of the 'catagory' parameter is used in a SQL query without proper validation.

## Exploitation Steps

Step 1: Determine the Number of Columns
- Use ORDER BY or UNION SELECT techniques to identify the number of columns returned by the query.

Example: 

 '+UNION+SELECT+NULL,NULL,NULL--

Step 2: Test Each Column for Text Support
- Replace each NULL value with a text string one column at a time.

 '+UNION+SELECT+'test',NULL,NULL--
 
 '+UNION+SELECT+NULL,'test',NULL--

 '+UNION+SELECT+NULL,NULL,'test'--

Step 3: Identify the Text Columns
- Observe the page response and determine which column displays the text value.

## Result 

- The columns capable of displaying text data were successfully identified.
-This information can be used in future UNION-based SQL injection attacks to extract database information.

## Impact 

- Helps attackers identify usable columns for data extraction.
- Facilities successful UNION-based SQL injection attacks.
- Enables retrieval of sensitive database information.

## Remediation

- Use parameterized queries.
- Validate and sanitize user input.
- Prevent SQL errors from being exposed to users.

## Key Learning 

- Before extracting data with a UNION attack, it is important to determine which columns support text values. This allows attackers to display database information in the application's response.

## Lab Status 
-Solved✅ 
