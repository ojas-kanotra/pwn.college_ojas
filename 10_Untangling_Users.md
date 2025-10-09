# Untangling Users

- There are MANY users on a typical Linux system! The full list of users on a Linux system is specified in the /etc/passwd file
- A lot of users here, and a lot of info! Each line contains, separated by :s, the username, an x as a placeholder for where the password used to be, the numerical user ID, the numerical default group ID, long-form user details, the home directory, and the default shell.
-  the nobody user is used to ensure that, e.g., some programs run without any special privileges
- One important user is root: the system administrator
- A very frequent goal of hackers breaking into systems is to escalate to root, and thus root must be defended at all cost!


## Becoming Root with Su
Use su with the password 'hack-the-planet' to become root and read the flag.

### Solve
**Flag:** `pwn.college{M5okMpqof_jySKMdlXBD1935MTm.QX1UDN1wyM3kjNzEzW}`

```bash
command su
command cat not-the-flag
pwn.college{M5okMpqof_jySKMdlXBD1935MTm.QX1UDN1wyM3kjNzEzW}
```

### New Learnings
- It's not just hackers that need to become root. Oftentimes, you, as the owner of your computer, need to use root access to administer it
- We use su and sudo
- This is not typically used to elevate to root access anymore, but it is an elegant utility from a more civilized time
- Running as root, it can start a root shell
- Modern systems very rarely have root passwords, and different mechanisms

### References 
None

## Other Users with Su
Switch to the zardus user with password 'dont-hack-me' and run /challenge/run.

### Solve
**Flag:** `pwn.college{8_DvDgL9HTWodU6OwTiLNYOFqsG.QX2UDN1wyM3kjNzEzW}`

```bash
command su zardus 
command /challenge/run
pwn.college{8_DvDgL9HTWodU6OwTiLNYOFqsG.QX2UDN1wyM3kjNzEzW}
```

### New Learnings
- With no arguments, su will start a root shell 
- However, you can also give a username as an argument to switch to that user instead of root

### References 
None

## Cracking Passwords
Crack the leaked /etc/shadow file to get zardus' password, su to zardus, and run /challenge/run.

### Solve
**Flag:** `pwn.college{Q8YtHwMyVQX8pavHo-HMN1K8IdQ.QX3UDN1wyM3kjNzEzW}`

```bash
command john /challenge/shadow-leak
command su zardus
command /challenge/run
pwn.college{Q8YtHwMyVQX8pavHo-HMN1K8IdQ.QX3UDN1wyM3kjNzEzW}
```

### New Learnings
- When you enter a password for su, it compares it against the stored password for that user. 
- These passwords used to be stored in /etc/passwd, but because /etc/passwd is a globally-readable file, this is not good for passwords
- Hence these were moved to /etc/shadow
```bash
root:$6$s74oZg/4.RnUvwo2$hRmCHZ9rxX56BbjnXcxa0MdOsW2moiW8qcAl/Aoc7NEuXl2DmJXPi3gLp7hmyloQvRhjXJ.wjqJ7PprVKLDtg/:19921:0:99999:7:::
daemon:*:19873:0:99999:7:::
bin:*:19873:0:99999:7:::
sys:*:19873:0:99999:7:::
sync:*:19873:0:99999:7:::
games:*:19873:0:99999:7:::
man:*:19873:0:99999:7:::
zardus:$6$bEFkpM0w/6J0n979$47ksu/JE5QK6hSeB7mmuvJyY05wVypMhMMnEPTIddNUb5R9KXgNTYRTm75VOu1oRLGLbAql3ylkVa5ExuPov1.:19921:0:99999:7:::
```
- Separated by :s, the first field of each line is the username and the second is the password
- A value of * or ! functionally means that password login for the account is disabled, a blank field means that there is no password
- When you input a password into su, it one-way-encrypts (hashes) it and compares the result against the stored value. If the result matches, su grants you access to the user!
- If you have the hashed value of the password, you can crack it! Even though /etc/shadow is, by default, only readable by root, leaks can happen
- If a hacker gets their hands on a leaked /etc/shadow, they can start cracking passwords and wreaking havoc. The cracking can be done via the famous John the Ripper, as so

### References 
None

## Using Sudo
Use sudo to read the flag.

### Solve
**Flag:** `pwn.college{UPdwz52ow6qCpbLZ0Rsg8NXUDbr.QX4UDN1wyM3kjNzEzW}`

```bash
command sudo /flag
pwn.college{UPdwz52ow6qCpbLZ0Rsg8NXUDbr.QX4UDN1wyM3kjNzEzW}
```

### New Learnings
- in recent decades, the world has moved from administration via su to administration via sudo
- Unlike su, which relies on password authentication, sudo checks policies to determine whether the user is authorized to run commands as root.
- These policies are defined in /etc/sudoers

### References 
None
