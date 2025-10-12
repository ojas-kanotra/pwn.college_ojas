# Chaining Commands

- Commands can be chained together using various operators to create more complex operations
```bash
hacker@dojo:~$ mkdir pwn_directory
hacker@dojo:~$ touch college_file
hacker@dojo:~$ ls -l
total 4
-rw-r--r-- 1 hacker hacker    0 May 22 13:42 college_file
drwxr-xr-x 2 hacker hacker 4096 May 22 13:42 pwn_directory
hacker@dojo:~$
```

- The first character of each line represents the file type
- The next nine characters are the actual access permissions of the file or directory, split into 3 characters denoting the permissions that the user who owns the file (termed the "owner") has to the file, 3 characters denoting the permissions that the group that owns the file (termed the "group") has to the file, and 3 characters denoting the permissions that all other access
- There are two columns showing the user that owns the file and then the group that owns the file

## Changing File Ownership
Change file owner with `chown user file` to transfer ownership and access rights.

### Solve
**Flag:** `pwn.college{gQpb_uZS8BCtPYl4BsLuAo8_1ma.QXxEjN0wyM3kjNzEzW}`

```bash
command chown hacker /flag
command cat /flag
pwn.college{gQpb_uZS8BCtPYl4BsLuAo8_1ma.QXxEjN0wyM3kjNzEzW}
```

### New Learnings
- chown changes a file's owner: `sudo chown user file` (root usually required to change owner).
- Ownership determines which user-level checks are used for access decisions.
- Verify owner with `ls -l` and use `stat filename` for full metadata.

```bash
# examples:
sudo chown hacker /flag      # make 'hacker' the owner of /flag
ls -l /flag                  # verify the owner and permissions
```

### References 
None

## Groups and Files
Change a file's group with `chgrp` to grant group-based access where appropriate.

### Solve
**Flag:** `pwn.college{UtZ_d1VzWTXiGa9jc5B0ffMXNzq.QXxcjM1wyM3kjNzEzW}`

```bash
command chgrp hacker /flag
command cat /flag
pwn.college{UtZ_d1VzWTXiGa9jc5B0ffMXNzq.QXxcjM1wyM3kjNzEzW}
```

### New Learnings
- Groups let multiple users share access: change group with `chgrp group file` or `sudo chgrp group file`.
- Check your groups with `id` or `id -nG`; group membership affects access checks.
- Only root (or file owner in some systems) can change a file's group to one you aren't a member of.

```bash
# examples:
id                      # show current user and groups
sudo chgrp hacker /flag  # change group ownership
ls -l /flag              # verify group and permissions
```

### References 
None

## Fun with Groups Names
List your groups (`id`) and use `chgrp` to set a group that has the desired permissions.

### Solve
**Flag:** `pwn.college{MHx_lJvQKSpaKkWDvinsjxE50cU.QXycjM1wyM3kjNzEzW}`

```bash
command id
command chgrp grp22721 /flag
command cat /flag
pwn.college{MHx_lJvQKSpaKkWDvinsjxE50cU.QXycjM1wyM3kjNzEzW}
```

### New Learnings
- Every user has one or more groups; `id -nG` lists group names.
- Use `chgrp` to change group ownership when appropriate; group ACLs control group access.

```bash
# example:
id -nG | tr ' ' '\n'   # list group names one-per-line for current user
```

### References 
None

## Changing Permissions
Use `chmod` (symbolic or octal) to add/remove read/write/execute bits and control access.

### Solve
**Flag:** `pwn.college{Iw30K7RlVrmMR9SnjFkpu2PvpE-.QXzcjM1wyM3kjNzEzW}`

```bash
command chmod o+r /flag
command cat /flag
pwn.college{Iw30K7RlVrmMR9SnjFkpu2PvpE-.QXzcjM1wyM3kjNzEzW}
```

### New Learnings
```bash 
ls -l
total 4
-rw-r--r-- 1 hacker hacker    0 May 22 13:42 college_file
drwxr-xr-x 2 hacker hacker 4096 May 22 13:42 pwn_directory
hacker@dojo:~$  
```
- The first character there is the file type. 
- The next nine characters are the actual access permissions of the file or directory, split into 3 characters denoting:
    - Permissions for the owning user
    - Permissions for the owning group
    - Permissions that all other access (e.g., by other users and other groups) has to the file.

- Each character of the three represent permission for a different type:

    - r - user/group/other can read the file (or list the directory)
    - w - user/group/other can modify the files (or create/delete files in the directory)
    - x - user/group/other can execute the file as a program (or can enter the directory, e.g., using `cd`)
    - - nothing 

- For college_file above, the rw-r--r-- permissions entry decodes to:

    - r: the user that owns the file (user hacker) can read it
    - w: the user that owns the file (user hacker) can write to it
    - -: the user that owns the file (user hacker) cannot execute it
    - r: users in the group that owns the file (group hacker) can read it
    - -: users in the group that owns the file (group hacker) cannot write to it
    - -: users in the group that owns the file (group hacker) cannot execute it
    - r: all other users can read it
    - -: all other users cannot write to it
    - -: all other users cannot execute it

- Like ownership, file permissions can also be changed. This is done with the chmod
- chmod [OPTIONS] MODE FILE
- chmod allows you to tweak permissions with the mode format of WHO+/-WHAT, where WHO is user/group/other and WHAT is read/write/execute.
    - u+r, as above, adds read access to the user's permissions
    - g+wx adds write and execute access to the group's permissions
    - o-w removes write access for other users
    - a-rwx removes all permissions for the user, group, and world

```bash
# common examples:
chmod o+r /flag        # add read for others
chmod u+x ./script.sh  # make script executable by owner
ls -l /flag            # verify mode
```

### References 
None

## Executable Files
Make scripts executable with `chmod +x` and run them; execute permission is required to run binaries.

### Solve
**Flag:** `pwn.college{4EZ40kFGOSxYzL4THtOE__dV1Qr.QXyEjN0wyM3kjNzEzW}`

```bash
command chmod o+x /challenge/run
command /challenge/run
pwn.college{4EZ40kFGOSxYzL4THtOE__dV1Qr.QXyEjN0wyM3kjNzEzW}
```

### New Learnings
- Execute permission is required to run a file (`chmod u+x file`);
- Running `./file` uses the current path; use a shebang to select the interpreter.

```bash
# example:
chmod u+x /challenge/run
./challenge/run
```

### References 
None

## Permission Tweaking Practice
Practice `chmod` with symbolic and octal modes to achieve the required permissions.

### Solve
**Flag:** `pwn.college{Uqz3mw0m6S1MThaaItZ79qHujRn.QXwEjN0wyM3kjNzEzW}`

```bash
command chmod 745 /challenge/pwn
command chmod 765 /challenge/pwn
command chmod 760 /challenge/pwn
command chmod 100 /challenge/pwn
command chmod 105 /challenge/pwn
command chmod 115 /challenge/pwn
command chmod 110 /challenge/pwn
command chmod 111 /challenge/pwn
command chmod 105 /flag
command cat /flag
pwn.college{Uqz3mw0m6S1MThaaItZ79qHujRn.QXwEjN0wyM3kjNzEzW}
```

### New Learnings
- Octal bits map: owner-group-others (e.g., `chmod 750 file` → u=rwx,g=rx,o=0).
- Use small, incremental changes (e.g., `chmod u+rx`) while verifying with `ls -l`.

```bash
# octal example:
chmod 755 ./script.sh   # rwxr-xr-x
```

### References 
- Learning reference chatgpt

## Permissions Setting Practice
Use advanced chmod syntax with = and , to set complex permissions on /flag.

### Solve
**Flag:** `pwn.college{geNoKGcjkl2m2mynryMgG9aylBx.QXzETO0wyM3kjNzEzW}`

```bash
command chmod u=r, g=rwx, w=- /challenge/pwn
command chmod u=r,g=rwx,o=- /challenge/pwn
command chmod u=-,g=-,o=-,u=x,o=r /challenge/pwn
command chmod u=-,g=-,o=-,u=rx,g=x,o=w /challenge/pwn
command chmod u=-,g=-,o=-,u=x,g=rx,o=r /challenge/pwn
command chmod u=-,g=-,o=-,u=rw,g=rw,o=rwx /challenge/pwn
command chmod u=-,g=-,o=-,g=rwx,o=r /challenge/pwn
command chmod u=-,g=-,o=-,u=x,g=rw,o=rwx /challenge/pwn  
command chmod u=-,g=-,o=-,u=r,o=r /challenge/pwn
command chmod u=r /flag
command cat /flag
pwn.college{geNoKGcjkl2m2mynryMgG9aylBx.QXzETO0wyM3kjNzEzW}
```

### New Learnings
- `chmod u=r,g=rw,o=r file` sets exact permissions (overwrite mode with `=`).
- Use `=` when you want to replace current permissions, `+`/`-` to modify.

## The Suid Bit
Set SUID (`chmod u+s`) to let an executable run with the owner's privileges—use with extreme caution.

### Solve
**Flag:** `pwn.college{oKyFHeo498EY537VT0WGPpAmOhk.QXzEjN0wyM3kjNzEzW}`

```bash
command chmod u+s /challenge/getroot
command /challenge/getroot
pwn.college{oKyFHeo498EY537VT0WGPpAmOhk.QXzEjN0wyM3kjNzEzW}
```

### New Learnings
- **SUID overview**: setting the SUID bit (`chmod u+s`) on an executable causes it to run with the file owner's privileges (commonly root) regardless of the invoking user.
- **Security implications**: SUID programs can be powerful escalation vectors; only trusted binaries should have this bit set.
- **Detection**: `ls -l` shows an `s` in the user-execute position when SUID is set (e.g., `rwsr-xr-x`).

```bash
# detect SUID files:
find / -perm -4000 -type f 2>/dev/null | head
```

### References 
None
