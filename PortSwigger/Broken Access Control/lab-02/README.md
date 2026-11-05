<h1>Unprotected admin functionality with unpredictable URL</h1>

<h2>1. Lab Information</h2>

| Field |	Details |
| --- | --- |
| Platform	| PortSwigger Web Security Academy |
| Category | Broken Access Control |
| Difficulty	| Apprentice |
| Status	| Completed |
| Date Completed |	2025 |
| Tools Used | Web Browser |

<h2> 2. Overview </h2>

This lab demonstrates a broken access control vulnerability in which a website has a lack of protection for sensitive functionality.

This creates an access control weakness because users may be able to access the admin panel along with its functions by modifying/changing the website's URL even when the application applied the "security by obscurity".

<h2> 3.Objective </h2>

The objective of this lab is to identify and exploit an access control weakness that allows a regular user to have access to admin functions and delete an account with the name "carlos".

The exercise demonstrates how the application might still leak admin panel URL to users even if it is obfuscated.

<h2> 4. Vulnerability Explanation </h2>

Broken Access Control occurs when an application does not properly enforce restrictions on what authenticated users are allowed to access or perform.

In this scenario, the user was able to access the website's admin panel by inspecting the application using Dev Tools.

Obfuscating the URL in an attempt to hide a sensitive functionality can still leak and may be able to manipulate admin privileges.

<h2>5. Technical Methodology</h2>

<h3> 5.1 Initial Reconnaisance </h3>

I accessed the lab application and checked if modifying to a recognizable URL will work with accessing the admin panel.

The initial objective was to understand how the application's URL works. Since it didn't work, the next step was to Inspect using Dev Tools and go to network tab.

<h3> 5.2 Vulnerability Investigation </h3>

Since modifying the URL will not work due to obfuscated URL. In the network tab, I looked for any response to when I clicked on login page to see how the response will look like in the script. There, I saw how it checks if the user will log as admin and will redirect to a link named "/admin-ncmrk0" for admin panel.   

The key security concept was identifying whether the application will leak the obfuscated URL somewhere in its script to redirect the admin to its admin panel.

<h3> 5.3 Verifications </h3>

I verified the access control weakness within the authorized training environment.

The successful completion of the lab demonstrated that the application's URL can be used to gain access to admin panel and used its privileges.

<h2>6. Findings</h2>

Identified Vulnerability: Broken Access Control

Root Cause: The application used an obfuscated URL but the script that authenticates if a user is admin is leaked along with its admin panel URL.

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

1. Perform authorization checks on the server side.
2. Exclude administrative routing configuration.
3. Use server-driven code splitting or dynamic imports.
4. Implement strict authorization model.

<h2> 9. Evidence </h2>

Supporting screenshots:


| Screenshot | Definition |
| --- | --- |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/a3909174-aee5-4544-9945-06b9ebb6d69d" /> | 01 - application's login page |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/713fa5a2-72fe-40bc-9c79-60720fff9781" /> | 02 - where I found the obfuscated URL |
| <img width="400" alt="image" src="https://github.com/user-attachments/assets/d05a2d25-d641-41a4-a321-369afd03890a" /> | 03 - admin panel where I was able to delete the user "carlos" in admin panel per the lab's requirement for completion. |


<h2> 10. Key Takeaways </h2>

Through this lab, I learned:

- How broken access control can lead to privilege escalation.
- Why even obfuscated URLs can still be leaked through application's script.
- The importance of server-side access control validation.

<h2> 11. References </h2>

- PortSwigger – Access Control Vulnerabilities

--------------------------------------
Lab completed in the authorized PortSwigger training environment.
