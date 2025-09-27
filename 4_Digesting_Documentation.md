# Digesting Documentation

---

## Learning From Documentation
The program for this challenge is /challenge/challenge, and you'll need to invoke it properly in order for it to give you the flag. Let's pretend that this is its documentation:
Welcome to the documentation for /challenge/challenge! To properly run this program, you will need to pass it the argument of --giveflag. Good luck!

### Solve
**Flag:** `pwn.college{olfzGqD62c47-nb6NbY7a1mP7b3.QX0ITO0wyM3kjNzEzW}`

```bash
command cd /challenge
command ./challenge --giveflag
pwn.college{olfzGqD62c47-nb6NbY7a1mP7b3.QX0ITO0wyM3kjNzEzW}
```

### New Learnings
- Documentation is essential for understanding program usage and available arguments
- Command-line arguments modify program behavior and functionality
- Proper argument specification is crucial for correct program execution
- Arguments like `--giveflag` are often documented in program help or manuals
- Reading documentation saves time and prevents trial-and-error approaches

### References 
None

---

## Learning Complex Usage
Here is this level's documentation for /challenge/challenge:

Welcome to the documentation for /challenge/challenge! This program allows you to print arbitrary files to the terminal, when given the --printfile argument. The argument to the --printfile argument is the path of the flag to read. For example, /challenge/challenge --printfile /challenge/DESCRIPTION.md will print out the description of the level!

### Solve
**Flag:** `pwn.college{wzWm1aHxkOoV-VbngUS1Xolqehk.QX1ITO0wyM3kjNzEzW}`

```bash
command /challenge/challenge --printfile /flag
pwn.college{wzWm1aHxkOoV-VbngUS1Xolqehk.QX1ITO0wyM3kjNzEzW}
```

### New Learnings
- Some arguments require additional parameters (argument to the argument)
- `--printfile` demonstrates arguments that take file paths as parameters
- Complex command patterns: `command --argument parameter`
- Understanding argument structure is key to using advanced program features
- Documentation provides examples of proper argument usage patterns 

### References 
None

---

## Reading Manuals
The challenge in this level has a secret option that, when you use it, will cause the challenge to print the flag. You must learn this option through the man page for challengemfind man 

### Solve
**Flag:** `pwn.college{E0tmYhucTK47BesYQ3PA5ZVQjOE.QX0EDO0wyM3kjNzEzW}`

```bash
command 
command /challenge/challenge --tmhuce 047
pwn.college{E0tmYhucTK47BesYQ3PA5ZVQjOE.QX0EDO0wyM3kjNzEzW}
```

### New Learnings
- `man` command displays manual pages for Linux commands and programs
- Manual pages have standardized format: NAME, SYNOPSIS, DESCRIPTION, SEE ALSO
- SYNOPSIS section shows command usage patterns and argument structure
- Use `man command_name` to access documentation (not full paths)
- Press `q` to quit the manual page viewer
- Manual pages are the primary source of official command documentation

### References 
None

---

## Searching Manuals
Find the option that will give you the flag by reading the challenge man page.

### Solve
**Flag:** `pwn.college{otsYqDGGtIpCbhg6lNIaEtUJFSj.QX1EDO0wyM3kjNzEzW}`

```bash
command man challenge
command /challenge/challenge --utuiqqp
pwn.college{otsYqDGGtIpCbhg6lNIaEtUJFSj.QX1EDO0wyM3kjNzEzW}
```

### New Learnings
- Navigate manual pages using arrow keys, PgUp/PgDn for scrolling
- Search within man pages using `/` followed by search term
- Use `n` for next search result, `N` for previous result
- Use `?` for backward search functionality
- These navigation skills are essential for efficiently finding information in long documentation

### References 
None

---

## Searching For Manuals
HINT 1: man man teaches you advanced usage of the man command itself, and you must use this knowledge to figure out how to search for the hidden manpage that will tell you how to use /challenge/challenge

HINT 2: though the manpage is randomly named, you still actually use /challenge/challenge to get the flag!

### Solve
**Flag:** `pwn.college{helloworld}`

```bash
command 1
command 2
pwn.college{helloworld}
```

### New Learnings
- Advanced manual navigation techniques using `man man`

### References 
None

---

## Helpful Program
You will practice reading a program's documentation with --help

### Solve
**Flag:** `pwn.college{I6Cw1JMR9JRLrmQLpjpVTtLM2sS.QX3IDO0wyM3kjNzEzW}`

I did trial and erorr and didn't notice there was anothe rarument needed after -g which was the number in place of GIVE_THE_FLAG 

```bash
command /challenge/challenge --help
command /challenge/challenge -p
command /challenge/challenge -g 619
pwn.college{I6Cw1JMR9JRLrmQLpjpVTtLM2sS.QX3IDO0wyM3kjNzEzW}
```

### New Learnings
Some programs don't have a man page, but might tell you how to run them if invoked with a special argument. Usually, this argument is --help, but it can often be -h or, in rare cases, -?, help

### References 
None

--

## Help For Bulletins
In this challenge, we'll practice using help to look up help for builtins. This challenge's challenge command is a shell builtin, rather than a program.

### Solve
**Flag:** `pwn.college{EUi0sy-oJvS8gZg6i25PpiJUWC5.QX0ETO0wyM3kjNzEzW}`

```bash
command help challenge
command challenge --secret EUi0sy-o
pwn.college{EUi0sy-oJvS8gZg6i25PpiJUWC5.QX0ETO0wyM3kjNzEzW}
```

### New Learnings
- You can get a list of shell builtins by running the builtin help
- You can get help on a specific one by passing it to the help builtin

### References 
None

--