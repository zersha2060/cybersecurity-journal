# User ID Controlled by Request Parameter

<h2>1. Lab Information</h2>

| Field | Details |
| --- | --- |
| Platform | PortSwigger Web Security Academy |
| Category | Broken Access Control |
| Difficulty | Apprentice |
| Status | Completed |
| Date Completed | 2025 |
| Tools Used |  Web Browser |

<h2>2. Overview</h2>

This lab demonstrates an Insecure Direct Object Reference (IDOR) vulnerability, which is a type of Broken Access Control.

The application uses a user ID supplied through a request parameter to retrieve account information. However, it does not properly verify whether the authenticated user is authorized to access the requested account.

This creates a security weakness because an attacker may be able to manipulate the user ID parameter and access another user's private information.

<h2>3. Objective</h2>

The objective of this lab is to identify and exploit an access control vulnerability that allows a regular user to access another user's account information by modifying a user ID request parameter.

The exercise demonstrates why applications must verify ownership and authorization before providing access to user-specific resources.

<h2>4. Vulnerability Explanation</h2>

Broken Access Control occurs when an application fails to properly enforce restrictions on the resources and information users are allowed to access.

In this scenario, the application relies on a user ID provided through a request parameter to identify which user's information should be displayed.

If the application does not verify whether the authenticated user has permission to access the requested user ID, an attacker may be able to manipulate the parameter and retrieve information belonging to another user.

This vulnerability is commonly known as Insecure Direct Object Reference (IDOR).

<h2>5. Technical Methodology</h2>

<h3>5.1 Initial Reconnaissance</h3>

I accessed the PortSwigger lab application and logged in using the provided credentials.

After authentication, I explored the application's functionality, particularly the account information and user profile features.

The initial objective was to understand how the application identified users and retrieved their account information.

<h3>5.2 Vulnerability Investigation</h3>

During the investigation, I examined the request parameters to identify whether the application used a user ID to retrieve account information.

I identified that the application relied on a user-controlled request parameter to determine which user's information would be displayed.

This suggested that the application might not properly validate whether the authenticated user was authorized to access the requested account.

<h3>5.3 Exploitation</h3>

After identifying the potential weakness, I modified the user ID parameter in the intercepted HTTP request.

I changed the parameter to reference another user's account (carlos) and forwarded the modified request to the application.

The application returned information belonging to the carlos without properly verifying ownership or authorization.

This demonstrated that the application was vulnerable to IDOR through a user-controlled request parameter.

<h3>5.4 Verification</h3>

After modifying the request parameter, I examined the server response to verify whether information belonging to another user could be accessed.

I confirmed that the application exposed another user's account information through the manipulated request.

The successful completion of the lab demonstrated that the application did not properly enforce access controls when retrieving user-specific resources.

<h2>6. Findings</h2>

**Identified Vulnerability:** Broken Access Control – Insecure Direct Object Reference (IDOR)

**Root Cause:** The application relied on a user-controlled ID request parameter without properly verifying whether the authenticated user was authorized to access the requested account.

**Security Impact:** An attacker could potentially access sensitive information belonging to other users by manipulating the user ID parameter.

**Result:** Lab successfully completed.

<h2>7. Security Impact</h2>

Potential consequences include:

- Unauthorized access to other users' accounts.
- Exposure of sensitive personal information.
- Unauthorized retrieval of private user data.
- Privacy violations.
- Potential access to confidential application resources.
- Account compromise, depending on the information exposed and available functionality.

<h2>8. Recommended Remediation</h2>

To prevent this vulnerability, developers should:

1. Enforce authorization checks on the server side for every user-specific resource.
2. Verify resource ownership before returning sensitive account information.
3. Never rely solely on user-supplied IDs to determine access permissions.
4. Apply the principle of least privilege.
5. Implement object-level authorization checks on every relevant endpoint.
6. Use indirect object references where appropriate.
7. Log and monitor suspicious attempts to access other users' resources.

<h2>9. Evidence</h2>

Supporting screenshots:

| Screenshot | Description |
| --- | --- |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/b83f6185-aaf8-4790-a5c3-5b29292e7d14" /> | Logged in using the provided user account. |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/5bac25f1-7d2d-4997-9e80-fc816e7ae2c4" /> | Identified the user ID request parameter. |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/291c8667-31bc-4001-ab15-63be05e43eb4" /> | Modified the user ID parameter to access another user's information and retrieved the information belonging to another user. Successfully completing the lab. |


<h2>10. Key Takeaways</h2>

Through this lab, I learned:

- How IDOR vulnerabilities can expose other users' information.
- Why user-controlled identifiers should not determine authorization.
- How to use Burp Suite to intercept and modify HTTP requests.
- The importance of implementing object-level authorization.
- Why applications must verify resource ownership before providing access.
- How improper access control can lead to unauthorized data disclosure.

<h2>11. References</h2>

- [PortSwigger – Insecure Direct Object References (IDOR)](https://portswigger.net/web-security/access-control/idor)
- [PortSwigger – Access Control Vulnerabilities](https://portswigger.net/web-security/access-control)

---

Lab completed in the authorized PortSwigger Web Security Academy training environment.
