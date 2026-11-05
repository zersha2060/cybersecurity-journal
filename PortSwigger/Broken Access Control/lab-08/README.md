# User ID Controlled by Request Parameter, with Unpredictable User IDs

<h2>1. Lab Information</h2>

| Field | Details |
| --- | --- |
| Platform | PortSwigger Web Security Academy |
| Category | Broken Access Control |
| Difficulty | Apprentice |
| Status | Completed |
| Date Completed | 2025 |
| Tools Used | Web Browser |

<h2>2. Overview</h2>

This lab demonstrates an Insecure Direct Object Reference (IDOR) vulnerability, which is a type of Broken Access Control.

The application uses unpredictable user IDs to identify individual user accounts. Although the identifiers are difficult to guess, the application does not properly verify whether the authenticated user is authorized to access the requested account.

The application exposes user-specific information through request parameters, creating a potential security weakness when access control is not properly enforced.

This demonstrates that unpredictable identifiers alone are not sufficient to protect sensitive resources from unauthorized access.

<h2>3. Objective</h2>

The objective of this lab is to identify and exploit an IDOR vulnerability that allows access to another user's information despite the application using unpredictable user IDs.

The exercise demonstrates why applications must enforce proper authorization checks rather than relying on difficult-to-guess identifiers as a security mechanism.

<h2>4. Vulnerability Explanation</h2>

Broken Access Control occurs when an application fails to properly enforce restrictions on the resources and information users are allowed to access.

In this scenario, the application uses unpredictable user IDs instead of simple sequential identifiers.

However, if the application does not verify whether the authenticated user has permission to access the requested account, an attacker may still be able to obtain another user's identifier and access their information.

This vulnerability is commonly associated with Insecure Direct Object Reference (IDOR).

Unpredictable identifiers may make unauthorized access more difficult, but they do not replace proper server-side authorization.

<h2>5. Technical Methodology</h2>

<h3>5.1 Initial Reconnaissance</h3>

I accessed the PortSwigger lab application and logged in using the provided credentials.

After authentication, I explored the available functionality, particularly the user profile and account information features.

The initial objective was to understand how the application identified individual users and how their information was retrieved.

<h3>5.2 Vulnerability Investigation</h3>

During the investigation, I examined the request parameters and identified that the application used unpredictable user IDs to retrieve account information.

Unlike applications that use sequential numeric identifiers, the application used identifiers that were more difficult to guess.

I then investigated whether these identifiers could be discovered through other application resources, such as publicly accessible information like their posted blogs or user-related content.

<h3>5.3 Exploitation</h3>

After investigating the application, I identified a way to obtain another user's unpredictable identifier through clicking on another user's post and clicking on their username.

I used the discovered identifier to modify the relevant user ID parameter in URL inside the my-account page to see if it will display another user's account.

The application returned the requested information without properly verifying whether the authenticated user was authorized to access that account.

This demonstrated that unpredictable user IDs did not prevent the underlying IDOR vulnerability.

<h3>5.4 Verification</h3>

I confirmed that the application exposed another user's information through the manipulated request.

The successful completion of the lab demonstrated that unpredictable identifiers do not provide sufficient protection when proper server-side authorization checks are missing.

<h2>6. Findings</h2>

**Identified Vulnerability:** Broken Access Control – Insecure Direct Object Reference (IDOR)

**Root Cause:** The application relied on unpredictable user IDs without properly verifying whether the authenticated user was authorized to access the requested account.

**Security Impact:** An attacker who discovers another user's identifier could potentially access private account information without authorization.

**Result:** Lab successfully completed.

<h2>7. Security Impact</h2>

Potential consequences include:

- Unauthorized access to other users' accounts.
- Exposure of sensitive personal information.
- Unauthorized retrieval of private user data.
- Privacy violations.
- Access to confidential application resources.
- Potential account compromise, depending on the information exposed and available functionality.

<h2>8. Recommended Remediation</h2>

To prevent this vulnerability, developers should:

1. Enforce authorization checks on the server side for every user-specific resource.
2. Verify resource ownership before returning sensitive account information.
3. Never rely solely on unpredictable or difficult-to-guess identifiers for access control.
4. Apply the principle of least privilege.
5. Implement object-level authorization checks on every relevant endpoint.
6. Avoid exposing sensitive user identifiers through publicly accessible resources.
7. Log and monitor suspicious attempts to access other users' resources.

<h2>9. Evidence</h2>

Supporting screenshots:

| Screenshot | Description |
| --- | --- |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/db455911-c735-45fa-8c40-4a7c9ad58d4d" /> | Logged in using the provided user account and identified the unpredictable user ID parameter. |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/08549912-2737-4466-a89e-c2a5827a57cb" /> | Investigated application resources to discover another user's identifier |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/6012c32e-b085-49c3-9094-7454ce03bf8e" /> | Modified the request using the discovered user ID. |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/af5a345e-7e78-4c7c-8132-ad825fc55f58" /> | Successfully completed the lab. |

<h2>10. Key Takeaways</h2>

Through this lab, I learned:

- How IDOR vulnerabilities can exist even when applications use unpredictable identifiers.
- Why difficult-to-guess user IDs are not a replacement for proper authorization.
- How to use Burp Suite to intercept and inspect HTTP requests.
- How exposed application resources may reveal identifiers belonging to other users.
- The importance of implementing object-level authorization.
- Why applications must verify resource ownership before providing access.
- How improper access control can lead to unauthorized information disclosure.

<h2>11. References</h2>

- [PortSwigger – Insecure Direct Object References (IDOR)](https://portswigger.net/web-security/access-control/idor)
- [PortSwigger – Access Control Vulnerabilities](https://portswigger.net/web-security/access-control)

---

Lab completed in the authorized PortSwigger Web Security Academy training environment.
