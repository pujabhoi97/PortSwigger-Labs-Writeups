Lab 05: AngularJS Sandbox Escape Without Strings

## Lab Details

- Category: Cross-Site Scripting (XSS)
- Difficulty: Expert

## Objective 

- Exploit a client-side template injection vulnerability in an AngularJS application and execute JavaScript without using string literals.

## Vulnerability Explanation

- The application uses AngularJS to process user input.
- User-controlled data is embedded into an AngularJS template without proper sanitization, allowing AngularJS expressions to be executed in the browser.
- Although the AngularJS sandbox attempts to restrict access to dangerous functions, it can be bypassed using specially crafted expressions.

## Finding the Vulnerability

- The search parameter is reflected inside an AngularJS template.

- Testing with: 

  {{7*7}}

  returns:

  49

- This confirms that AngularJS expressions are being evaluated.

## Exploitation Steps

Step 1: Confirm Template Injection

- Inject:

  {{7*7}}

- This result is evaluated and displayed by the application.

Step 2: Escape the AngularJS Sandbox 

- Use the following payload:

  {{$on.constructor('alert(1)')()}}

Step 3: Load the Payload

- Submit the payload through the vulnerable search parameter.

Step 4: Observe the Response

- The browser executes the JavaScript code and displays an alert box.

## Result 

- The AngularJS sandbox was bypassed successfully.
- Arbitary JavaScript execution was achieved, completing the lab.

## Impact

- Attackers can execute arbitary JavaScript.
- User sessions may be hijacked.
- Sensitive information may be accessed.

## Remediation

- Do not evaluate untrusted user input as AngularJS template.
- Sanitize user input before rendering.

## Key Learning

- Client-Side Template Injection can lead to Cross-Site Scripting when template engines evaluate user-controlled input.

## Lab Status
- Solved✅ 
