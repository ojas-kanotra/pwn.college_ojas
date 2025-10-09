# Data Manipulation

## Translating Characters
The /challenge/run program outputs the flag with all characters' case swapped (A becomes a, etc.). Use tr to correct the case and obtain the flag.

### Solve
**Flag:** `pwn.college{cdBOj9tyovExfljSNBLz3uYe9y_.01MxEzNxwyM3kjNzEzW}`

```bash
command /challenge/run | tr [A-Z,a-z] [a-z,A-Z]
pwn.college{cdBOj9tyovExfljSNBLz3uYe9y_.01MxEzNxwyM3kjNzEzW}
```

### New Learnings
- Many Linux commands will help you modify data in really cool ways
- One of these is tr, which translates characters it receives over standard input and prints them to standard output.
- tr translates the character provided in its first argument to the character provided in its second argument

### References 
None

## Deleting Characters
Decoy characters (^ and %) are mixed with the flag characters. Use tr -d to delete them and reveal the flag.

### Solve
**Flag:** `pwn.college{0fHEow_7KdcQDCbiWcKkUjh0c_-.0FNxEzNxwyM3kjNzEzW}`

```bash
command /challenge/run | tr -d [^,*,%]
pwn.college{0fHEow_7KdcQDCbiWcKkUjh0c_-.0FNxEzNxwyM3kjNzEzW}
```

### New Learnings
- tr can also translate characters to nothing (i.e., delete them)
- This is done via a -d flag and an argument of what characters to delete

### References 
None

## Deleting Newlines
Newlines have been inserted into the flag. Use tr -d with the escaped newline (\n) to remove them.

### Solve
**Flag:** `pwn.college{wJlj3TmYyIgIaPWbrb3QtsOs8Wk.0VNxEzNxwyM3kjNzEzW}`

```bash
command /challenge/run | tr -d "\n"
pwn.college{wJlj3TmYyIgIaPWbrb3QtsOs8Wk.0VNxEzNxwyM3kjNzEzW}
```

### New Learnings
- \n is a standin for this newline
- it must be in quotes to prevent the shell interpreter itself from trying to interpret it and pass it to tr instead
- Fun fact! Want to actually replace a backslash (\) character? Because \ is the escape character, you gotta escape it! \\ will be treated as a backslash by tr.

### References 
None

## Extracting the First Lines with Head
Pipe the output of /challenge/pwn through head to select the first 7 lines, then pipe to /challenge/college to get the flag.

### Solve
**Flag:** `pwn.college{8z-nttGabtoSImQFu6GwVsFqojT.0lNxEzNxwyM3kjNzEzW}`

```bash
command /challenge/pwn | head -n 7 | /challenge/college
pwn.college{8z-nttGabtoSImQFu6GwVsFqojT.0lNxEzNxwyM3kjNzEzW}
```

### New Learnings
- In your Linux journey, you'll experience situations where you need to grab just the early output of very verbose programs
- The head command is used to display the first few lines of its input
- By default, it shows the first 10 lines, but you can control this with the -n option
- `cat /something/very/long | head -n 2`

### References 
None

## Extracting Specific Sections of Text
The /challenge/run program outputs lines with random numbers and flag characters in columns. Use cut to extract the flag column, then tr -d '\n' to concatenate them.

### Solve
**Flag:** `pwn.college{YvttT4HaeFosE2q0vfmS8_Aftpa.01NxEzNxwyM3kjNzEzW}`

```bash
command /challenge/run | cut -d " " -f 2 | tr -d "\n"
pwn.college{YvttT4HaeFosE2q0vfmS8_Aftpa.01NxEzNxwyM3kjNzEzW}
```

### New Learnings
- Sometimes, you want to grab specific columns of data, such as the first column, the third column, or the 42nd column. For this, there's the cut command.
- -d argument specifies the column delimiter (how columns are separated)
- -f argument specifies the field number (which column to extract)
```bash
cat scores.txt
hacker 78 99 67
root 92 43 89

hacker@dojo:~$ cut -d " " -f 1 scores.txt
hacker
root
hacker@dojo:~$ cut -d " " -f 2 scores.txt
78
92
hacker@dojo:~$ cut -d " " -f 3 scores.txt
99
43
hacker@dojo:~$
```
- In this case -d the delimiter is a space character

### References 
None

## Sorting Data
The file /challenge/flags.txt contains 100 flags, with the real one at the end when sorted alphabetically. Use sort to find it.

### Solve
**Flag:** `pwn.college{UcIPiayy4TfZESEYLP8NRo85MNu.0FM0MDOxwyM3kjNzEzW}`

```bash
command sort /challenge/flags.txt
pwn.college{UcIPiayy4TfZESEYLP8NRo85MNu.0FM0MDOxwyM3kjNzEzW}
```

### New Learnings
- Files (or output lines of commands) aren't always in the order you need them! The sort command helps you organize data. It reads lines from input (or files) and outputs them in sorted orde
- By default, sort orders lines alphabetically. Arguments can change this:
- -r: reverse order (Z to A)
- -n: numeric sort (for numbers)
- -u: unique lines only (remove duplicates)
- -R: random order!

### References 
None
