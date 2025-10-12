# Pondering PATH

Thus far, you have invoked commands in several ways:

Through an absolute path (e.g., /challenge/run).
Through a relative path (e.g., ./run).
Through a bare command name (e.g., ls).

We know the absolute way or relative way of locating -- the first and second option however in the third one all the scritps are located in PATH

## The PATH Variable
PATH is a colon-separated list of directories the shell searches for commands invoked by name; clearing it makes bare names fail.

### Solve
**Flag:** `pwn.college{8miN9eTLg4xAGhzTSythdMTC9i8.QX2cDM1wyM3kjNzEzW}`

```bash
command PATH=""
command /challenge/run
pwn.college{8miN9eTLg4xAGhzTSythdMTC9i8.QX2cDM1wyM3kjNzEzW}
```

### New Learnings
- **What PATH is**: PATH is a colon-separated list of directories the shell searches to find commands invoked by name.
- **Effect of empty PATH**: clearing `PATH` makes bare command names unavailable (e.g., `ls` → "No such file or directory").
- **Order matters**: the shell searches PATH entries left-to-right and uses the first matching executable.

```bash
# examples:
echo $PATH
PATH=""; which ls || echo not-found
```

### References 
None

## Setting Path
Temporarily prepend or export directories into `PATH` (e.g., `PATH=~/bin:$PATH; export PATH`) to call local scripts by name.

### Solve
**Flag:** `pwn.college{MEB3crs9X3WAYAhayU7J7ntj3Xy.QX1cjM1wyM3kjNzEzW}`

```bash
command PATH=/challenge/more_commands
command  /challenge/run
pwn.college{MEB3crs9X3WAYAhayU7J7ntj3Xy.QX1cjM1wyM3kjNzEzW}
```

### New Learnings
- **Modify PATH**: set `PATH=/some/dir:$PATH` (or temporarily `PATH=/some/dir command`) to include custom command locations.
- **Local scripts**: adding `~/bin` or `/home/user/scripts` to PATH makes personal utilities callable by name.
- **Security caution**: do not put `.` (current dir) at the front of PATH — it can enable accidental execution of malicious programs.

```bash
# examples:
PATH=~/bin:$PATH
export PATH
```

### References 
None

## Finding Commands
Use `which` or `type -a` to locate the first executable matching a name and inspect whether it's an alias, builtin, or external program.

### Solve
**Flag:** `pwn.college{YpmyNTx_qZdjnSZLPFyt_3E1ywh.01NzEzNxwyM3kjNzEzW}`

```bash
command which win
command cat /challenge/paths/13317/flag
pwn.college{YpmyNTx_qZdjnSZLPFyt_3E1ywh.01NzEzNxwyM3kjNzEzW}
```

### New Learnings
- **which**: `which cmd` prints the path to the first matching executable found in PATH.
- **how shell finds commands**: the shell searches each PATH directory in order for an executable file with the command name.
- **Inspect before run**: use `which` or `type` to see whether a name is an alias, builtin, or external command.

```bash
# examples:
which win
type -a ls
```

### References 
None

## Adding Commands
When adding a custom command directory to PATH, include system dirs or call system binaries by absolute path to avoid breaking required tools.

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
- **Builtins vs external**: shell builtins (like `read`) run without referencing PATH; external commands require PATH lookup.
- **Safe PATH overrides**: include system directories in PATH when adding custom dirs, or invoke required system binaries by absolute path.
- **Privilege note**: when programs run as another user (e.g., root), PATH and builtins behave according to that user's environment and shell.

```bash
# example:
/bin/cat /flag    # invoke cat via absolute path when PATH is overridden
```

### References 
None

## Hijacking Commands
Placing an executable earlier in `PATH` can hijack common command names; prefer absolute paths for critical binaries and avoid '.' at the front of PATH.

### Solve
**Flag:** `pwn.college{helloworld}`

```bash
command 1
command 2
pwn.college{helloworld}
```

### New Learnings
- **Command hijacking**: placing a malicious executable earlier in PATH can cause innocent-looking commands to run your code—beware when modifying PATH.
- **Defenses**: prefer full paths for critical binaries, avoid `.` in PATH, and check `which`/`type` before trusting a command.

```bash
# example:
which ls
type ls
```

### References 
None