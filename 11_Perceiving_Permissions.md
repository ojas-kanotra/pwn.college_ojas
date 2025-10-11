# Perceiving Permissions

- You can check out the permissions of a file or directory using ls -l. Let's make some files and look at their permissions
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
Change the ownership of /flag to the hacker user using chown, then read it.

### Solve
**Flag:** `pwn.college{gQpb_uZS8BCtPYl4BsLuAo8_1ma.QXxEjN0wyM3kjNzEzW}`

```bash
command chown hacker /flag
command cat /flag
pwn.college{gQpb_uZS8BCtPYl4BsLuAo8_1ma.QXxEjN0wyM3kjNzEzW}
```

### New Learnings
- On a shared system (such as in a computer lab), there might be many people with different user accounts, all with their own files in their own home directories. But even on a non-shared system (such as your personal PC), Linux still has many "service" user accounts for different tasks.
- Interestingly, we can change the ownership of files! This is done via the chown (change owner) command
- chown [username] [file]

### References 
None

## Groups and Files
Change the group of /flag to one that allows reading, then read the flag.

### Solve
**Flag:** `pwn.college{UtZ_d1VzWTXiGa9jc5B0ffMXNzq.QXxcjM1wyM3kjNzEzW}`

```bash
command chgrp hacker /flag
command cat /flag
pwn.college{UtZ_d1VzWTXiGa9jc5B0ffMXNzq.QXxcjM1wyM3kjNzEzW}
```

### New Learnings
- You can check what groups you are part of with the id command
- Here, the hacker user is only in the hacker group. The most common use-case for groups is to control access to different system resources
- A typical main user of a typical Linux desktop has a lot of groups
- group ownership can be changed with the chgrp (change group) command! - Unless you have write access to the file and membership in the new group, this typically requires root access. 

### References 
None

## Fun with Groups Names
Use id to find your group name, then chgrp to change /flag's group for reading.

### Solve
**Flag:** `pwn.college{MHx_lJvQKSpaKkWDvinsjxE50cU.QXycjM1wyM3kjNzEzW}`

```bash
command id
command chgrp grp22721 /flag
command cat /flag
pwn.college{MHx_lJvQKSpaKkWDvinsjxE50cU.QXycjM1wyM3kjNzEzW}
```

### New Learnings
- every user has their own group, but this does not have to be the case
- For example, many computer labs will put all of their users into a single, shared users group.

### References 
None

## Changing Permissions
Follow the prompts from /challenge/run to set permissions on /challenge/pwn correctly eight times to unlock /flag.

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

### References 
None

## Executable Files
Make /challenge/run executable with chmod, then run it for the flag.

### Solve
**Flag:** `pwn.college{4EZ40kFGOSxYzL4THtOE__dV1Qr.QXyEjN0wyM3kjNzEzW}`

```bash
command chmod o+x /challenge/run
command /challenge/run
pwn.college{4EZ40kFGOSxYzL4THtOE__dV1Qr.QXyEjN0wyM3kjNzEzW}
```

### New Learnings
- When you invoke a program, such as /challenge/run, Linux will only actually execute it if you have execute-access to the program file

### References 
None

## Permission Tweaking Practice
Use chmod to make /flag readable and get the flag.

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
- The three digits in chmod always go in this order: owner - group - others
- Read	    r	4
- Write	    w	2
- Execute	x	1

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
- In addition to adding and removing permissions, as in the previous level, chmod can also simply set permissions altogether, overwriting the old ones. This is done by using = instead of - or +
- u=rw sets read and write permissions for the user, and wipes the execute permission
- o=x sets only executable permissions for the world, wiping read and write
- a=rwx sets read, write, and executable permissions for the user, group, and world!
- Even run multiples chmod u=rw,g=r /challenge/pwn
- You can zero out permission with dash(-) chmod u=rw,g=r,o=- /challenge/pwn

### References 
None

## The Suid Bit
Set the SUID bit on /challenge/getroot with chmod to run it as root and get the flag.

### Solve
**Flag:**  `pwn.college{oKyFHeo498EY537VT0WGPpAmOhk.QXzEjN0wyM3kjNzEzW}`

```bash
command chmod u+s /challenge/getroot
command /challenge/getroot
pwn.college{oKyFHeo498EY537VT0WGPpAmOhk.QXzEjN0wyM3kjNzEzW}
```

### New Learnings
SUID (set-user-ID) is a special permission that makes an executable run with the file owner’s privileges (often root), useful for controlled elevation but dangerous if set on insecure programs.

### References 
None
