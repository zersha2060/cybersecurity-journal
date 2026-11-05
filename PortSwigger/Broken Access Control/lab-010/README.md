# User ID Controlled by Request Parameter with Password Disclosure

<h2>1. Lab Information</h2>

| Field | Details |
| --- | --- |
| Platform | PortSwigger Web Security Academy |
| Category | Broken Access Control |
| Difficulty | Apprentice |
| Status | Completed |
| Date Completed | [Date] |
| Tools Used | Web Browser |

<h2>2. Overview</h2>

This lab demonstrates an Insecure Direct Object Reference (IDOR) vulnerability that can lead to unauthorized access to sensitive user information, including password disclosure.

The application uses a user ID supplied through a request parameter to retrieve account information. However, it does not properly verify whether the authenticated user is authorized to access the requested account.

As a result, an attacker may be able to manipulate the user ID parameter and access another user's profile information, potentially exposing sensitive credentials.

This creates a serious security weakness because unauthorized users may obtain information that could be used to compromise other accounts.

<h2>3. Objective</h2>

The objective of this lab is to identify and exploit an IDOR vulnerability that allows a regular user to access another user's account information and discover sensitive password information.

The exercise demonstrates why applications must enforce proper authorization checks and protect sensitive authentication data from unauthorized access.

<h2>4. Vulnerability Explanation</h2>

Broken Access Control occurs when an application fails to properly enforce restrictions on the resources and information users are allowed to access.

In this scenario, the application relies on a user ID provided through a request parameter to identify which user's profile information should be retrieved.

If the application does not verify whether the authenticated user is authorized to access the requested account, an attacker may be able to manipulate the user ID parameter and retrieve another user's information.

The vulnerability becomes more serious when sensitive information, such as passwords, is exposed through the application.

This combines Insecure Direct Object Reference (IDOR) with sensitive information disclosure.

<h2>5. Technical Methodology</h2>

<h3>5.1 Initial Reconnaissance</h3>

I accessed the PortSwigger lab application and logged in using the provided credentials.

After authentication, I explored the application's available functionality, particularly the user profile and account information features.

The initial objective was to understand how the application retrieved user information and whether sensitive account attributes were properly protected.

<h3>5.2 Vulnerability Investigation</h3>

During the investigation, I examined the request parameters and identified that the application used a user ID to retrieve profile information.

I also investigated whether the application exposed sensitive information through its profile functionality.

This revealed that the application did not properly restrict access to sensitive user information based on the authenticated user's permissions.

<h3>5.3 Exploitation</h3>

After identifying the weakness, I modified the user ID parameter in the URL to reference admin's account.

The application returned admin's profile information, which included sensitive password-related information.

I logged in as administrator with the exposed password and successfully deleted the user "carlos" using the admin privileges. 

This demonstrated that an attacker could potentially obtain another user's credentials by exploiting the IDOR vulnerability.

<h3>5.4 Verification</h3>

After identifying the exposed password information, I verified the result within the authorized training environment.

I confirmed that the application disclosed sensitive account information belonging to another user without properly enforcing access control.

The exposed credentials demonstrated the potential severity of the vulnerability and allowed the lab objective to be completed.

<h2>6. Findings</h2>

**Identified Vulnerability:** Broken Access Control – Insecure Direct Object Reference (IDOR) with Password Disclosure

**Root Cause:** The application relied on a user-controlled ID parameter without properly verifying authorization before returning sensitive account information.

**Security Impact:** An attacker could potentially access another user's profile and obtain sensitive password information, which may lead to unauthorized account access.

**Result:** Lab successfully completed.

<h2>7. Security Impact</h2>

Potential consequences include:

- Unauthorized access to other users' accounts.
- Exposure of sensitive password information.
- Credential compromise.
- Unauthorized access to confidential application data.
- Account takeover.
- Potential compromise of additional accounts if exposed credentials are reused elsewhere.

<h2>8. Recommended Remediation</h2>

To prevent this vulnerability, developers should:

1. Enforce server-side authorization checks for every user-specific resource.
2. Verify resource ownership before returning account information.
3. Never rely solely on user-supplied IDs to determine access permissions.
4. Never expose passwords or authentication secrets through profile pages or API responses.
5. Store passwords using strong, salted password hashing algorithms.
6. Apply the principle of least privilege.
7. Implement monitoring and logging for suspicious attempts to access other users' information.

<h2>9. Evidence</h2>

Supporting screenshots:

| Screenshot | Description |
| --- | --- |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/5a24d86c-d4a0-4000-9891-b57b08cc8ca7" /> | Logged in using the provided user account. |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/eb311765-f1ba-4df5-a2b3-1d5d9179ebc1" /> | Modified predictable id parameter in URL to check whether I can access another user profile. |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/a712bd30-6a30-4f76-9037-0ffddc52c392" /> | Discovered sensitive password information using Dev Tools. |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/c1c7c380-bf37-47e8-8221-82d34e653912" /> | Used the exposed admin password to log in and delete user "carlos". Successfully completing the lab. |

<h2>10. Key Takeaways</h2>

Through this lab, I learned:

- How IDOR vulnerabilities can expose sensitive user information.
- Why user-controlled identifiers should never determine authorization.
- How improper access control can lead to password disclosure.
- How to use Burp Suite to intercept and inspect HTTP requests and responses.
- The importance of protecting authentication-related information.
- Why passwords should never be exposed through application responses.
- How unauthorized information disclosure can lead to account compromise.

<h2>11. References</h2>

- [PortSwigger – Insecure Direct Object References (IDOR)](https://portswigger.net/web-security/access-control/idor)
- [PortSwigger – Access Control Vulnerabilities](https://portswigger.net/web-security/access-control)
- [PortSwigger – Password Storage](https://portswigger.net/kb/issues/00500700_password-stored-in-retrievable-format)

---

Lab completed in the authorized PortSwigger Web Security Academy training environment.
