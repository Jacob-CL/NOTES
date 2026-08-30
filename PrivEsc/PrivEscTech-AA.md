# Chapter 1 - Introduction
- The process of exploiting **vulnerabilities** OR **misconfigs** in systems to elevate privileges from one user to another.
- Occurs usually after initial access / foothold.
- Operating systems are designed to handle multiple users with multiple users with multiple roles and permissions. This abstraction of user roles and permissions on a system is called a PROTECTION RING.
- The different rings in the heirachy represent layers of privileges within the OS

<img width="650" height="467" alt="image" src="https://github.com/user-attachments/assets/8c72c348-357d-4782-9603-1f50e62490a0" />

## Root
- Install, uninstall and modify system software or binaries.
- Add, modify, or remove users and user groups.
- Create, access, modify, and delete any system or user data
- Access and have control over all system hardware
- Create, manage and kill system and user processes.

## Non-root
- Ability to start and stop user processes and programs
- Ability to create, modify, and delete user data
- Access to network functionality.

## Two methods of pivesc
### HORIZONTAL
- Process of accessing the funcitonality or data of other user accounts on a system, as opposed to gaining access to accounts with admin or root privs. Accessing or authorizing functionality on a system using accounts that are on the same user level of perms.
- You would do this if you're interested in accessing unprivileged user account data or in harvesting user account credentials or password hashes.

### VERTICAL
- Process of exploiting a vulnerability in an OS to gain root or admin access on a system. 

<img width="546" height="489" alt="image" src="https://github.com/user-attachments/assets/bac32bde-29a4-49c5-81f1-3474079b4b2a" />

```
It is common to find misconfiged systems and services that may allow non-admin users to run commands or binaries with admin perms.
```

<img width="733" height="283" alt="image" src="https://github.com/user-attachments/assets/29d6b50b-d464-4d4f-aaff-e77b8254ae9d" />

## Differences between Linux + Windows privesc
The difference between Windows and Linux boil down to their unique design philosphy.

<img width="729" height="277" alt="image" src="https://github.com/user-attachments/assets/74dfb930-521d-4b1a-9f0b-0d0b645e013f" />

### WINDOWS
- Much more user centered design (UCD)
- User auth on Windows is handled by the WINDOWS LOGON (Winlogon) process + SECURITY ACCOUNT MANAGER (SAM). SAM is a database that is used to manage and store user accounts on Windows systems.
- Modern Windows utilize the New Technology LAN Manager 2 (NTLM2) encryption protocol for password hashing and encryption, which is significantly strong than the LAN Manager (LM) encryption protocol in older versions of Windows.
- Authentication onto domains on Windows is typically facilitated by auth protocols such as Kerberos.
- The process of user identification on Windows utilizes a SECURITY IDENTIFIER (SID) for identification. Each user and group has a unique SID that consists of:

<img width="741" height="236" alt="image" src="https://github.com/user-attachments/assets/73178d82-ffd1-41d1-b9fe-bafbc635212c" />

SID String = inidicates that it's an SID string
Revision = Always set to 1; this refers to the structure revision number
Authroity ID = Specifies who created or granted the SID as follows:
- Null: 0
- World Authority: 1
- Local Authority: 2
- Creator Authority: 3
- Non-unique authority: 4
- NT Authority: 5
Subauthority ID / Actual ID = Unique ID for the user, or comprises the domain identifier
RelativeID (RID) = used in reference to other accounts to distinguish one user form another.

Windows will have the following unique RIDs assigned to specific users. It is important to be able to identify privileged users based on their SID as follows: 
- Administrator: 500
- Guest user: 501
- Domain administrator: 512
- Domain Computer: 515

You can enumerate the SIDs on a Windows system by running the following command in CMD:
```
wmic useraccount get name,sid
```
*^^^ REMOVED IN WINDOW 11*
Use in Powershell 5:
```
Get-LocalUser | Select-Object Name, SID
```
PAY CLOSE ATTENTION TO THE SIDS WHICH WILL QUICKLY IDENTIFY THE ADMIN AND GUEST ACCOUNTS.






