# Processes and Jobs

## Listing Processes
Use `ps` (or `pgrep`) to locate running programs, inspect their PIDs and command lines to identify targets.

### Solve
**Flag:** `pwn.college{IQdgPKPSMRYwD_vDb3cGIQT2Ktu.QX4MDO0wyM3kjNzEzW}`

```bash
command ps aux
command /challenge/20101-run-8284
pwn.college{IQdgPKPSMRYwD_vDb3cGIQT2Ktu.QX4MDO0wyM3kjNzEzW}
```

### New Learnings
- **ps overview**: `ps` shows running processes; use `ps aux` (BSD style) or `ps -ef` (UNIX style) to list system-wide processes.
- **Key columns**: USER (owner), PID (process id), PPID (parent PID), TTY, STIME/START (start time), TIME (CPU time), CMD (command).
- **Finding processes**: combine `ps` with `grep` (e.g., `ps aux | grep name`) or use `pgrep name` to get PIDs quickly.
- **Resource view**: `ps aux` includes CPU% and MEM% columns for quick resource checks.
- **PID actions**: use `kill PID` (SIGTERM) for graceful termination or `kill -9 PID` (SIGKILL) to force-stop.

```bash
# examples:
ps aux | grep run
pgrep -a run         # list matching processes and args
kill 1234             # request graceful stop
kill -9 1234          # force kill
```

### References 
None

## Killing Processes
Terminate interfering processes with `kill` (prefer graceful first) to allow other commands to run.

### Solve
**Flag:** `pwn.college{0tEXyNALA9uXh99u1OY9-s99IJG.QXyQDO0wyM3kjNzEzW}`

```bash
command ps aux | grep /challenge/dont_run
command kill 136
pwn.college{0tEXyNALA9uXh99u1OY9-s99IJG.QXyQDO0wyM3kjNzEzW}
```

### New Learnings
- **kill basics**: `kill PID` sends SIGTERM (graceful); `kill -9 PID` sends SIGKILL (forceful).
- **Safe termination first**: prefer `kill` without `-9` so processes can clean up files and state.
- **Discover PID**: find PID with `ps aux | grep pattern` or `pgrep name`.

```bash
# find and kill by name (example):
pkill -f /challenge/dont_run
```

### References 
None

## Interrupting Processes
Send Ctrl-C (SIGINT) to interrupt a foreground job; some programs trap it to perform cleanup.

### Solve
**Flag:** `pwn.college{gVVWCJhaODNLIk_s1LBFUjCoqiy.QXzQDO0wyM3kjNzEzW}`

```bash
command /challenge/run
command ^C
pwn.college{gVVWCJhaODNLIk_s1LBFUjCoqiy.QXzQDO0wyM3kjNzEzW}
```

### New Learnings
- **Ctrl-C (SIGINT)**: sends an interrupt to the foreground process; commonly terminates interactive programs.
- **Graceful handling**: some programs trap SIGINT to perform cleanup—behavior varies by program.

```bash
# press Ctrl-C in the terminal to send SIGINT to the foreground job
```

### References 
None

## Killing Misbehaving Processes
Identify and stop misbehaving daemons using `ps`, `top`, and `kill` to restore normal operation.

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
- **Practical debugging**: use `ps`, `pgrep`, `top`, and `htop` to inspect live processes and resource consumption.
- **Terminate or suspend**: `kill`, Ctrl-C, and `kill -9` are tools to stop misbehaving processes; prefer graceful methods first.

```bash
# quick live view:
top
```

### References 
None

## Suspending Processes
Suspend the foreground job with Ctrl-Z to stop it without killing it, then manage it with `jobs`/`bg`/`fg`.

### Solve
**Flag:** `pwn.college{Ibp9tzjyo4wKN3P1cdHabI1BbKO.QX1QDO0wyM3kjNzEzW}`

```bash
command /challenge/run
command ^Z
command /challenge/run
pwn.college{Ibp9tzjyo4wKN3P1cdHabI1BbKO.QX1QDO0wyM3kjNzEzW}
```

### New Learnings
- **Ctrl-Z (SIGTSTP)**: suspends the foreground job and returns control to the shell (job is stopped, not killed).
- **Jobs and signals**: manage suspended/background jobs with `jobs`, `fg`, and `bg`.
- **Job states**: S (sleeping), R (running), T (stopped); `ps` and `jobs` show differing views.

```bash
# suspend then background example:
sleep 100
# press Ctrl-Z, then:
bg
jobs
```

### References 
None

## Resuming Processes
Use `fg` to bring a stopped/backgrounded job back to the foreground for interaction.

### Solve
**Flag:** `pwn.college{YXAkynr0YsL3FsUDy-dyfBp5frZ.QX2QDO0wyM3kjNzEzW}`

```bash
command /challenge/run
command ^Z
command fg
pwn.college{YXAkynr0YsL3FsUDy-dyfBp5frZ.QX2QDO0wyM3kjNzEzW}
```

### New Learnings
- **fg**: brings a stopped/backgrounded job to the foreground so it can receive input and signals.
- **bg**: resumes a stopped job in the background so it continues running while you use the shell.

```bash
# bring job 1 to foreground:
fg %1
```

### References 
None

## Backgrounding Processes
Start a job in the background with `&` or move it there with `bg` to free the shell prompt.

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
- **Background at start**: append `&` to run a job in the background immediately (e.g., `/challenge/run &`).
- **Shell prompt returned**: backgrounding frees the shell for new commands while the job runs.
- **Job control commands**: `jobs` lists current jobs; `fg %1` or `bg %1` operate on numbered jobs.
- **STAT column decoding**: `T`=stopped, `S`=sleeping, `R`=running, `+`=foreground job in `ps`/`jobs` output.

```bash
# start in background:
/challenge/run &
jobs
```

### References 
None

## Foregrounding Processes
Use `fg` (with job id) to return a backgrounded job to the foreground for input and signals.

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
- **Bring back to foreground**: `fg` restores backgrounded processes for interaction; use job ids (e.g., `%1`) when multiple jobs exist.

```bash
# bring job 1 to foreground:
fg %1
```

### References 
None

## Starting Backgrounded Processes
Launch long-running tasks with `&` to run them concurrently while you continue working.

### Solve
**Flag:** `pwn.college{87tq9HL5BmO1JwCho_rVpOgpoPP.QX5QDO0wyM3kjNzEzW}`

```bash
command /challenge/run &
pwn.college{87tq9HL5BmO1JwCho_rVpOgpoPP.QX5QDO0wyM3kjNzEzW}
```

### New Learnings
- **Background at start**: append `&` to run a job in the background immediately (e.g., `/challenge/run &`).
- **Shell prompt returned**: backgrounding frees the shell for new commands while the job runs.

```bash
# start in background:
/challenge/run &
```

### References 
None

## Process Exit Codes
Check `$?` for the previous command's exit status to script behavior or pass the code to other tools.

### Solve
**Flag:** `pwn.college{helloworld}`

```bash
command /challenge/get-code
command echo $?
command /challenge/submit-code 128
pwn.college{sxyQLrmuJ5cTMCeuRdvpMeT9QSX.QX5YDO1wyM3kjNzEzW}
```

### New Learnings
- **Exit codes**: `$?` holds the exit status of the last command (0 = success, non-zero = failure).
- **Use cases**: check `$?` in scripts or use `&&`/`||` operators to branch on command success or failure.

```bash
# example:
false; echo $?    # prints non-zero
true; echo $?     # prints 0
```

### References 
None
