# Practicing Piping

## Redirecting output
In this challenge, you must use this output redirection to write the word PWN (all uppercase) to the filename COLLEGE (all uppercase).

### Solve
**Flag:** `pwn.college{QtgTnqy52bUlGeLltuz0tY3eIdG.QX0YTN0wyM3kjNzEzW}`


```bash
command echo PWN > COLLEGE
pwn.college{QtgTnqy52bUlGeLltuz0tY3eIdG.QX0YTN0wyM3kjNzEzW}
```

### New Learnings
- Redirecting stdout to files. You can accomplish this with the > character
- hacker@dojo:~$ echo hi > asdf
- This will redirect the output of echo hi (which will be hi) to the file asdf

### References 
None

---

## Redirecting more output
Add challenge description here

### Solve
**Flag:** `pwn.college{A0XSkkO6pVyALJ6ialgUKDyQE7S.QX1YTN0wyM3kjNzEzW}`


```bash
command /challenge/run > myflag
command cat myflag
pwn.college{A0XSkkO6pVyALJ6ialgUKDyQE7S.QX1YTN0wyM3kjNzEzW}
```

### New Learnings
- Aside from redirecting the output of echo, you can, of course, redirect the output of any command.
- command > file

### References 
None

---

## Appending output
To practice, run /challenge/run with an append-mode redirect of the output to the file /home/hacker/the-flag. The practice will write the first half of the flag to the file, and the second half to stdout if stdout is redirected to the file. If you properly redirect in append-mode, the second half will be appended to the first, but if you redirect in truncation mode (>), the second half will overwrite the first and you won't get the flag!

### Solve
**Flag:** `pwn.college{Ynmx4-QxJt3ggoeGwlBjo1ZgBdO.QX3ATO0wyM3kjNzEzW}`

```bash
command /challenge/run > /home/hacker/the-flag
command /challenge/run >> /home/hacker/the-flag
command cat /home/hacker/the-flag
pwn.college{Ynmx4-QxJt3ggoeGwlBjo1ZgBdO.QX3ATO0wyM3kjNzEzW}
```

### New Learnings
- > simply writes over the file
- >> appends to the file
- Often times, you want to do this in aggregate: run a bunch of commands, save their output, and grep through it later. In this case, you might want all that output to keep appending to the same file, but > will create a new output file every time, deleting the old contents.
- You can redirect input in append mode using >> instead of >

### References 
None

---

## Redirecting errors
In this challenge, you will need to redirect the output of /challenge/run, like before, to myflag, and the "errors" (in our case, the instructions) to instructions. You'll notice that nothing will be printed to the terminal, because you have redirected everything! You can find the instructions/feedback in instructions and the flag in myflag when you successfully pull this off!

### Solve
**Flag:** `pwn.college{EEmPGxs3M7kHTzt9zjXzoY-f0Do.QX3YTN0wyM3kjNzEzW}`


```bash
command /challenge/run > myflag 2> instructions
command cat myflag
pwn.college{EEmPGxs3M7kHTzt9zjXzoY-f0Do.QX3YTN0wyM3kjNzEzW}
```

### New Learnings
- A File Descriptor (FD) is a number that describes a communication channel in Linux
- FD 0: Standard Input
- FD 1: Standard Output
- FD 2: Standard Error

### References 
None

---

## Redirecting input
Practice using /challenge/run, which will require you to redirect the PWN file to it and have the PWN file contain the value COLLEGE!

### Solve
**Flag:** `pwn.college{wYcF16ihpayq4uc6A3MAM-Wjd5F.QXwcTN0wyM3kjNzEzW}`

```bash
command echo COLLEGE > PWN
command /challenge/run < PWN
pwn.college{wYcF16ihpayq4uc6A3MAM-Wjd5F.QXwcTN0wyM3kjNzEzW}
```

### New Learnings
- Just like you can redirect output from programs, you can redirect input to programs! This is done using <

### References 
None

---

## Grepping stored results
In preparation for more complex levels, we want you to:

- Redirect the output of /challenge/run to /tmp/data.txt.
- This will result in a hundred thousand lines of text, with one of them being the flag, in /tmp/data.txt.
- `grep` that for the flag!

### Solve
**Flag:** `pwn.college{McRktwC9DsBN_UKvjXPbeolaFdF.QX4EDO0wyM3kjNzEzW}`


```bash
command /challenge/run 1> /tmp/data.txt
command grep pwn. /tmp/data.txt
pwn.college{McRktwC9DsBN_UKvjXPbeolaFdF.QX4EDO0wyM3kjNzEzW}
```

### New Learnings
-

### References 
None

---

## Grepping live output
/challenge/run will output a hundred thousand lines of text, including the flag. grep for the flag!

### Solve
**Flag:** `pwn.college{oYUy-XEgF94Uf1eDz4F6CVfceV9.QX5EDO0wyM3kjNzEzW}`


```bash
command /challenge/run | grep pwn.
pwn.college{oYUy-XEgF94Uf1eDz4F6CVfceV9.QX5EDO0wyM3kjNzEzW}
```

### New Learnings
- It turns out that you can "cut out the middleman" and avoid the need to store results to a file 
- You can do this by using the | (pipe) operator
- Standard output from the command to the left of the pipe will be connected to (piped into) the standard input of the command to the right of the pipe

### References 
None

---

## Grepping errors
This time on standard error, grep through it to find the flag!

### Solve
**Flag:** `pwn.college{Y9BLr8eOXdUKWB40WJzCkmiGpy4.QX1ATO0wyM3kjNzEzW}`


```bash
command /challenge/run 2>& 1 | grep pwn.
pwn.college{Y9BLr8eOXdUKWB40WJzCkmiGpy4.QX1ATO0wyM3kjNzEzW}
```

### New Learnings
- The > operator redirects a given file descriptor to a file, and you've used 2> to redirect fd 2, which is standard error
- The | operator redirects only standard output to another program, and there is no 2| form of the operator!
- The shell has a >& operator, which redirects a file descriptor to another file descriptor. 
- This means that we can have a two-step process to grep through errors: 

First, we redirect standard error to standard output (2>& 1)

Then pipe the now-combined stderr and stdout as normal (|)


### References 
None

---

## Filtering With grep -v
/challenge/run will output the flag to stdout, but it will also output over 1000 decoy flags (containing the word DECOY somewhere in the flag) mixed in with the real flag. You'll need to filter out the decoys while keeping the real flag!

Use grep -v to filter out all the lines containing "DECOY" and reveal the real flag!

### Solve
**Flag:** `pwn.college{A22sVrnGTPew1x1AXzDFi5XWUlR.0FOxEzNxwyM3kjNzEzW}`

```bash
command /challenge/run | grep -v DECOY
pwn.college{A22sVrnGTPew1x1AXzDFi5XWUlR.0FOxEzNxwyM3kjNzEzW}
```

### New Learnings
- The grep command has a very useful option: -v (invert match). While normal grep shows lines that MATCH a pattern, grep -v shows lines that do NOT match a pattern

### References 
None

---

## Duplicating piped data with tee
Now, you try it! This process' /challenge/pwn must be piped into /challenge/college, but you'll need to intercept the data to see what pwn needs from you!

### Solve
**Flag:** `pwn.college{YgOzIx0CUHluifThcV5s4Xsesq_.QXxITO0wyM3kjNzEzW}`

```bash
command  /challenge/pwn | tee intercepted_data.txt | /challenge/college
command /challenge/pwn --secret YgOzIx0C | tee intercepted_data.txt | /challenge/college
pwn.college{YgOzIx0CUHluifThcV5s4Xsesq_.QXxITO0wyM3kjNzEzW}
```

### New Learnings
- You might want to see the data as it flows through between your commands to debug unintended outcomes (e.g., "why did that second command not work???")

- tee command, named after a "T-splitter" duplicates data flowing through your pipes to any number of files provided on the command line

```bash
hacker@dojo:~$ echo hi | tee pwn college
hi
hacker@dojo:~$ cat pwn
hi
hacker@dojo:~$ cat college
hi
hacker@dojo:~$
```

- As you can see, by providing two files to tee, we ended up with three copies of the piped-in data: one to stdout, one to the pwn file, and one to the college file.

### References 
None

---

## Process substitution for input
Now for your challenge! Recall what you learned in the diff challenge from Comprehending Commands. In that challenge, you diffed two files. Now, you'll diff two sets of command outputs: /challenge/print_decoys, which will print a bunch of decoy flags, and /challenge/print_decoys_and_flag which will print those same decoys plus the real flag.

Use process substitution with diff to compare the outputs of these two programs and find your flag!

### Solve
**Flag:** `pwn.college{s0xOPOmtdcEoYzASRYoCUGiT_5k.0lNwMDOxwyM3kjNzEzW}`


```bash
command diff <(/challenge/print_decoys) <(/challenge/print_decoys_and_flag)
> pwn.college{s0xOPOmtdcEoYzASRYoCUGiT_5k.0lNwMDOxwyM3kjNzEzW}
```

### New Learnings
- Sometimes you need to compare the output of two commands rather than two files. You might think to save each output to a file first:
- command1 > file1
- command2 > file2
- diff file1 file2
- Linux follows the philosophy that "everything is a file"
- That is, the system strives to provide file-like access to most resources, including the input and output of running programs
- We can hook input and output of programs to arguments of commands. This is done using Process Substitution
- For reading from a command (input process substitution), use <(command)
- When you write <(command), bash will run the command and hook up its output to a temporary file that it will create
- This isn't a real file, of course, it's what's called a named pipe, in that it has a file name
```bash
hacker@dojo:~$ echo <(echo hi)
/dev/fd/63
hacker@dojo:~$
```
- bash replaced <(echo hi) with the path of the named pipe file that's hooked up to the command's output! While the command is running, reading from this file will read data from the standard output of the command. Typically, this is done using commands that take input files as arguments like a cat command

### References 
None

---

## Writing to multiple programs
In this challenge, we have /challenge/hack, /challenge/the, and /challenge/planet. Run the /challenge/hack command, and duplicate its output as input to both the /challenge/the and the /challenge/planet commands! Scroll back through the previous challenges "Duplicating piped data with tee" and "Process substitution for input" if you need a refresher on this method

### Solve
**Flag:** `pwn.college{helloworld}`


```bash
command 1
command 2
pwn.college{helloworld}
```

### New Learnings
- Now you've learned that process substitution can make command output appear as files for reading with <(command)
- tee to duplicate data to a file and a command and 
- bash can make commands look like files using process substitution! For writing to a command (output process substitution), use >(command). If you write an argument of >(rev), bash will run the rev command (this command reads data from standard input, reverses its order, and writes it to standard output!), but hook up its input to a temporary named pipe file

### References 
None

---

## Split-piping stderr and stdout
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

---

## Named pipes
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

---