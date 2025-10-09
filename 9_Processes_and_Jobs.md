# Processes and Jobs

## Listing Processes
The /challenge/run program is renamed and hidden from ls. Use ps to find its process and filename, then execute it to get the flag.

### Solve
**Flag:** `pwn.college{IQdgPKPSMRYwD_vDb3cGIQT2Ktu.QX4MDO0wyM3kjNzEzW}`

```bash
command ps aux
command /challenge/20101-run-8284
pwn.college{IQdgPKPSMRYwD_vDb3cGIQT2Ktu.QX4MDO0wyM3kjNzEzW}
```

### New Learnings
- To list running processes using the ps command
- ps either stands for "process snapshot" or "process status", and it lists processes
- ps just lists the processes running in your terminal, which honestly isn't very useful
- We have PID, which is a number that uniquely identifies every running process in a Linux environment
- We also see the total amount of cpu time that the process has eaten up so far
- As ps is a very old utility, its usage is a bit of a mess. There are two ways to specify arguments.
- "Standard" Syntax: in this syntax, you can use -e to list "every" process and -f for a "full format" output, including arguments. These can be combined into a single argument -ef.
- "BSD" Syntax: in this syntax, you can use a to list processes for all users, x to list processes that aren't running in a terminal, and u for a "user-readable" output. These can be combined into a single argument aux.
- These two methods, ps -ef and ps aux, result in slightly different, but cross-recognizable output
- There are many commonalities between ps -ef and ps aux: both display the user (USER column), the PID, the TTY, the start time of the process (STIME/START), the total utilized CPU time (TIME), and the command (CMD/COMMAND)
- ps -ef additionally outputs the Parent Process ID (PPID), which is the PID of the process that launched the one in question
- ps aux outputs the percentage of total system CPU and Memory that the process is utilizing.


### References 
None

## Killing Processes
Kill the running /challenge/dont_run process to allow /challenge/run to execute and provide the flag.

### Solve
**Flag:** `pwn.college{0tEXyNALA9uXh99u1OY9-s99IJG.QXyQDO0wyM3kjNzEzW}`

```bash
command ps aux | grep /challenge/dont_run
command kill 136
pwn.college{0tEXyNALA9uXh99u1OY9-s99IJG.QXyQDO0wyM3kjNzEzW}
```

### New Learnings
- You've launched processes, you've viewed processes, now you will learn to terminate processes
- kill will terminate a process in a way that gives it a chance to get its affairs in order before ceasing to exist
- You use kill to terminate it by passing the process identifier (the PID from ps) as an argument
- `ps -e | grep sleep` to get the sleep from list of ps

### References 
None

## Interrupting Processes
Interrupt the /challenge/run process with Ctrl-C to make it output the flag.

### Solve
**Flag:** `pwn.college{gVVWCJhaODNLIk_s1LBFUjCoqiy.QXzQDO0wyM3kjNzEzW}`

```bash
command /challenge/run
command ^C
pwn.college{gVVWCJhaODNLIk_s1LBFUjCoqiy.QXzQDO0wyM3kjNzEzW}
```

### New Learnings
- You've learned how to kill other processes with the kill command, but sometimes you just want to get rid of the process that's clogging up your terminal! 
- Ctrl-C (e.g., holding down the Ctrl key and pressing C) sends an "interrupt" to whatever application is waiting on input from the terminal and, typically, this causes the application to cleanly exit.

### References 
None

## Killing Misbehaving Processes
Kill the /challenge/decoy process to stop it from interfering, then run /challenge/run to get the flag.

### Solve
**Flag:** `pwn.college{o40pLxi8M52GaQKg0pNQucIsFIK.0FNzMDOxwyM3kjNzEzW}`

```bash
command ps aux | grep /challenge/decoy
command kill 142
command /challenge/run
command cat /tmp/flag_fifo
command cat /tmp/flag_fifo
pwn.college{o40pLxi8M52GaQKg0pNQucIsFIK.0FNzMDOxwyM3kjNzEzW}
```

### New Learnings
Brief note on what you learned from the challenge

### References 
None

## Suspending Processes
Launch /challenge/run, suspend it with Ctrl-Z, then launch another instance while the first is suspended.

### Solve
**Flag:** `pwn.college{Ibp9tzjyo4wKN3P1cdHabI1BbKO.QX1QDO0wyM3kjNzEzW}`

```bash
command /challenge/run
command ^Z
command /challenge/run
pwn.college{Ibp9tzjyo4wKN3P1cdHabI1BbKO.QX1QDO0wyM3kjNzEzW}
```

### New Learnings
- You have learned to interrupt processes with Ctrl-C, but there are less drastic measures you can use to get your terminal back! You can suspend processes to the background with Ctrl-Z
- When you pressed Ctrl-Z, you suspended the first instance of /challenge/run, which paused its execution and returned control to the shell. At that point, the first process was still alive — just stopped in the background.
- Then, when you ran /challenge/run a second time, two processes were now running in the same terminal session:

### References 
None

## Resuming Processes
Suspend /challenge/run with Ctrl-Z, then resume it with fg to get the flag.

### Solve
**Flag:** `pwn.college{YXAkynr0YsL3FsUDy-dyfBp5frZ.QX2QDO0wyM3kjNzEzW}`

```bash
command /challenge/run
command ^Z
command fg
pwn.college{YXAkynr0YsL3FsUDy-dyfBp5frZ.QX2QDO0wyM3kjNzEzW}
```

### New Learnings
- Your shell provides the fg command, a builtin that takes the suspended process, resumes it, and puts it back in the foreground of your terminal.

### References 
None

## Backgrounding Processes
Launch /challenge/run, suspend it, background it with bg, then launch another instance.

### Solve
**Flag:** `pwn.college{0Fi5p9ZHFN5zhQaX8TXQ8iRSKy0.QX3QDO0wyM3kjNzEzW}`

```bash
command /challenge/run
command ^Z
command bg
command /challenge/run
pwn.college{0Fi5p9ZHFN5zhQaX8TXQ8iRSKy0.QX3QDO0wyM3kjNzEzW}
```

### New Learnings
- You've resumed processes in the foreground with the fg command. You can also resume processes in the background with the bg command!
- This will allow the process to keep running, while giving you your shell back to invoke more commands in the meantime.

- To know the state we can run ps -o user,pid,stat,cmd
```bash
USER         PID STAT CMD
hacker       702 Ss   bash
hacker       762 T    sleep 1337
hacker       782 R+   ps -o user,pid,stat,cmd
```
- See that T? That means that the process is suspended due to our Ctrl-Z. The S in bash's STAT column means that bash is sleeping while waiting for input. The R in ps's column means that it's actively running, and the + means that it's in the foreground!
- Now if we run bg our sleep which was suspended is shifted to background. Letter S will appear in STAT 

### References 
None

## Foregrounding Processes
Bring a backgrounded /challenge/run process to the foreground using fg.

### Solve
**Flag:** `pwn.college{MCOudR65AUmB9-6PavIA0XkBTMe.QX4QDO0wyM3kjNzEzW}`

```bash
command /challenge/run
command ^Z
command bg
command fg 
command /challenge/run
pwn.college{MCOudR65AUmB9-6PavIA0XkBTMe.QX4QDO0wyM3kjNzEzW}
```

### New Learnings
- Imagine that you have a backgrounded process, and you want to mess with it some more. What do you do? Well, you can foreground a backgrounded process with fg just like you foreground a suspended process

### References 
None

## Starting Backgrounded Processes
Launch /challenge/run in the background using & to get the flag.

### Solve
**Flag:** `pwn.college{87tq9HL5BmO1JwCho_rVpOgpoPP.QX5QDO0wyM3kjNzEzW}`

```bash
command /challenge/run &
pwn.college{87tq9HL5BmO1JwCho_rVpOgpoPP.QX5QDO0wyM3kjNzEzW}
```

### New Learnings
- Of course, you don't have to suspend processes to background them: you can start them backgrounded right off the bat! It's easy; all you have to do is append & to the command

### References 
None

## Process Exit Codes
Run /challenge/get-code to get its exit code, then pass that code to /challenge/submit-code as an argument.

### Solve
**Flag:** `pwn.college{helloworld}`

```bash
command /challenge/get-code
command echo $?
command /challenge/submit-code 128
pwn.college{sxyQLrmuJ5cTMCeuRdvpMeT9QSX.QX5YDO1wyM3kjNzEzW}
```

### New Learnings
- You can access the exit code of the most recently-terminated command using the special ? variable (don't forget to prepend it with $ to read its value!)

### References 
None
