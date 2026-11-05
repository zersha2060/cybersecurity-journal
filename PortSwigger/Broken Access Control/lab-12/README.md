# Access Control Vulnerabilities in Multi-Step Processes

<h2>1. Lab Information</h2>

| Field | Details |
| --- | --- |
| Platform | PortSwigger Web Security Academy |
| Category | Broken Access Control |
| Difficulty | Practitioner |
| Status | Completed |
| Date Completed | 2025 |
| Tools Used | Burp Suite, Web Browser |

<h2>2. Overview</h2>

This lab demonstrates a Broken Access Control vulnerability in which access restrictions are not properly enforced across a multi-step process.

The application uses multiple steps to perform sensitive administrative operations. However, the application does not consistently verify the user's authorization at every stage of the process.

This creates a security weakness because an unauthorized user may be able to bypass intermediate steps and directly access a later stage of an administrative operation.

As a result, an attacker may be able to perform restricted actions without having the required administrative privileges.

<h2>3. Objective</h2>

The objective of this lab is to identify and exploit an access control vulnerability in a multi-step administrative process.

The exercise demonstrates why applications must enforce authorization checks at every stage of a sensitive operation rather than assuming that users have already passed the required authorization checks in previous steps.

<h2>4. Vulnerability Explanation</h2>

Broken Access Control occurs when an application fails to properly enforce restrictions on sensitive functionality or operations.

In this scenario, the application performs an administrative operation through multiple steps.

For example, a sensitive operation may involve:

1. Initiating an administrative action.
2. Reviewing or confirming the requested changes.
3. Submitting the final request to complete the operation.

If the application only validates authorization during the initial step, an attacker may be able to bypass the earlier stages and directly submit a request to a later endpoint.

This creates a security weakness because the application assumes that reaching a later step means the user has already been authorized.

Proper authorization must be independently enforced on every endpoint involved in a multi-step process.

<h2>5. Technical Methodology</h2>

<h3>5.1 Initial Reconnaissance</h3>

I accessed the PortSwigger lab application and explored its available functionality.

The initial objective was to understand how the application handled administrative operations and whether sensitive actions required multiple steps to complete.

I examined the application's functionality to identify operations that involved confirmation or additional processing stages.

<h3>5.2 Vulnerability Investigation</h3>

I used Burp Suite to intercept and inspect the HTTP requests generated during the multi-step administrative process.

During the investigation, I examined the different requests sent by the application and identified the endpoints responsible for processing each stage.

I focused on determining whether authorization checks were consistently enforced across all stages of the operation.

The investigation revealed that the application did not properly enforce access restrictions on a later stage of the administrative process.

<h3>5.3 Exploitation</h3>

After identifying the weakness, I investigated whether the later stage of the administrative process could be accessed directly.

Using Burp Suite, I examined the relevant HTTP requests and tested whether the final operation could be submitted without completing the expected earlier authorization steps.

The application processed the request without properly verifying whether the authenticated user had administrative privileges.

This demonstrated that the multi-step process could be bypassed due to insufficient authorization enforcement.

<h3>5.4 Verification</h3>

After submitting the modified request, I examined the server response to determine whether the restricted administrative operation had been successfully performed.

I verified that the application accepted the operation despite the user not having the required administrative privileges.

The successful completion of the lab demonstrated that authorization checks were not consistently enforced throughout the multi-step process.

<h2>6. Findings</h2>

**Identified Vulnerability:** Broken Access Control – Multi-Step Process Authorization Bypass

**Root Cause:** The application failed to enforce authorization checks consistently across all stages of a sensitive administrative operation.

**Security Impact:** An unauthorized user could potentially bypass intermediate steps and perform restricted administrative actions.

**Result:** Lab successfully completed.

<h2>7. Security Impact</h2>

Potential consequences include:

- Unauthorized execution of administrative operations.
- Bypass of intermediate authorization checks.
- Unauthorized modification of application settings.
- Unauthorized changes to user accounts and permissions.
- Exposure or modification of sensitive application data.
- Potential privilege escalation.

<h2>8. Recommended Remediation</h2>

To prevent this vulnerability, developers should:

1. Enforce server-side authorization checks at every stage of a multi-step process.
2. Never assume that users have been authorized simply because they reached a previous step.
3. Validate the authenticated user's permissions before processing sensitive operations.
4. Protect final submission endpoints against direct unauthorized access.
5. Apply the principle of least privilege.
6. Implement centralized authorization mechanisms.
7. Log and monitor attempts to bypass intermediate steps or access restricted endpoints directly.

<h2>9. Evidence</h2>

Supporting screenshots:

| Screenshot | Description |
| --- | --- |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/72ecb227-08fa-4f19-8ca0-77f2872f6fbf" /> | Accessed the lab application using admin credentials to familiarize myself with administrative functionalities. |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/92e96813-9a1d-4c6a-a014-d7509c816ecf" /> | Using cookie session from a regular user. Skip some steps in upgrading a role in admin functionalities to check if it can be bypassed.   |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/e92f76af-fde1-42ac-a5c0-f40668774caa" /> | Upgraded role successfully and completing the lab. |

<h2>10. Key Takeaways</h2>

Through this lab, I learned:

- How multi-step processes can introduce Broken Access Control vulnerabilities.
- Why authorization checks must be enforced at every stage of an operation.
- How to use Burp Suite to intercept and analyze multi-step HTTP requests.
- Why applications should not rely on previous authorization checks.
- How direct access to later-stage endpoints can bypass intended restrictions.
- The importance of implementing consistent server-side authorization.
- How improper access control can allow unauthorized administrative operations.

<h2>11. References</h2>

- [PortSwigger – Access Control Vulnerabilities](https://portswigger.net/web-security/access-control)
- [PortSwigger Web Security Academy – Broken Access Control](https://portswigger.net/web-security/access-control)

---

Lab completed in the authorized PortSwigger Web Security Academy training environment.
