<h1> Linux File Permissions </h1>
<h2>1. Challenge Information</h2>

| Field	| Details |
| --- | --- |
| Platform |		pwn.college |
| Dojo |	Linux Luminarium (example) |
| Module | 	File Permissions (example) |
| Challenge	| 	Linux File Permissions |
| Category	| 	Linux Fundamentals |
| Status	| Completed |
| Date Completed	| [Date] |
| Environment | Linux Terminal |  

<h2>2. Overview</h2>

This exercise focuses on understanding Linux file permissions and how access to files and directories is controlled within a Linux environment.

It explores the relationship between file ownership, user groups, and permission settings.

<h2>3. Objective</h2>

The objective is to understand how Linux determines whether a user can read, write, or execute a particular file.

The exercise also introduces commands used to inspect and manage file permissions.

<h2>4. Concepts Covered</h2>

<h3>Linux File Permissions</h3>

Linux uses three primary permission categories:

| Permission	| Meaning |
| --- | --- |
| Read (r)	| Allows reading file contents |
| Write (w)	| Allows modifying file contents |
| Execute (x)	| Allows executing a file |

<h3>Permission Representation</h3>

Example:

```
-rwxr-xr--
```

This represents:

- Owner: Read, write, execute
- Group: Read, execute
- Others: Read only

<h2>5. Tools and Commands</h2>

| Command |	Purpose |
| --- | --- |
| ls -l	| Display file permissions and ownership |
| chmod	| Modify file permissions |
| chown	| Change file ownership |
| id	| Display user and group information |
| whoami	| Identify the current user |

<h2>6. Methodology </h2>

<h3>6.1 Initial Environment Inspection</h3>

I examined the Linux environment and identified the available files and directories.

The ls -l command was used to inspect file permissions and ownership information.

<h3>6.2 Permission Analysis</h3>

I examined the permission representation to understand which operations were permitted for the file owner, group, and other users.

<h3>6.3 Command Execution</h3>

I used the relevant Linux commands to understand how file permissions are inspected and managed within the environment.

<h3>6.4 Verification</h3>

I verified the resulting file permissions and checked whether the intended access conditions were satisfied.

<h2>7. Findings</h2>

The exercise demonstrated how Linux uses file permission settings to control access to files.

It also reinforced the importance of understanding ownership and permission categories when administering Linux systems.

<h2>8. Security Relevance</h2>

Incorrectly configured file permissions can expose sensitive information or allow unauthorized modification and execution of files.

Examples include:

- Sensitive files readable by unauthorized users.
- Executable files with excessive permissions.
- Incorrect ownership assignments.
- Insecure directory permissions.

<h2>9. Key Takeaways</h2>

- Understood the Linux permission model.
- Learned how to inspect file ownership and permissions.
- Practiced using common Linux file management commands.
- Recognized the security implications of incorrect file permissions.

<h2>10. References</h2>

- pwn.college
- Linux man-pages

[Relevant documentation]

------------------------------------------
Personal technical documentation for educational purposes.
