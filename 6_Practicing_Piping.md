# Practicing Piping

---

## Redirecting Output
Use output redirection to write the word "PWN" to a file named "COLLEGE".

### Solve
**Flag:** `pwn.college{QtgTnqy52bUlGeLltuz0tY3eIdG.QX0YTN0wyM3kjNzEzW}`


```bash
command echo PWN > COLLEGE
pwn.college{QtgTnqy52bUlGeLltuz0tY3eIdG.QX0YTN0wyM3kjNzEzW}
```

### New Learnings
- **Output Redirection**: Redirect standard output (stdout) to files using the `>` character
- **Redirection Syntax**: Use `command > filename` to send command output to a file
- **File Creation**: Redirection automatically creates the target file if it doesn't exist
- **Content Replacement**: Using `>` overwrites existing file content completely
- **Example Usage**: `echo hi > asdf` redirects the output "hi" to the file "asdf"

### References 
None

---

## Redirecting More Output
Practice redirecting output from any command, not just `echo`, to capture program results in files.

### Solve
**Flag:** `pwn.college{A0XSkkO6pVyALJ6ialgUKDyQE7S.QX1YTN0wyM3kjNzEzW}`


```bash
command /challenge/run > myflag
command cat myflag
pwn.college{A0XSkkO6pVyALJ6ialgUKDyQE7S.QX1YTN0wyM3kjNzEzW}
```

### New Learnings
- **Universal Redirection**: Any command's output can be redirected, not just `echo`
- **General Syntax**: Use `command > file` pattern for any command
- **Program Output Capture**: Redirect complex program outputs to files for later analysis
- **File Storage**: Useful for saving command results, logs, or data for future reference
- **Workflow Integration**: Essential technique for building automated workflows and scripts

### References 
None

---

## Appending Output
Run `/challenge/run` with append-mode redirection to `/home/hacker/the-flag`. The program writes the first half of the flag to the file, then the second half to stdout. Use append mode (`>>`) to combine both parts, not truncate mode (`>`) which would overwrite the first half.

### Solve
**Flag:** `pwn.college{Ynmx4-QxJt3ggoeGwlBjo1ZgBdO.QX3ATO0wyM3kjNzEzW}`

```bash
command /challenge/run > /home/hacker/the-flag
command /challenge/run >> /home/hacker/the-flag
command cat /home/hacker/the-flag
pwn.college{Ynmx4-QxJt3ggoeGwlBjo1ZgBdO.QX3ATO0wyM3kjNzEzW}
```

### New Learnings
- **Truncation vs Append**: `>` overwrites file contents completely, while `>>` appends to existing content
- **Append Mode Benefits**: `>>` allows accumulating output from multiple commands in the same file
- **Workflow Applications**: Often used to aggregate multiple command outputs for later analysis with tools like `grep`
- **Content Preservation**: Using `>>` prevents accidental loss of previous command outputs
- **Sequential Operations**: Essential for building logs or collecting data from multiple program runs
- **File Content Management**: Understanding when to truncate vs append is crucial for proper file handling

### References 
None

---

## Redirecting Errors
Redirect both standard output and standard error to separate files. Send `/challenge/run` output to `myflag` and errors (instructions) to `instructions`. Nothing will print to the terminal since all output is redirected.

### Solve
**Flag:** `pwn.college{EEmPGxs3M7kHTzt9zjXzoY-f0Do.QX3YTN0wyM3kjNzEzW}`


```bash
command /challenge/run > myflag 2> instructions
command cat myflag
pwn.college{EEmPGxs3M7kHTzt9zjXzoY-f0Do.QX3YTN0wyM3kjNzEzW}
```

### New Learnings
- **File Descriptors**: A File Descriptor (FD) is a number that describes a communication channel in Linux
- **Standard Input (FD 0)**: The default input source, typically keyboard input
- **Standard Output (FD 1)**: The default output destination, typically terminal display
- **Standard Error (FD 2)**: The default error message destination, typically terminal display
- **Error Redirection Syntax**: Use `2>` to redirect standard error to a file
- **Separate Stream Control**: Ability to redirect stdout and stderr to different destinations simultaneously

### References 
None

---

## Redirecting Input
Create a file named "PWN" containing "COLLEGE", then redirect this file as input to `/challenge/run`.

### Solve
**Flag:** `pwn.college{wYcF16ihpayq4uc6A3MAM-Wjd5F.QXwcTN0wyM3kjNzEzW}`

```bash
command echo COLLEGE > PWN
command /challenge/run < PWN
pwn.college{wYcF16ihpayq4uc6A3MAM-Wjd5F.QXwcTN0wyM3kjNzEzW}
```

### New Learnings
- **Input Redirection**: Just like output redirection, you can redirect input to programs using the `<` operator
- **Input Source Control**: Allows programs to read from files instead of keyboard input
- **File as Input**: Use `command < filename` to feed file contents as input to a command
- **Automation Benefits**: Essential for automating programs that normally require interactive input
- **Data Pipeline**: Forms the foundation for creating data processing pipelines

### References 
None

---

## Grepping Stored Results
Redirect `/challenge/run` output to `/tmp/data.txt`, then use `grep` to find the flag among the hundred thousand lines of text.

### Solve
**Flag:** `pwn.college{McRktwC9DsBN_UKvjXPbeolaFdF.QX4EDO0wyM3kjNzEzW}`


```bash
command /challenge/run 1> /tmp/data.txt
command grep pwn. /tmp/data.txt
pwn.college{McRktwC9DsBN_UKvjXPbeolaFdF.QX4EDO0wyM3kjNzEzW}
```

### New Learnings
- **Two-Step Process**: Combines output redirection with pattern searching for complex data analysis
- **Large File Handling**: Demonstrates handling large amounts of output data efficiently
- **File Descriptor Specificity**: Using `1>` explicitly specifies standard output redirection
- **Data Storage and Analysis**: Shows the workflow of capturing data first, then analyzing it
- **Grep Integration**: Combines file operations with text searching for practical problem-solving

### References 
None

---

## Grepping Live Output
Use piping to search through `/challenge/run` output in real-time without storing it to a file first.

### Solve
**Flag:** `pwn.college{oYUy-XEgF94Uf1eDz4F6CVfceV9.QX5EDO0wyM3kjNzEzW}`


```bash
command /challenge/run | grep pwn.
pwn.college{oYUy-XEgF94Uf1eDz4F6CVfceV9.QX5EDO0wyM3kjNzEzW}
```

### New Learnings
- **Pipe Operator**: The `|` (pipe) operator connects command output directly to another command's input
- **Real-Time Processing**: Eliminates the need to store intermediate results in files
- **Stream Connection**: Standard output from left command becomes standard input for right command
- **Efficiency Benefits**: Saves disk space and processing time by avoiding temporary files
- **Command Chaining**: Foundation for building complex command pipelines for data processing
- **Memory Streaming**: Data flows through memory rather than being written to disk

### References 
None

---

## Grepping Errors
The flag is output to standard error this time. Use redirection techniques to pipe stderr through `grep` to find the flag.

### Solve
**Flag:** `pwn.college{Y9BLr8eOXdUKWB40WJzCkmiGpy4.QX1ATO0wyM3kjNzEzW}`


```bash
command /challenge/run 2>& 1 | grep pwn.
pwn.college{Y9BLr8eOXdUKWB40WJzCkmiGpy4.QX1ATO0wyM3kjNzEzW}
```

### New Learnings
- **File Descriptor Redirection**: The `>` operator redirects file descriptors to files, `2>` redirects stderr
- **Pipe Limitation**: The `|` operator only redirects stdout, there's no `2|` for stderr
- **File Descriptor Merging**: The `>&` operator redirects one file descriptor to another file descriptor
- **Two-Step Error Piping**: First redirect stderr to stdout (`2>&1`), then pipe the combined stream (`|`)
- **Stream Merging**: Combining stderr and stdout allows both to be processed by the same pipeline
- **Advanced Redirection**: Essential technique for processing error messages through text processing tools


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
**Flag:** `pwn.college{c1Eaas59PxTtYBIB0ZuDZUZYcZ4.QXwgDN1wyM3kjNzEzW}`


```bash
command /challenge/hack | tee >(/challenge/the) >(/challenge/planet)
pwn.college{c1Eaas59PxTtYBIB0ZuDZUZYcZ4.QXwgDN1wyM3kjNzEzW}
```

### New Learnings
- Now you've learned that process substitution can make command output appear as files for reading with <(command)
- tee to duplicate data to a file and a command and 
- bash can make commands look like files using process substitution! For writing to a command (output process substitution), use >(command). If you write an argument of >(rev), bash will run the rev command (this command reads data from standard input, reverses its order, and writes it to standard output!), but hook up its input to a temporary named pipe file

### References 
None

---

## Split-piping stderr and stdout
In this challenge, you have:

/challenge/hack: this produces data on stdout and stderr
/challenge/the: you must redirect hack's stderr to this program
/challenge/planet: you must redirect hack's stdout to this program

### Solve
**Flag:** `pwn.college{kSrPaa156Wlqy_gCx6NaRR4M7cR.QXxQDM2wyM3kjNzEzW}`


```bash
command  /challenge/hack 2> >(/challenge/the) | /challenge/planet
pwn.college{kSrPaa156Wlqy_gCx6NaRR4M7cR.QXxQDM2wyM3kjNzEzW}
```

### New Learnings
- | operator links the stdout of the left command with the stdin of the right command

### References 
None

---

## Named pipes
This challenge will be a simple introduction to FIFOs. You'll need to create a /tmp/flag_fifo file and redirect the stdout of /challenge/run to it. If you're successful, /challenge/run will write the flag into the FIFO! Go do it!

HINT: The blocking behavior of FIFOs makes it hard to solve this challenge in a single terminal. You may want to use the Desktop or VSCode mode for this challenge so that you can launch two terminals.

### Solve
**Flag:** `pwn.college{sLm6xZfupUk2vfkEUf9lUWNQZsZ.01MzMDOxwyM3kjNzEzW}`


```bash
command mkfifo /tmp/flag_fifo
command /challenge/run > /tmp/flag_fifo
command cat /tmp/flag_fifo 
pwn.college{sLm6xZfupUk2vfkEUf9lUWNQZsZ.01MzMDOxwyM3kjNzEzW}
```

### New Learnings
- A FIFO is a special kind of file that acts like a pipe, but you create it yourself and it stays on your filesystem until you delete it.
- You can make one using the command mkfifo my_pipe. This creates a named pipe called "my_pipe".
- When you list files (ls -l), the FIFO shows a "p" at the start of its permissions (e.g., prw-r--r--) instead of a dash (-) like normal files.
- FIFOs let processes communicate by writing to and reading from the pipe file, much like a direct channel.
- The key thing: FIFOs block operations until both writing and reading ends are connected. If you try to write but no one is reading, the write waits; if you try to read but no one is writing, the read waits.

Unlike regular files, FIFOs:

- Lose the data as soon as it's read (no persistent content).
- Automatically synchronize communication between processes (readers and writers wait for each other).
- Can be used to build complex data flows and support multiple writers and readers.

### References 
None
---