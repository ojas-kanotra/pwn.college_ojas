# Pondering Paths

---

## The Root
In this challenge, we'll learn about absolute paths by executing a program from the root directory. The program we need to run is located at /pwn, and we need to invoke it using its absolute path from the root directory (/).

### Solution
**Flag:** `pwn.college{ANqONht6ClS4bWI68ywT-tRTIXd.QX4cTO0wyM3kjNzEzW}`

```bash
command /pwn
pwn.college{ANqONht6ClS4bWI68ywT-tRTIXd.QX4cTO0wyM3kjNzEzW}
```

### New Learnings
- **Absolute Path Definition**: Absolute paths start from the root directory (/) and provide the complete path to a file or directory
- **Universal Access**: Commands can be executed using their absolute path from any location in the filesystem
- **Path Uniqueness**: Absolute paths are unambiguous and always point to the same location regardless of current directory
- **Root Directory**: The `/` symbol represents the root directory, which is the top-level directory in Linux filesystem

### References 
None

---

## Program And Absolute Paths
This challenge requires us to execute a program by invoking its absolute path. We need to execute the run file that is located in the challenge directory, which is in turn located in the root directory (/). This teaches us how to run programs using their complete absolute paths.

### Solution
**Flag:** `pwn.college{wJP8IujEZiTfQGMEHWmhneUruZr.QX1QTN0wyM3kjNzEzW}`

```bash
command /challenge/run
pwn.college{wJP8IujEZiTfQGMEHWmhneUruZr.QX1QTN0wyM3kjNzEzW}
```

### New Learnings
- **Filesystem Hierarchy**: The root directory (/) is the top-level directory in Linux filesystem hierarchy
- **Directory Structure**: All files and directories in Linux are contained within the root directory
- **Absolute Path Syntax**: Absolute paths always begin with `/` to indicate they start from the root
- **Program Execution**: The `/challenge/run` command demonstrates executing programs via absolute paths from any location
- **Path Navigation**: Understanding how directories are organized under the root directory structure

### References 
None

---

## Position Thy Self
This challenge requires us to execute the /challenge/run program from a specific directory. We need to use the cd command to navigate to the required directory before running the challenge program. This demonstrates how some programs may need to be executed from particular locations.

### Solution
**Flag:** `pwn.college{U2ZXDI2BsJwj9kMZNCKrryAxr5J.QX2QTN0wyM3kjNzEzW}`

```bash
command /challenge/run
command cd /usr/include
hacker@paths~position-thy-self:/usr/include$ /challenge/run
pwn.college{U2ZXDI2BsJwj9kMZNCKrryAxr5J.QX2QTN0wyM3kjNzEzW}
```

### New Learnings
- **CD Command**: The `cd` (change directory) command is used to navigate between directories in the filesystem
- **Working Directory Context**: Current working directory affects how relative paths are interpreted by the system
- **Directory-Dependent Programs**: Some programs may require execution from specific directories to function properly
- **CD Syntax**: Use `cd /path/to/directory` to change to a specific absolute location
- **Navigation Workflow**: Combining directory navigation with program execution for context-specific tasks

### References 
None

---

## Position Elsewhere
This challenge is similar to the previous one, but requires us to execute the /challenge/run program from a different specific directory. We need to cd to the new required directory before rerunning the challenge program.

### Solution
**Flag:** `pwn.college{Arewe6ZoipdT1gG5a-76f0_mSpP.QX3QTN0wyM3kjNzEzW}`

```bash
command /challenge/run
command cd /usr/bin
command /challenge/run
pwn.college{Arewe6ZoipdT1gG5a-76f0_mSpP.QX3QTN0wyM3kjNzEzW}
```

### New Learnings
- **CD Command Reinforcement**: Strengthens understanding of changing directories with the `cd` command
- **Variable Path Requirements**: Different challenges may require execution from different specific paths
- **Context Importance**: Working directory context is crucial for proper program execution and functionality
- **Pattern Recognition**: Similar workflow pattern to "Position Thy Self" challenge, building consistent navigation skills

### References 
None

---

## Position Yet Elsewhere
Once again, this challenge requires us to execute the /challenge/run program from yet another specific directory. We must cd to that directory before rerunning the challenge program. This reinforces the concept of directory-dependent program execution.


### Solution
**Flag:** `pwn.college{EGxO8c-T0XSlE9Jaq5XmKGDrKAx.QX4QTN0wyM3kjNzEzW}`

```bash
command /challenge/run
command cd /var/log
command /challenge/run
pwn.college{EGxO8c-T0XSlE9Jaq5XmKGDrKAx.QX4QTN0wyM3kjNzEzW}
```

### New Learnings
- **Pattern Continuation**: Continues the established pattern of directory-dependent program execution
- **Navigation Skill Building**: Further reinforces navigation skills with the `cd` command through practice
- **Challenge Consistency**: Demonstrates consistency in challenge structure and requirements across similar problems
- **Directory Familiarity**: Builds comfort and familiarity with changing working directories for various tasks

### References 
None

---

## Implicit Relative Paths From Root
Run `/challenge/run` using a relative path while your current working directory is the root directory (`/`).

### Solution
**Flag:** `pwn.college{k4ME7s7RozotXz4EGgtlSX_WaBI.QX5QTN0wyM3kjNzEzW}`

```bash
command cd /
command challenge/run
pwn.college{k4ME7s7RozotXz4EGgtlSX_WaBI.QX5QTN0wyM3kjNzEzW}
```

### New Learnings
- **Relative Path Definition**: Relative paths do not start with `/` and are interpreted relative to the current directory
- **Root Directory Context**: When in root directory (`/`), the relative path `challenge/run` is equivalent to absolute path `/challenge/run`
- **Path Flexibility**: Relative paths provide flexibility and context-dependent navigation capabilities
- **Path Type Distinction**: Understanding the fundamental difference between absolute and relative path notation
- **Context-Dependent Resolution**: How the same relative path can point to different locations based on current directory

### References 
None

---

## Explicit Relative Paths From Root
Run `/challenge/run` using an explicit relative path while in the root directory.

### Solution
**Flag:** `pwn.college{o98epbraDrKXVfYwQ8nEo62-80f.QXwUTN0wyM3kjNzEzW}`

```bash
command /
command ./challenge/run
pwn.college{o98epbraDrKXVfYwQ8nEo62-80f.QXwUTN0wyM3kjNzEzW}
```

### New Learnings
- **Current Directory Symbol**: The `.` symbol represents the current directory in relative path notation
- **Explicit Path Syntax**: `./challenge/run` explicitly indicates execution from the current directory
- **Path Clarity**: Explicit relative paths with `./` prefix are clearer and more precise than implicit relative paths
- **Command Disambiguation**: This notation distinguishes between system commands and local executables, preventing confusion
- **Best Practice**: Using `./` prefix is a security and clarity best practice in shell scripting

### References 
None

---

## Implicit Relative Path
Learn to use explicit relative paths to execute programs. Use the `.` symbol to tell Linux you want to execute a program in the current directory.

### Solution
**Flag:** `pwn.college{4vFQNkOvl-GO4_rwopzh5caoF6p.QXxUTN0wyM3kjNzEzW}`

```bash
command cd /challenge
command ./run
pwn.college{4vFQNkOvl-GO4_rwopzh5caoF6p.QXxUTN0wyM3kjNzEzW}
```

### New Learnings
- **Command Disambiguation**: Using `./` prefix prevents confusion between local executables and system commands
- **Security Best Practice**: Explicitly specifying current directory execution is a security best practice
- **PATH Conflict Avoidance**: Avoids potential conflicts with commands already available in system PATH
- **Clear Intent**: Makes intentions explicit and clear when executing local programs or scripts
- **Execution Safety**: Reduces risk of accidentally running unintended system commands with similar names 

### References 
None

---

## Home Sweet Home
The `/challenge/run` program will write the flag to a file you specify with these requirements:

1. Your argument must be an absolute path
2. The path must be inside your home directory  
3. Before expansion, your argument must be three characters or less

Provide your path as an argument to `/challenge/run`.

### Solution
**Flag:** `pwn.college{c79Vo_z227vdbHDGKMgdMkzbxgV.QXzMDO0wyM3kjNzEzW}`

```bash
command cd ~
command > l
command /challenge/run ~/l
pwn.college{c79Vo_z227vdbHDGKMgdMkzbxgV.QXzMDO0wyM3kjNzEzW}
```

### New Learnings
- **Home Directory Shortcut**: The `~` symbol is shorthand notation for the user's home directory (typically `/home/username`)
- **Bash Expansion**: Bash automatically expands `~` to the full home directory path during command execution
- **CD Default Behavior**: The `cd` command without arguments defaults to navigating to the home directory
- **File Creation**: `> filename` creates an empty file (alternative to the `touch` command)
- **Efficiency Benefits**: Home directory shortcuts improve efficiency in navigation and file operations
- **Path Length Constraints**: Understanding how shell expansion works with character length limitations

### References 
[How_to_create_an_empty_file](https://stackoverflow.com/questions/9381463/how-to-create-a-file-in-linux-from-terminal-window)