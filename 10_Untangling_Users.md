# Untangling Users

- There are MANY users on a typical Linux system! The full list of users on a Linux system is specified in the /etc/passwd file
- A lot of users here, and a lot of info! Each line contains, separated by :s, the username, an x as a placeholder for where the password used to be, the numerical user ID, the numerical default group ID, long-form user details, the home directory, and the default shell.
-  the nobody user is used to ensure that, e.g., some programs run without any special privileges
- One important user is root: the system administrator
- A very frequent goal of hackers breaking into systems is to escalate to root, and thus root must be defended at all cost!


## Becoming Root with Su
Use `su` (with the target password) to switch to root and access root-owned files.

### Solve
**Flag:** `pwn.college{M5okMpqof_jySKMdlXBD1935MTm.QX1UDN1wyM3kjNzEzW}`

```bash
command su
command cat not-the-flag
pwn.college{M5okMpqof_jySKMdlXBD1935MTm.QX1UDN1wyM3kjNzEzW}
```

### New Learnings
- **Root user**: `root` is the system administrator account with unrestricted privileges.
- **su basics**: `su` switches user contexts (no args → root); provide a username to switch to that user.
- **Password-based elevation**: `su` typically requires the target user's password; modern systems often prefer `sudo`.
- **Privilege caution**: running as root bypasses many safety checks—use sparingly and with care.

### References 
None

## Other Users with Su
Switch to another user with `su username` (providing their password) to access user-scoped files.

### Solve
**Flag:** `pwn.college{8_DvDgL9HTWodU6OwTiLNYOFqsG.QX2UDN1wyM3kjNzEzW}`

```bash
command su zardus 
command /challenge/run
pwn.college{8_DvDgL9HTWodU6OwTiLNYOFqsG.QX2UDN1wyM3kjNzEzW}
```

### New Learnings
- **su with username**: `su username` switches to that user (asks for their password).
- **User-scoped access**: switching users helps access files and privileges available only to that account.

### References 
None

## Cracking Passwords
Extract leaked hashes (e.g., from a leaked `/etc/shadow`) and use cracking tools like `john` to recover weak passwords offline.

### Solve
**Flag:** `pwn.college{Q8YtHwMyVQX8pavHo-HMN1K8IdQ.QX3UDN1wyM3kjNzEzW}`

```bash
command john /challenge/shadow-leak
command su zardus
command /challenge/run
pwn.college{Q8YtHwMyVQX8pavHo-HMN1K8IdQ.QX3UDN1wyM3kjNzEzW}
```

### New Learnings
- **/etc/passwd vs /etc/shadow**: `/etc/passwd` lists users and metadata; sensitive password hashes live in `/etc/shadow` (not world-readable).
- **Password hashing**: passwords are stored as hashes; cracking tools (e.g., `john`) attempt to brute-force or dictionary-attack hashes.
- **Leaked shadow**: exposed shadow files allow offline cracking—serious security risk.
- **Authentication flow**: login utilities hash the presented password and compare it to the stored hash.

### References 
None

## Using Sudo
Use `sudo` to run individual commands with elevated privileges according to policy (check `/etc/sudoers`).

### Solve
**Flag:** `pwn.college{UPdwz52ow6qCpbLZ0Rsg8NXUDbr.QX4UDN1wyM3kjNzEzW}`

```bash
command sudo /flag
pwn.college{UPdwz52ow6qCpbLZ0Rsg8NXUDbr.QX4UDN1wyM3kjNzEzW}
```

### New Learnings
- **sudo vs su**: `sudo` runs commands with elevated privileges according to policy (no root password required if authorized).
- **Policies**: `sudo` behavior is controlled by `/etc/sudoers` (use `visudo` to edit safely).
- **Least privilege**: prefer `sudo` for single-command elevation instead of a full root shell.

### References 
None
