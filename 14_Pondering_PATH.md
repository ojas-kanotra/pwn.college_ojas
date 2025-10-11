# Pondering PATH

Thus far, you have invoked commands in several ways:

Through an absolute path (e.g., /challenge/run).
Through a relative path (e.g., ./run).
Through a bare command name (e.g., ls).

We know the absolute way or relative way of locating -- the first and second option however in the third one all the scritps are located in PATH

## The PATH Variable
The PATH Variable

### Solve
**Flag:** `pwn.college{8miN9eTLg4xAGhzTSythdMTC9i8.QX2cDM1wyM3kjNzEzW}`

```bash
command PATH=""
command /challenge/run
pwn.college{8miN9eTLg4xAGhzTSythdMTC9i8.QX2cDM1wyM3kjNzEzW}
```

### New Learnings
- It turns out that the answer to "How does the shell find ls?" is fairly simple. There is a special shell variable, called PATH, that stores a bunch of directory paths in which the shell will search for programs corresponding to commands. If you blank out the variable, things go badly
```bash
hacker@dojo:~$ ls
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$ PATH=""
hacker@dojo:~$ ls
bash: ls: No such file or directory
hacker@dojo:~$
```

### References 
None

## Setting Path
Local Binaries

### Solve
**Flag:** `pwn.college{MEB3crs9X3WAYAhayU7J7ntj3Xy.QX1cjM1wyM3kjNzEzW}`

```bash
command PATH=/challenge/more_commands
command  /challenge/run
pwn.college{MEB3crs9X3WAYAhayU7J7ntj3Xy.QX1cjM1wyM3kjNzEzW}
```

### New Learnings
- PATH stores a list of directories to find commands in and, for commands in nonstandard places, we must typically execute them via their path
- An example is adding goodscript to the PATH
```bash
hacker@dojo:~$ PATH=/home/hacker/scripts
hacker@dojo:~$ goodscript
YEAH! This is the best script!
hacker@dojo:~$
```

### References 
None

## Finding Commands
In this challenge, we added a win command somewhere in your $PATH, but it won't give you the flag. Instead, it's in the same directory as a flag file that we made readable by you

### Solve
**Flag:** `pwn.college{YpmyNTx_qZdjnSZLPFyt_3E1ywh.01NzEzNxwyM3kjNzEzW}`

```bash
command which win
command cat /challenge/paths/13317/flag
pwn.college{YpmyNTx_qZdjnSZLPFyt_3E1ywh.01NzEzNxwyM3kjNzEzW}
```

### New Learnings
- You can find out with the aptly-named which command:
- Mirroring what the shell does when searching for commands, which looks at each directory in $PATH in order and prints the first file it finds whose name matches the argument you passed.

### References 
None

## Adding Commands
Hint: /challenge/run runs as root and will call win. Thus, win can simply cat the flag file. Again, the win command is the only thing that /challenge/run needs, so you can just overwrite PATH with that one directory. But remember, if you do that, your win command won't be able to find cat.

You have three options to avoid that:

- Figure out where the cat program is on the filesystem. It must be in a directory that lives in the PATH variable, so you can print the variable out (refer to Shell Variables to remember how!), and go through the directories in it (recall that the different entries are separated by :), find which one has cat in it, and invoke cat by its absolute path.
- Set a PATH that has the old directories plus a new entry for wherever you create win.
- Use read (again, refer to Shell Variables) to read /flag. Since read is a builtin functionality of bash, it is unaffected by PATH shenanigans.

### Solve
**Flag:** `pwn.college{4j4NuKlZyAAfGABToqtdi0MGT1e.QX2cjM1wyM3kjNzEzW}`

```bash
command echo '#!/bin/bash
FLAG=$(</flag)
echo $FLAG
' > win
command chmod 777 ~/win
command PATH=~/
comamnd /challenge/run
pwn.college{4j4NuKlZyAAfGABToqtdi0MGT1e.QX2cjM1wyM3kjNzEzW}
```
echo '#!/bin/bash 
FLAG=$(</flag)
read FLAG
' > win
### New Learnings
Use of previous knowledge

### References 
None

## Hijacking Commands
The PATH Variable 2

### Solve
**Flag:** `pwn.college{helloworld}`

```bash
command 1
command 2
pwn.college{helloworld}
```

### New Learnings
Brief note on what you learned from the challenge

### References 
None
