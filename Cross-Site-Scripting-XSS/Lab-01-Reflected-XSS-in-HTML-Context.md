Lab 01: Reflected XSS into HTML Context With Nothing Encoded

## Lab Details

- Catagory: Cross-Site Scripting (XSS)
- Difficulty: Apprentice

## Objective 

- Exploiting a reflected XSS vulnerability by injecting JavaScript into the search functionality of the application.

## Vulnerability Explanation

- The application reflects user input directly into the HTML response without any filtering or encoding.
- As a result, JavaScript code supplied by the user is executed by the browser.

## Finding the Vulnerability

- The Vulnerability contains a search function.
- Any text entered into the search box is reflected back onto the page.

## Exploitation Steps

Step 1: Enter a Test Payload

In the search box, enter:

<script>alert(1)</script>

Step 2: Submit the Search

Click the search button or press Enter.

Step 3: Observe the Response

The payload is reflected in the page and executed by the browser.

An alert box appears, demonstrating successful JavaScript execution.

## Result

- The JavaScript payload executed successfully, triggering an alert box.
- The reflected XSS vulnerability was successfully exploited, completing the lab.

## Impact

- Attackers can execute arbitary JavaScript in a victim's browser.
- User sessions may be stolen.
- Sensitive information may be accessed.
- User can be redirected to malicious websites.

## Remediation

- Encode user input before displaying it in HTML.
- Validate and sanitize user input.

## Key Learning 

- Reflected XSS occurs when user input is immediately returned in the application's response without proper encoding or sanitization.

## Lab Status
-Solved✅ 
