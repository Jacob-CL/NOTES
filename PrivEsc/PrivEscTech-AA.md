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



