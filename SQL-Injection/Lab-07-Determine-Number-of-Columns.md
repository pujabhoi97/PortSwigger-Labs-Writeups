Lab 07: SQL injection UNION attack, determining the number of columns returned by the query

## Lab Details

- Catagory: SQL Imjection
- Difficulty: Practitioner

## Objective 

- Determine the number of columns returned by the original SQL query using a UNION attack.

## Vulnerability Explanation

- The application is vulnerable to SQL injection in the product catagory filter.
- Before performing a UNION attack, it is necessary to identify how many columns are returned by the original query. If the number of columns does not match, the database will return an error.

## Finding the Vulnerability

- When selecting a product catagory, the URL contains a parameter similar to:

  /filter?category=Gifts

- The value of the 'catagory' parameter is used in a SQL query without proper validation.

## Exploitation Steps

Step 1: Test with ORDER BY
- Use the following payloads and increase the number until an error occurs:

  '+ORDER+BY+1--

  '+ORDER+BY+2--

  '+ORDER+BY+3--

- Continue increasing the number until the application returns an error.

Step 2: Identify the Number of Columns
- If ORDER BY 3 works but ORDER BY 4 returns an error, the query contains 3 columns.

Step 3: Confirm Using UNION SELECT
- Use:

  '+UNION+SELECT+NULL,NULL,NULL--

- Replace the number of NULL values with the number of columns discovered.

- If the page loads successfully, the column count has been confirmed.

## Result

- The number of columns returned by the original query was successfully identified.
- This information can be used in later UNION-based SQL injection attacks.

## Impact

- Helps attackers craft successful UNION attacks.
- Enables extraction of data from the database.
- Can be used as a stepping stone for further exploitation.

## Remediation

- Use parameterized queries.
- Validate and sanitize user input.
- Prevent detailed database error messages from being displayed.

## Key Learning

- Determining the correct number of columns is a crucial step when performing UNION-based SQL injection attacks. The ORDER BY technique provides a quick way to identify the column count.

## Lab Status
- Solved✅ 
