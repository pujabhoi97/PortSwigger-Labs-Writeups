Lab 03: DOM XSS in document.write Sink Using Source location.search

## Lab Details

- Catagory: Cross-Site Scripting (XSS)
- Difficulty: Apprentice

## Objective

- Exploit a DOM-based XSS vulnerability using the document.write sink.

## Vulnerability Explanation

- The application reads data from the URL and writes it directly into the page using JavaScript's document.write() function.
- Because the input is not properly sanitized, malicious JavaScript can be injected and executed in the browser.

## Finding the Vulnerability

- The website contains a search function.
- The search term is taken from the URL and inserted into the page using document.write().

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

- The browser executes the JavaScript code contained in the onerror event.

- An alert box appears, confirming successful exploitation.

## Result

- The DOM-based XSS vulnerability was successfully exploited.
- JavaScript execution occured within the victim's browser, completing the lab.

## Impact

- Attackers can execute arbitary JavaScript.
- User sessions may be hijacked.
- Sensitive information may be stolen

## Remediation

- Avoid using document.write() with untrusted input.
- Sanitize and validate user-controlled data.

## Key Learning

- DOM XSS occurs entirely within the browser when client-side JavaScript processess untrusted data insecurely. Functions such as document.write() can introduce XSS vulnerabilities when user input is inserted into the page without proper sanitization.

## Lab Status
- Solved✅ 
