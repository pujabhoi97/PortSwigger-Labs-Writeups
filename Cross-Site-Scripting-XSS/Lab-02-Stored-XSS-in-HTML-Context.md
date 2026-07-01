Lab 02: Stored XSS into HTML Context With Nothing Encoded

## Lab Details

- Catagory: Cross-Site Scripting (XSS)
- Difficulty: Apprentice

## Objective

- Exploit a stored XSS vulnerability by injecting JavaScript into the comment section of a blog post.

## Vulnerability Explanantion

- The application stores user input and displays it to other users without any filtering or encoding.
- As a result, malicious JavaScript code submitted by a user is permanently stored and executed whenever the page is viewed.

## Finding the Vulnerability 

- The website allows users to submit comments on blog posts.
- User input submitted through the comment form is displayed on the page without being sanitized.

## Exploitation Steps
Step 1: Open a Blog Post

- Navigate to any blog post and scroll to the comment section.

Step 2: Submit a Malicious Comment

- Enter the following payload in the comment field:

  <script>alert(1)</script>

- Fill in the remaining fields and submit the comment.

Step 3: View the Comment

- After the comment is posted, the payload is displayed on the page.

Step 4: Observe the Response

- The browser executes the JavaScript code and displays an alert box.

## Result

- The payload was stored by the application and executed when the page loaded.
- The stored XSS vulnerability was successfully exploited, completing the lab.

## Impact

- Attackers can execute arbitrary JavaScript in other users' browsers.
- Session cookies may be stolen.
- User accounts may be compromised.
- Malicious content can be delivered to all visitors of the page.

## Remediation

- Encode user input before displaying it in HTML.
- Validate and sanitize user input.

## Key Learning

- Stored XSS is more dangerous than reflected XSS because the malicious payload is saved on the server and automatically executed whenever users view the affected page.

## Lab Status
- Solved✅
