# Chaining Commands

## Chaining with Semicolons
Run commands sequentially regardless of their exit status using `;` between them.

### Solve
**Flag:** `pwn.college{UwiXlmoYoNzuqiei2ZijZw2r_LS.QX1UDO0wyM3kjNzEzW}`

```bash
/challenge/pwn; /challenge/college
pwn.college{UwiXlmoYoNzuqiei2ZijZw2r_LS.QX1UDO0wyM3kjNzEzW}
```

### New Learnings
- `;` runs multiple commands in sequence regardless of each exit status.
- Use semicolons for short sequences; prefer scripts for longer workflows.

```bash
# example:
echo first; echo second
```

### References 
None

## Building on Success
Use `&&` to run a follow-up command only if the previous command succeeded.

### Solve
**Flag:** `pwn.college{0Zd2beMJcuk0NmpewBfimP1Momw.0lM0MDOxwyM3kjNzEzW}`

```bash
/challenge/first-success && /challenge/second
pwn.college{0Zd2beMJcuk0NmpewBfimP1Momw.0lM0MDOxwyM3kjNzEzW}
```

### New Learnings
- `&&` runs the right-hand command only if the left-hand command exits with 0 (success).
- Great for chaining dependent steps (e.g., compile && run).

```bash
# example:
true && echo will-run
```

### References 
None

## Handling Failure
Use `||` to run a recovery or fallback command when the previous command fails.

### Solve
**Flag:** ` pwn.college{4pbOvS7jvbmBJtf6oQwUMePiLIv.01M0MDOxwyM3kjNzEzW}`

```bash
command /challenge/first-failure || /challenge/second
 pwn.college{4pbOvS7jvbmBJtf6oQwUMePiLIv.01M0MDOxwyM3kjNzEzW}
```

### New Learnings
- `||` executes the right-hand command only if the left-hand command fails (non-zero exit).
- Combine `&&` and `||` to build simple conditional flows without scripts.

```bash
# example:
false || echo recovered
```

### References 
None

## Your First Shell Script
Create a shell script file, make it executable, or run it with `bash script.sh` to automate tasks.

### Solve
**Flag:** `pwn.college{EjhLJZULWVyKdX8KU4YhzYFVM8Q.QXxcDO0wyM3kjNzEzW}`

```bash
command echo '/challenge/pwn' > x.sh; echo '/challenge/college' >> x.sh
command bash x.sh
pwn.college{EjhLJZULWVyKdX8KU4YhzYFVM8Q.QXxcDO0wyM3kjNzEzW}
```

### New Learnings
- Scripts are plain-text lists of shell commands—make them executable (`chmod +x`) or run with `bash script.sh`.
- Use scripts to encapsulate multi-step tasks and to avoid long one-liners.

```bash
# example:
echo -e '#!/bin/bash\necho Hello' > script.sh; chmod +x script.sh; ./script.sh
```

### References 
None

## Redirecting Script Output
Pipe a script's stdout into other commands (e.g., `bash script.sh | grep ...`) to compose workflows.

### Solve
**Flag:** `pwn.college{khI2RnKATid8CFWUfgQlr3DtKUc.QX4ETO0wyM3kjNzEzW}`

```bash
command echo '/challenge/pwn' > script.sh; echo '/challenge/college' >> script.sh
command bash script.sh | /challenge/solve
pwn.college{khI2RnKATid8CFWUfgQlr3DtKUc.QX4ETO0wyM3kjNzEzW}
```

### New Learnings
- Scripts produce stdout like any command; pipe it into other tools to filter or transform output.
- Piping lets you compose small tools into larger workflows (unix philosophy).

```bash
# example:
bash script.sh | grep pwn
```

### References 
None

## Executable Shell Scripts
Make scripts executable (`chmod +x`) and rely on the shebang when running them directly.

### Solve
**Flag:** `pwn.college{Afh-erehrfNlgFLIlSNuSS-_yr3.QX0cjM1wyM3kjNzEzW}`

```bash
command echo '/challenge/solve' > script.sh
command chmod u=rwx ./script.sh
command ./script.sh
pwn.college{Afh-erehrfNlgFLIlSNuSS-_yr3.QX0cjM1wyM3kjNzEzW}
```

### New Learnings
- `chmod +x` makes a script executable; the shebang (`#!`) tells the kernel which interpreter to use.
- When running `./script`, the kernel invokes the shebang interpreter with the script as an argument.

```bash
# example:
chmod u+x script.sh; ./script.sh
```

### References 
None

## Understanding Shebangs
Place a shebang (`#!/bin/bash`) as the first line so the kernel invokes the right interpreter.

### Solve
**Flag:** `Flag: pwn.college{wOl1RGNYJB0oCmddqHUL2kBUH8J.0VOzMDOxwyM3kjNzEzW}`

```bash
command echo '#!/bin/bash 
"hack the planet"' > /home/hacker/solve.sh
comamnd chmod +x /home/hacker/solve.sh
Flag: pwn.college{wOl1RGNYJB0oCmddqHUL2kBUH8J.0VOzMDOxwyM3kjNzEzW}
```

### New Learnings
- The shebang must be the very first line (`#!/bin/bash`); it selects the interpreter when running the script directly.
- For portability, prefer `#!/usr/bin/env bash` to find bash on different systems.

```bash
# example:
echo -e '#!/bin/bash\necho hi' > say.sh; chmod +x say.sh; ./say.sh
```

### References 
None

## Scripting with Arguments
Use `$1`, `$2`, etc., to accept positional parameters in scripts; `$#` gives argument count.

### Solve
**Flag:** `pwn.college{sd4_b4WHNoKwUR8SSmF085H3hW-.0VNzMDOxwyM3kjNzEzW}`

```bash
command echo '#!/bin/bash
echo "$2 $1"' > /home/hacker/solve.sh
command chmod +x /home/hacker/solve.sh
command /challenge/run
pwn.college{sd4_b4WHNoKwUR8SSmF085H3hW-.0VNzMDOxwyM3kjNzEzW}
```

### New Learnings
- `$1`, `$2`, ... are positional parameters; `$0` is the script name and `$#` is argument count.
- Quote expansions like `"$1"` to preserve whitespace in arguments.

```bash
# example:
./script.sh hello world    # $1=hello, $2=world
```

### References 
None

## Scripting with Conditionals
Use `if [ ... ]; then ... fi` (note spaces) to branch script behavior based on conditions.

### Solve
**Flag:** `pwn.college{MNqruUAvAu7d2-25_awxA7HCDO7.0lNzMDOxwyM3kjNzEzW}`

```bash
command echo '#!/bin/bash
> if [ "$1" == "pwn" ]
> then
> echo "college"
> fi
> ' > /home/hacker/solve.sh
command /challenge/run
pwn.college{MNqruUAvAu7d2-25_awxA7HCDO7.0lNzMDOxwyM3kjNzEzW}
```

### New Learnings
- Use `if [ "expr" ]; then ... fi` for branching; spaces around `[` and `]` are required.
- Use `elif` and `else` for multiple branches and always close with `fi`.

```bash
# example:
if [ "$1" == "ping" ]; then echo pong; fi
```

### References 
None

## Scripting with Default Cases
Add `else` to provide default behavior when no condition matches.

### Solve
**Flag:** `pwn.college{whs0cU5NaMPw4djuZMWcKE5yUwz.01NzMDOxwyM3kjNzEzW}`

```bash
command echo '#!/bin/bash
if [ $1 == "pwn" ]
then
echo "college"
else
echo "nope"
fi
' > /home/hacker/solve.sh
command /challenge/run
pwn.college{whs0cU5NaMPw4djuZMWcKE5yUwz.01NzMDOxwyM3kjNzEzW}
```

### New Learnings
- `else` provides a fallback branch; always quote variables in tests to avoid syntax errors.

```bash
# example:
if [ "$1" == "hello" ]; then echo Hi; else echo No; fi
```

### References 
None

## Scripting with Multiple Conditions
Chain `elif` blocks to test multiple exclusive conditions; the first true branch runs.

### Solve
**Flag:** `pwn.college{helloworld}`

```bash
command echo '#!/bin/bash
if [ $1 == "hack" ]
then
echo "the planet"
elif [ $1 == "pwn" ]
then
echo "college"
elif [ $1 == "learn" ]
then
echo "linux"
else
echo "unknown"
fi
' > /home/hacker/solve.sh
command /challenge/run
pwn.college{wfMiPJ5sN7pdYd_iGuwxyWQEQBI.0FOzMDOxwyM3kjNzEzW}
```

### New Learnings
- `elif` lets you test multiple mutually-exclusive conditions; script evaluates top-to-bottom and stops at the first true branch.

```bash
# example:
if [ "$1" == "a" ]; then echo A; elif [ "$1" == "b" ]; then echo B; fi
```

### References 
None

## Reading Shell Scripts
Always `cat` or inspect scripts before running them to understand what they'll do.

### Solve
**Flag:** `pwn.college{Q80iERWq1UC0IpbuivdUB1H8v2m.0lMwgDOxwyM3kjNzEzW}`

```bash
command /challenge/run
pwn.college{Q80iERWq1UC0IpbuivdUB1H8v2m.0lMwgDOxwyM3kjNzEzW}
```

### New Learnings
- Review a script's contents with `cat` before running it, especially if it runs as root or modifies system state.
- Prefer reading over blind execution to avoid surprises.

```bash
# example:
cat script.sh
```

### References 
None