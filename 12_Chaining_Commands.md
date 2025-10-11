# Chaining Commands

## Chaining with Semicolons

### Solve
**Flag:** `pwn.college{UwiXlmoYoNzuqiei2ZijZw2r_LS.QX1UDO0wyM3kjNzEzW}`

```bash
/challenge/pwn; /challenge/college
pwn.college{UwiXlmoYoNzuqiei2ZijZw2r_LS.QX1UDO0wyM3kjNzEzW}
```

### New Learnings
- Use of semicolon to chain commands sequentially

### References 
None

## Building on Success

### Solve
**Flag:** `pwn.college{0Zd2beMJcuk0NmpewBfimP1Momw.0lM0MDOxwyM3kjNzEzW}`

```bash
/challenge/first-success && /challenge/second
pwn.college{0Zd2beMJcuk0NmpewBfimP1Momw.0lM0MDOxwyM3kjNzEzW}
```

### New Learnings
- The && operator allows you to run a second command only if the first command succeeds

### References 
None

## Handling Failure

### Solve
**Flag:** ` pwn.college{4pbOvS7jvbmBJtf6oQwUMePiLIv.01M0MDOxwyM3kjNzEzW}`

```bash
command /challenge/first-failure || /challenge/second
 pwn.college{4pbOvS7jvbmBJtf6oQwUMePiLIv.01M0MDOxwyM3kjNzEzW}
```

### New Learnings
- || operator allows you to run a second command only if the first command fails

### References 
None

## Your First Shell Script

### Solve
**Flag:** `pwn.college{EjhLJZULWVyKdX8KU4YhzYFVM8Q.QXxcDO0wyM3kjNzEzW}`

```bash
command echo '/challenge/pwn' > x.sh; echo '/challenge/college' >> x.sh
command bash x.sh
pwn.college{EjhLJZULWVyKdX8KU4YhzYFVM8Q.QXxcDO0wyM3kjNzEzW}
```

### New Learnings
- We can create a shell script called pwn.sh (by convention, shell scripts are frequently named with a sh suffix)
- And then we can execute by passing it as an argument to a new instance of our shell

### References 
None

## Redirecting Script Output

### Solve
**Flag:** `pwn.college{khI2RnKATid8CFWUfgQlr3DtKUc.QX4ETO0wyM3kjNzEzW}`

```bash
command echo '/challenge/pwn' > script.sh; echo '/challenge/college' >> script.sh
command bash script.sh | /challenge/solve
pwn.college{khI2RnKATid8CFWUfgQlr3DtKUc.QX4ETO0wyM3kjNzEzW}
```

### New Learnings
Brief note on what you learned from the challenge

### References 
None

## Executable Shell Scripts

### Solve
**Flag:** `pwn.college{Afh-erehrfNlgFLIlSNuSS-_yr3.QX0cjM1wyM3kjNzEzW}`

```bash
command echo '/challenge/solve' > script.sh
command chmod u=rwx ./script.sh
command ./script.sh
pwn.college{Afh-erehrfNlgFLIlSNuSS-_yr3.QX0cjM1wyM3kjNzEzW}
```

### New Learnings
- When you invoke bash script.sh, you are, of course launching the bash command with the script.sh argument. This tells bash to read its commands from script.sh instead of standard input, and thus your shell script is executed.
- It turns out that you can avoid the need to manually invoke bash
- If your shell script file is executable (recall File Permissions), you can simply invoke it via its relative or absolute path

### References 
None

## Understanding Shebangs

### Solve
**Flag:** `Flag: pwn.college{wOl1RGNYJB0oCmddqHUL2kBUH8J.0VOzMDOxwyM3kjNzEzW}`

```bash
command echo '#!/bin/bash 
"hack the planet"' > /home/hacker/solve.sh
comamnd chmod +x /home/hacker/solve.sh
Flag: pwn.college{wOl1RGNYJB0oCmddqHUL2kBUH8J.0VOzMDOxwyM3kjNzEzW}
```

### New Learnings
- When a program is invoked in Linux, the Linux kernel first inspects the file to determine how it should be run. This does NOT use the extension
- (which is why you don't have to name your shell scripts with a .sh extension, or your Python scripts with a .py extension, or so on). Rather, Linux looks at the first few bytes of the file for this information.
- There are a bunch of different types of programs, but if the program file starts with the characters #! (often termed a "shebang")
- Linux treats the file as an interpreted program, and the contents of the rest of the line as the path to the interpreter
- When ./script.sh was executed, Linux opened the file, read the first line, extracted /bin/bash as the interpreter, and executed /bin/bash ./script.sh to launch the script
- Note, the shebang line must be the VERY FIRST line of the file - no blank lines or spaces before it!
- FUN FACT: Common shebangs you might see:
    - #!/bin/bash for bash scripts
    - #!/usr/bin/python3 for Python scripts
    - #!/bin/sh for POSIX shell scripts --- this is a more primitive predecessor to bash with fewer features, but more compatibility to non-Linux systems!
- Use -e after echo to make it read the escape characters otherwise it doesn't work

### References 
None

## Scripting with Arguments

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
- The script can access these arguments using special variables:

    - $1 contains the first argument ("hello")
    - $2 contains the second argument ("world")
    - $3 would contain the third argument (if there had been one)

Here's a simple example:

```bash
hacker@dojo:~$ cat myscript.sh
#!/bin/bash
echo "First argument: $1"
echo "Second argument: $2"
hacker@dojo:~$ bash myscript.sh hello world
First argument: hello
Second argument: world
hacker@dojo:~$
```

### References 
None

## Scripting with Conditionals

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
- In bash, you can use if statements
- First, you must have spaces after if (if you're used to a language like C, this is different), after [, and before ]
- Second, if, then, and fi must all be on different lines (or separated by semicolons)
- instead of endif or end or something like that, the terminator of the if statement is fi (if backwards)

```bash
if [ "$1" == "ping" ]
then
    echo "pong"
fi
```

### References 
None

## Scripting with Default Cases

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

```bash
if [ "$1" == "hello" ]
then
    echo "Hi there!"
else
    echo "I don't understand"
fi
```

### References 
None

## Scripting with Multiple Conditions

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
```bash
if [ "$1" == "one" ]
then
    echo "1"
elif [ "$1" == "two" ]
then
    echo "2"
elif [ "$1" == "three" ]
then
    echo "3"
else
    echo "unknown"
fi
```

### References 
None

## Reading Shell Scripts

### Solve
**Flag:** `pwn.college{Q80iERWq1UC0IpbuivdUB1H8v2m.0lMwgDOxwyM3kjNzEzW}`

```bash
command /challenge/run
pwn.college{Q80iERWq1UC0IpbuivdUB1H8v2m.0lMwgDOxwyM3kjNzEzW}
```

### New Learnings
None

### References 
None