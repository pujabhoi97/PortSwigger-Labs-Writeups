Lab 04: DOM XSS in innerHTML Sink Using Source location.search

## Lab Details

- Catagory: Cross-Site Scripting (XSS)
- Platform: Apprentice

## Objective 

- Exploit a DOM-based XSS vulnerability caused by the use of the innerHTML sink.

## Vulnerability Explanation

- The application takes user input from the URL and inserts it into the page using the innerHTML property.
- Because the input is not properly sanitized, HTML elements and JavaScript event handlers can be injected and executed in the browser.

## Finding the Vulnerability

- The website contains a search function.
- The serch term is read from the URL and inserted into the page using innerHTML.

## Exploitation Steps

Step 1: Perform a Search

- Search for any value and observe that the search term appears in the URL.

- Example:
  
  ?/search=test

Step 2: Inject a Payload 

- Replace the search term with the following payload:

  <img src=1 onerror=alert(1)>

Step 3: Load the URL

- Press Enter and load the page.

Step 4: Observe the Response 

- The browser parses the injected HTML and executes the JavaScript code in the 'onerror' event handler.

- The alert box appears, confirming successful exploitation.

## Result 

- The DOM-based XSS vulnerability was successfully exploited using the innerHTML sink.
- JavaScript execution occured in the browser, completing the lab.

## Impact 

- Attackers can execute arbitary JavaScript.
- User sessions may be hijacked.
- Sensitive information may be stolen.

## Remediation

- Avoid inserting untrusted data.
- Validate and sanitize user input.

## Key Learning

- The innerHTML property is a common source of DOM-based XSS vulnerabilities. When untrusted input is inserted directly into the DOM, attackers can inject HTML elements and JavaScript event handlers to achieve code execution.

## Lab Status
- Solved✅ 
