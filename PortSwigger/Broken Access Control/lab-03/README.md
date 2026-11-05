<h1>User Role Controlled by Request Parameter</h1>

<h2>1. Lab Information</h2>

| Field |	Details |
| --- | --- |
| Platform	| PortSwigger Web Security Academy |
| Category | Broken Access Control |
| Difficulty	| Apprentice |
| Status	| Completed |
| Date Completed |	[Date] |
| Tools Used | Burp Suite, Web Browser |

<h2> 2. Overview </h2>

This lab demonstrates a broken access control vulnerability in which a user's role or privilege level is determined by a client-controlled request parameter.

The application relies on information supplied by the client to determine whether a user has administrative privileges.

This creates an access control weakness because users may be able to manipulate request parameters and access functionality that should be restricted to administrators.

<h2> 3.Objective </h2>

The objective of this lab is to identify and exploit an access control weakness that allows a regular user to obtain unauthorized administrative privileges.

The exercise demonstrates why authorization decisions must be enforced on the server side rather than relying on client-controlled values.

<h2> 4. Vulnerability Explanation </h2>

Broken Access Control occurs when an application does not properly enforce restrictions on what authenticated users are allowed to access or perform.

In this scenario, the application uses a request parameter to determine the user's role.

If the application trusts this parameter without independently verifying the user's actual permissions, an attacker may be able to manipulate their privileges.

<h2>5. Technical Methodology</h2>

<h3> 5.1 Initial Reconnaisance </h3>

I accessed the lab application and examined its available functionality.

The initial objective was to understand how the application handled authentication, user roles, and access to restricted functionality.

<h3> 5.2 Vulnerability Investigation </h3>

I investigated whether the application relied on client-supplied information when determining authorization.

The key security concept was identifying whether the application independently validated the authenticated user's permissions on the server side.

<h3> 5.4 Verifications </h3>

I verified the access control weakness within the authorized training environment.

The successful completion of the lab demonstrated that the application's authorization mechanism could be bypassed.

<h2>6. Findings</h2>

Identified Vulnerability: Broken Access Control

Root Cause: The application relied on client-controlled information when determining user privileges rather than enforcing authorization through trusted server-side controls.

Security Impact: A user with ordinary privileges could potentially obtain access to functionality intended for administrators.

Result: Lab successfully completed.

<h2>7. Security Impact</h2>

Potential consequences include:

- Unauthorized access to administrative functionality.
- Privilege escalation.
- Unauthorized modification of application data.
- Access to restricted resources.
- Administrative account compromise, depending on the application.

<h2> 8. Recommended Remediation </h2>

To prevent this vulnerability, developers should:

1. Enforce authorization checks on the server side.
2. Never trust client-controlled role or privilege parameters.
3. Derive user permissions from trusted server-side session information.
4. Apply the principle of least privilege.
5. Validate authorization on every sensitive endpoint.
6. Implement appropriate logging and monitoring for unauthorized access attempts.

<h2> 9. Evidence </h2>

Supporting screenshots:


| Screenshot |	Description |
| --- | --- |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/309b3389-677e-4285-84e9-d3fe2e711083" /> |	Logged in as regular user |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/ee6aa63d-26c2-4b79-a6c9-b87c815d2a30" />	| Inspect using Dev Tools in Application Tab on Cookies |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/da2a1900-29ad-4baa-9600-bccec05dc005" />	| Admin changed to true and refreshing the application showed Admin Panel |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/d648eab0-6522-4830-b807-217eddc3e9d3" /> | Solved the lab by deleting user "carlos" |

<h2> 10. Key Takeaways </h2>

Through this lab, I learned:

- How broken access control can lead to privilege escalation.
- Why client-side information should never determine authorization.
- The importance of server-side access control validation.
- The security implications of improperly implemented role management.

<h2> 11. References </h2>

- PortSwigger – Access Control Vulnerabilities

--------------------------------------
Lab completed in the authorized PortSwigger training environment.

