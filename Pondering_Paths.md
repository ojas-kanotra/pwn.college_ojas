# Pondering Paths

---

## The Root
The use of absolute path to open a file

### Solution
**Flag:** `pwn.college{ANqONht6ClS4bWI68ywT-tRTIXd.QX4cTO0wyM3kjNzEzW}`

```bash
command /pwn
pwn.college{ANqONht6ClS4bWI68ywT-tRTIXd.QX4cTO0wyM3kjNzEzW}
```

### New Learnings
- Absolute paths start from the root directory (/) and provide the complete path to a file
- Commands can be executed using their absolute path from any location
- Absolute paths are unambiguous and always point to the same location regardless of current directory

### References 
None

---

## Program And Absolute Paths
This challenge again required us to execute it by invoking its absolute path. We would have to execute the run file that is in the challenge directory that is, in turn, in the / directory

### Solution
**Flag:** `pwn.college{wJP8IujEZiTfQGMEHWmhneUruZr.QX1QTN0wyM3kjNzEzW}`

```bash
command /challenge/run
pwn.college{wJP8IujEZiTfQGMEHWmhneUruZr.QX1QTN0wyM3kjNzEzW}
```

### New Learnings
- The root directory (/) is the top-level directory in Linux filesystem hierarchy
- All files and directories in Linux are contained within the root directory
- Absolute paths always begin with / to indicate they start from the root
- The `/challenge/run` command demonstrates executing programs via absolute paths

### References 
None

---

## Position Thy Self
This challenge will required us to execute the /challenge/run program from a specific path. We had to cd to that directory before rerunning the challenge program

### Solution
**Flag:** `pwn.college{U2ZXDI2BsJwj9kMZNCKrryAxr5J.QX2QTN0wyM3kjNzEzW}`

```bash
command /challenge/run
command cd /usr/include
hacker@paths~position-thy-self:/usr/include$ /challenge/run
pwn.college{U2ZXDI2BsJwj9kMZNCKrryAxr5J.QX2QTN0wyM3kjNzEzW}
```

### New Learnings
- `cd` (change directory) command is used to navigate between directories
- Current working directory affects how relative paths are interpreted
- Some programs may require execution from specific directories
- Syntax: `cd /path/to/directory` to change to a specific location

### References 
None

---

## Position Elsewhere
This challenge required us to execute the /challenge/run program from a specific path. We had to cd to that directory before rerunning the challenge program.

### Solution
**Flag:** `pwn.college{Arewe6ZoipdT1gG5a-76f0_mSpP.QX3QTN0wyM3kjNzEzW}`

```bash
command /challenge/run
command cd /usr/bin
command /challenge/run
pwn.college{Arewe6ZoipdT1gG5a-76f0_mSpP.QX3QTN0wyM3kjNzEzW}
```

### New Learnings
- Reinforces the concept of changing directories with `cd`
- Demonstrates that different challenges may require execution from different paths
- Working directory context is crucial for proper program execution
- Similar pattern to Position Thy Self challenge

### References 
None

---

## Position Yet Elsewhere
This challenge required us to execute the /challenge/run program from a specific path. We had to cd to that directory before rerunning the challenge program.


### Solution
**Flag:** `pwn.college{EGxO8c-T0XSlE9Jaq5XmKGDrKAx.QX4QTN0wyM3kjNzEzW}`

```bash
command /challenge/run
command cd /var/log
command /challenge/run
pwn.college{EGxO8c-T0XSlE9Jaq5XmKGDrKAx.QX4QTN0wyM3kjNzEzW}
```

### New Learnings
- Continues the pattern of directory-dependent program execution
- Reinforces navigation skills with `cd` command
- Shows consistency in challenge structure and requirements
- Builds familiarity with changing working directories for different tasks

### References 
None

---

## Implicit Relative Paths, From /
We need to run /challenge/run using a relative path while having a current working directory of /

### Solution
**Flag:** `pwn.college{k4ME7s7RozotXz4EGgtlSX_WaBI.QX5QTN0wyM3kjNzEzW}`

```bash
command cd /
command challenge/run
pwn.college{k4ME7s7RozotXz4EGgtlSX_WaBI.QX5QTN0wyM3kjNzEzW}
```

### New Learnings
- Relative paths do not start with / and are interpreted relative to current directory
- When in root directory (/), `challenge/run` is equivalent to `/challenge/run`
- Relative paths provide flexibility and context-dependent navigation
- Understanding the difference between absolute and relative path notation

### References 
None

---

## Explicit Relative Paths, From /
To run /challenge/run using relative path in a specific directory

### Solution
**Flag:** `pwn.college{o98epbraDrKXVfYwQ8nEo62-80f.QXwUTN0wyM3kjNzEzW}`

```bash
command /
command ./challenge/run
pwn.college{o98epbraDrKXVfYwQ8nEo62-80f.QXwUTN0wyM3kjNzEzW}
```

### New Learnings
- The `.` symbol represents the current directory in relative paths
- `./challenge/run` explicitly indicates execution from current directory
- Explicit relative paths with `./` are clearer and more precise than implicit paths
- This notation distinguishes between system commands and local executables

### References 
None

---

## Implicit Relative Path
In this challenge, we'll learn how to explicitly use relative paths to launch run in this scenario. The way to do this is to tell Linux that you explicitly want to execute a program in the current directory, using . like in the previous levels.

### Solution
**Flag:** `pwn.college{4vFQNkOvl-GO4_rwopzh5caoF6p.QXxUTN0wyM3kjNzEzW}`

```bash
command cd /challenge
command ./run
pwn.college{4vFQNkOvl-GO4_rwopzh5caoF6p.QXxUTN0wyM3kjNzEzW}
```

### New Learnings
- Using `./` prefix prevents confusion between local executables and system commands
- Security best practice to explicitly specify current directory execution
- Avoids potential conflicts with commands in system PATH
- Makes intentions clear when executing local programs or scripts 

### References 
None

---

## Home Sweet Home
In this challenge, /challenge/run will write a copy of the flag to any file you specify as an argument on the commandline, with these constraints:

1. Your argument must be an absolute path.

2. The path must be inside your home directory.

3. Before expansion, your argument must be three characters or less.

Again, you must specify your path as an argument to /challenge/run

### Solution
**Flag:** `pwn.college{c79Vo_z227vdbHDGKMgdMkzbxgV.QXzMDO0wyM3kjNzEzW}`

```bash
command cd ~
command > l
command /challenge/run ~/l
pwn.college{c79Vo_z227vdbHDGKMgdMkzbxgV.QXzMDO0wyM3kjNzEzW}
```

### New Learnings
- `~` symbol is a shorthand notation for the user's home directory (/home/hacker)
- Bash automatically expands `~` to the full home directory path
- `cd` without arguments defaults to the home directory
- `> filename` creates an empty file (alternative to `touch` command)
- Home directory shortcuts improve efficiency in navigation and file operations

### References 
[How_to_create_an_empty_file](https://stackoverflow.com/questions/9381463/how-to-create-a-file-in-linux-from-terminal-window)