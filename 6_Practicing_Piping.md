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

## Filtering With Grep -v
`/challenge/run` prints the real flag along with many decoy flags that contain the word "DECOY". Filter out lines containing "DECOY" using `grep -v` to reveal the real flag.

### Solve
**Flag:** `pwn.college{A22sVrnGTPew1x1AXzDFi5XWUlR.0FOxEzNxwyM3kjNzEzW}`

```bash
command /challenge/run | grep -v DECOY
pwn.college{A22sVrnGTPew1x1AXzDFi5XWUlR.0FOxEzNxwyM3kjNzEzW}
```

### New Learnings
- **Invert Match (-v)**: `grep -v PATTERN` shows lines that do *not* match PATTERN (inverse of normal `grep` behavior).
- **Practical Filtering**: Use `command | grep -v PATTERN` to remove unwanted lines (e.g., decoys) from a stream.
- **Combine Safely**: Pair `grep -v` with `grep`, `sort`, or `uniq` for multi-stage filtering (e.g., remove decoys then find the specific flag).
- **Exact vs Partial Matching**: Quote patterns when they contain special characters or spaces to avoid shell expansion and get exact matches.

### References 
None

---

## Duplicating Piped Data With Tee
Pipe `/challenge/pwn` into `/challenge/college` while intercepting the stream with `tee` so you can inspect the data as it flows.

### Solve
**Flag:** `pwn.college{YgOzIx0CUHluifThcV5s4Xsesq_.QXxITO0wyM3kjNzEzW}`

```bash
command  /challenge/pwn | tee intercepted_data.txt | /challenge/college
command /challenge/pwn --secret YgOzIx0C | tee intercepted_data.txt | /challenge/college
pwn.college{YgOzIx0CUHluifThcV5s4Xsesq_.QXxITO0wyM3kjNzEzW}
```

### New Learnings
- **Tee Duplicates Streams**: `tee` copies piped input to stdout and also writes it to one or more files: `command | tee file1 file2`.
- **Debugging Pipelines**: Use `tee` to inspect intermediate data in a pipeline without interrupting the flow to downstream commands.
- **Multiple Destinations**: `tee` lets you both save a copy to disk and continue piping to the next command.
- **Non-destructive Inspection**: Useful when you need to log or view data in-flight while still delivering it to the final consumer.

### References 
None

---

## Process Substitution For Input
Compare the outputs of two commands using `diff` and process substitution. Use `<(command)` to treat each command's output as a file for `diff`.

### Solve
**Flag:** `pwn.college{s0xOPOmtdcEoYzASRYoCUGiT_5k.0lNwMDOxwyM3kjNzEzW}`


```bash
command diff <(/challenge/print_decoys) <(/challenge/print_decoys_and_flag)
> pwn.college{s0xOPOmtdcEoYzASRYoCUGiT_5k.0lNwMDOxwyM3kjNzEzW}
```

### New Learnings
- **Process Substitution Overview**: `<(command)` runs `command` and provides its output via a temporary file-like handle (named pipe) that other commands can read.
- **Compare Streams Directly**: Use `diff <(cmd1) <(cmd2)` to compare command outputs without creating intermediate files.
- **Named Pipe Interface**: The shell exposes the command output as `/dev/fd/N` (a file descriptor path) for the duration of the command.
- **Cleaner Workflows**: Process substitution keeps the filesystem cleaner and avoids race conditions from manually creating temporary files.
- **When to Use**: Ideal when tools expect filenames but you want to supply dynamically generated content.

### References 
None

---

## Writing To Multiple Programs
Run `/challenge/hack` and feed its output simultaneously as input to both `/challenge/the` and `/challenge/planet` by combining `tee` with output process substitution.

### Solve
**Flag:** `pwn.college{c1Eaas59PxTtYBIB0ZuDZUZYcZ4.QXwgDN1wyM3kjNzEzW}`


```bash
command /challenge/hack | tee >(/challenge/the) >(/challenge/planet)
pwn.college{c1Eaas59PxTtYBIB0ZuDZUZYcZ4.QXwgDN1wyM3kjNzEzW}
```

### New Learnings
- **Output Process Substitution**: `>(cmd)` runs `cmd` and provides a filename that accepts data written into the command's stdin (useful for writing to commands as if they were files).
- **Combine `tee` and `>(...)`**: Use `command | tee >(cmd1) >(cmd2)` to send the same stream to multiple consuming commands.
- **Flexible Topologies**: Process substitution allows building complex pipelines where output can be routed to multiple commands without temporary files.
- **Tool Compatibility**: Useful when target commands accept filenames rather than reading from stdin.

### References 
None

---

## Split-Piping Stderr And Stdout
`/challenge/hack` produces data on both stdout and stderr. Redirect stderr to `/challenge/the` and stdout to `/challenge/planet` so each program receives the correct stream.

### Solve
**Flag:** `pwn.college{kSrPaa156Wlqy_gCx6NaRR4M7cR.QXxQDM2wyM3kjNzEzW}`


```bash
command  /challenge/hack 2> >(/challenge/the) | /challenge/planet
pwn.college{kSrPaa156Wlqy_gCx6NaRR4M7cR.QXxQDM2wyM3kjNzEzW}
```

### New Learnings
- **Stdout Piping**: The `|` operator routes the left command's stdout into the right command's stdin.
- **Redirecting Specific Streams**: Use `2> >(...)` to send stderr into a process substitution or `2>file` to send it to a file, while piping stdout normally.
- **Split Topology**: Combining redirections with process substitution enables routing stderr and stdout to different consumers simultaneously.
- **Practical Use**: Useful for separating informational output from error messages when feeding different handlers.

### References 
None

---

## Named Pipes
Create a FIFO (named pipe) at `/tmp/flag_fifo` and redirect `/challenge/run` stdout into it. Then read the FIFO from another process to receive the flag.

### Solve
**Flag:** `pwn.college{sLm6xZfupUk2vfkEUf9lUWNQZsZ.01MzMDOxwyM3kjNzEzW}`


```bash
command mkfifo /tmp/flag_fifo
command /challenge/run > /tmp/flag_fifo
command cat /tmp/flag_fifo 
pwn.college{sLm6xZfupUk2vfkEUf9lUWNQZsZ.01MzMDOxwyM3kjNzEzW}
```

### New Learnings
- **What a FIFO Is**: A FIFO (named pipe) is a special filesystem entry that behaves like a pipe but has a persistent name (created with `mkfifo`).
- **Creation and Identification**: Create one with `mkfifo /tmp/flag_fifo`. `ls -l` shows a leading `p` in the permission string for FIFOs.
- **Blocking Behavior**: Reads and writes block until both ends are connected—writers wait for readers and vice versa.
- **Transient Data**: Data sent through a FIFO is not stored persistently; it is consumed by readers and disappears.
- **Use Cases**: Useful for coordinating between two processes (e.g., producer writes into FIFO, consumer reads from it) without temporary files.

### References 
None
---