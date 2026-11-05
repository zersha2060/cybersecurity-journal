<h1>Unprotected admin functionality</h1>

<h2>1. Lab Information</h2>

| Field |	Details |
| --- | --- |
| Platform	| PortSwigger Web Security Academy |
| Category | Broken Access Control |
| Difficulty	| Apprentice |
| Status	| Completed |
| Date Completed |	2025 |
| Tools Used | Burp Suite, Web Browser |

<h2> 2. Overview </h2>

This lab demonstrates a broken access control vulnerability in which a website has a lack of protection for sensitive functionality.

This creates an access control weakness because users may be able to access the admin panel along with its functions by modifying/changing the website's URL.

<h2> 3.Objective </h2>

The objective of this lab is to identify and exploit an access control weakness that allows a regular user to have access to admin functions and delete an account with the name "carlos".

The exercise demonstrates why it is important to enforce protection in making sure that access to certain functionalities can only be done once the user is determined to have authorization to the said functionalities and panels.

<h2> 4. Vulnerability Explanation </h2>

Broken Access Control occurs when an application does not properly enforce restrictions on what authenticated users are allowed to access or perform.

In this scenario, the user was able to access the website's admin panel by changing the URL.

If the application does not enforce any protection, an attacker may be able to manipulate their privileges.

<h2>5. Technical Methodology</h2>

<h3> 5.1 Initial Reconnaisance </h3>

I accessed the lab application and examined its available functionality.

The initial objective was to understand how the application's URL works.

<h3> 5.2 Vulnerability Investigation </h3>

I checked the application's URL handling and tried to modify the URL.

The key security concept was identifying whether the application will permit me to access the admin panel even without any authentication needed.

<h3> 5.3 Verifications </h3>

I verified the access control weakness within the authorized training environment.

The successful completion of the lab demonstrated that the application's URL can be used to gain access to admin panel and used its privileges.

<h2>6. Findings</h2>

Identified Vulnerability: Broken Access Control

Root Cause: The application did not have any protection against sensitive functionality.

Security Impact: A user with ordinary privileges could potentially obtain access to functionality intended for administrators.

Result: Lab successfully completed.

<h2>7. Security Impact</h2>

Potential consequences include:

- Unauthorized access to administrative functionality.
- Vertical Privilege escalation.
- Unauthorized modification of users data (i.e. deleting user accounts).
- Access to restricted resources.
- Administrative account compromise, depending on the application.

<h2> 8. Recommended Remediation </h2>

To prevent this vulnerability, developers should:

1. Enforce authorization checks on the server side.
2. Users should be assigned explicit roles that determines which access they are granted to.
3. Use centralized routing to intercept incoming requests and validate security tokens first.
4. Manage authentication states in secure server-side tokens
5. Routes should be locked down completely by default unless authorization rule grants access.

<h2> 9. Evidence </h2>

Supporting screenshots:


| Screenshot | Definition |
| --- | --- |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/5e00c9e8-03d1-4478-a038-33faffae5183" /> | 01 - application's home page |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/3b045b96-df29-451a-8203-72e2b93d047f" /> | 02 - modified the URL by using robots.txt which showed the route to admin panel |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/4024c6ef-5826-49dd-82a8-cb0cee438885" /> | 03 - admin panel where I was able to delete the user "carlos" per the lab's requirement for completion. |


<h2> 10. Key Takeaways </h2>

Through this lab, I learned:

- How broken access control can lead to privilege escalation.
- Why it is important to enforce protection for sensitive functionalities.
- The importance of server-side access control validation.
- The security implications of improper routing of user's access and permissions.

<h2> 11. References </h2>

- PortSwigger – Access Control Vulnerabilities

--------------------------------------
Lab completed in the authorized PortSwigger training environment.
