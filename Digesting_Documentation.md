#Digesting Documentation

## Learning from Documentation
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
The typical need you'll have for documentation is just to figure out how to use all these dang programs, and a specific case of that is figuring out what arguments to specify on the command line.
The correct usage of programs depends, in a large part, on the proper specification of arguments to them. Recall the -a of ls -a in the hidden files challenge of the Basic Commands module: that -a was an argument that told ls to list out hidden files as well as non-hidden files. Because we wanted to list out hidden files, invoking ls with the -a argument was the correct way to use it in our scenario.

### References 
None




## Learning complex usage
Here is this level's documentation for /challenge/challenge:

Welcome to the documentation for /challenge/challenge! This program allows you to print arbitrary files to the terminal, when given the --printfile argument. The argument to the --printfile argument is the path of the flag to read. For example, /challenge/challenge --printfile /challenge/DESCRIPTION.md will print out the description of the level!

### Solve
**Flag:** `pwn.college{wzWm1aHxkOoV-VbngUS1Xolqehk.QX1ITO0wyM3kjNzEzW}`

```bash
command /challenge/challenge --printfile /flag
pwn.college{wzWm1aHxkOoV-VbngUS1Xolqehk.QX1ITO0wyM3kjNzEzW}
```

### New Learnings
find has a -name argument, and the -name argument itself takes an argument specifying the name to search for. Many other commands are analogous.cd 

### References 
None





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
This level introduces the man command. man is short for manual, and will display (if available) the manual of the command you pass as an argument
Man command gives output in following format:

NAME(1)                           CATEGORY                          NAME(1)

NAME
	This gives the name (and short description) of the command or
	concept discussed by the page.

SYNOPSIS
	This gives a short usage synopsis. These synopses have a standard
	format. Typically, each line is a different valid invocation of the
	command, and the lines can be read as:

	COMMAND [OPTIONAL_ARGUMENT] SINGLE_MANDATORY_ARGUMENT
	COMMAND [OPTIONAL_ARGUMENT] MULTIPLE_ARGUMENTS...

DESCRIPTION
	Details of the command or concept, with detailed descriptions
	of the various options.

SEE ALSO
	Other man pages or online resources that might be useful.

COLLECTION                        DATE                          NAME(1)

We can hit q to quit when we are done

you run man yes to look up the yes manpage, rather than man /usr/bin/yes, which would be the actual path to the yes program but would result in man displaying garbage

### References 
None





## Searching Manulas
Find the option that will give you the flag by reading the challenge man page.

### Solve
**Flag:** `pwn.college{otsYqDGGtIpCbhg6lNIaEtUJFSj.QX1EDO0wyM3kjNzEzW}`



```bash
command man challenge
command /challenge/challenge --utuiqqp
pwn.college{otsYqDGGtIpCbhg6lNIaEtUJFSj.QX1EDO0wyM3kjNzEzW}
```

### New Learnings
You can scroll man pages with the arrow keys (and PgUp/PgDn) and search with /. After searching, you can hit n to go to the next result and N to go to the previous result. Instead of /, you can use ? to search backwards!

### References 
None





## Searching for Manuals
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
Brief note on what you learned from the challenge

### References 
None




## Helpful program
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




## Challenge Name
Add challenge description here

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
