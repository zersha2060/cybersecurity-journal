# User Role Can Be Modified in User Profile

<h2>1. Lab Information</h2>

| Field | Details |
| --- | --- |
| Platform | PortSwigger Web Security Academy |
| Category | Broken Access Control |
| Difficulty | Apprentice |
| Status | Completed |
| Date Completed | 2025 |
| Tools Used | Burp Suite, Web Browser |

<h2>2. Overview</h2>

This lab demonstrates a Broken Access Control vulnerability in which a user's role can be modified through the user profile functionality.

The application allows authenticated users to update their profile information. However, it also accepts modifications to security-sensitive attributes, such as the user's role, without properly verifying whether the user is authorized to perform such changes.

This creates an access control weakness because a regular user may be able to modify their own role and obtain unauthorized administrative privileges.

<h2>3. Objective</h2>

The objective of this lab is to identify and exploit an access control vulnerability that allows a regular user to escalate their privileges by modifying their role through the profile update functionality.

The exercise demonstrates why applications must enforce proper authorization checks and prevent ordinary users from modifying sensitive account attributes.

<h2>4. Vulnerability Explanation</h2>

Broken Access Control occurs when an application fails to properly enforce restrictions on what authenticated users are allowed to access or modify.

In this scenario, the application allows users to update their profile information but does not properly restrict modifications to security-sensitive attributes.

If the application trusts user-supplied information without independently verifying authorization, an attacker may be able to change their account role from a regular user to an administrator.

This vulnerability can lead to privilege escalation and unauthorized access to administrative functionality.

<h2>5. Technical Methodology</h2>

<h3>5.1 Initial Reconnaissance</h3>

I accessed the PortSwigger lab application and logged in using the provided credentials.

After authentication, I explored the available application functionality, particularly the user profile page and its profile update feature.

The initial objective was to understand how the application handled user information and whether sensitive account attributes were protected.

<h3>5.2 Vulnerability Investigation</h3>

I used Burp Suite to intercept and inspect the HTTP requests generated when updating profile information.

During the investigation, I examined the parameters submitted by the profile update functionality to determine whether the application accepted additional user attributes beyond the ordinary profile fields.

I identified that the user role could be included in the profile update request.

This indicated that the application was not properly restricting modifications to sensitive account properties.

<h3>5.3 Exploitation</h3>

After identifying the weakness, I modified the relevant request parameter responsible for the user's role.

I changed the role value from a regular user ("roleid": 1) to an administrative role ("roleid": 2) and forwarded the modified request to the application.

The application accepted the modification, demonstrating that an ordinary authenticated user could alter their own privilege level through the profile functionality.

<h3>5.4 Verification</h3>

After submitting the modified request, I verified whether the account's role had successfully changed.

I then accessed the application's restricted administrative functionality to confirm that the privilege escalation was successful.

The successful completion of the lab demonstrated that the application's authorization mechanism did not properly restrict modifications to user roles.

<h2>6. Findings</h2>

**Identified Vulnerability:** Broken Access Control – Privilege Escalation

**Root Cause:** The application allowed authenticated users to modify their own role through the profile update functionality without properly enforcing authorization restrictions.

**Security Impact:** A regular user could potentially escalate their privileges to administrator level and gain access to restricted application functionality.

**Result:** Lab successfully completed.

<h2>7. Security Impact</h2>

Potential consequences include:

- Unauthorized privilege escalation.
- Unauthorized access to administrative functionality.
- Unauthorized modification of application data.
- Exposure of restricted information.
- Unauthorized management of user accounts.
- Potential compromise of the application, depending on the privileges granted to administrators.

<h2>8. Recommended Remediation</h2>

To prevent this vulnerability, developers should:

1. Enforce authorization checks on the server side.
2. Prevent ordinary users from modifying security-sensitive attributes such as roles and permissions.
3. Implement an allowlist of profile fields that users are permitted to update.
4. Derive user permissions from trusted server-side session information.
5. Apply the principle of least privilege.
6. Validate authorization on every sensitive endpoint.
7. Implement appropriate logging and monitoring for suspicious role modifications.

<h2>9. Evidence</h2>

Supporting screenshots:

| Screenshot | Description |
| --- | --- |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/5ef4adf2-26d3-42e5-a3cc-e5f83a249bfc" /> | Logged in using a regular user account. |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/29159322-f1fa-4b4b-aa89-7306d68b2939" /> | Accessed the user profile page and examined the profile update functionality. |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/bc2363a2-8fbc-4267-9e91-a1b3a5b057e3" /> | Intercepted the profile update request using Burp Suite. |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/030ab7e9-7c79-4403-894b-8c1213035003" /> | Modified the user role parameter in the intercepted request. |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/46bf8b2b-76fe-4b18-b272-e3bb8e66873a" /> | Verified that the account successfully obtained administrative privileges. |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/a48b5555-f79c-4644-8fe0-b7bbc15a9c4f" /> | Successfully completed the lab. |

<h2>10. Key Takeaways</h2>

Through this lab, I learned:

- How insecure profile update functionality can lead to privilege escalation.
- Why client-controlled information should never determine user authorization.
- How to use Burp Suite to intercept and inspect HTTP requests.
- The importance of server-side authorization validation.
- Why user roles and permissions should be managed through trusted server-side controls.
- How improper handling of user-controlled parameters can result in Broken Access Control.

<h2>11. References</h2>

- [PortSwigger – Access Control Vulnerabilities](https://portswigger.net/web-security/access-control)
- [PortSwigger Web Security Academy – Broken Access Control](https://portswigger.net/web-security/access-control)

---

Lab completed in the authorized PortSwigger Web Security Academy training environment.
