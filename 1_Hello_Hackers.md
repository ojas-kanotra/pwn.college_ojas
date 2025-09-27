# Hello Hackers

## Intro To Commands
Invoke the hello command to get the flag! Keep in mind: commands in Linux are case sensitive: hello is different from HELLO.

### Solve
**Flag:** `pwn.college{Ead7X6t_UmfRmi2ngdj1c_Qpr8R.QX3YjM1wyM3kjNzEzW}`

```bash
command hello
pwn.college{Ead7X6t_UmfRmi2ngdj1c_Qpr8R.QX3YjM1wyM3kjNzEzW}
```

### New Learnings
- Commands in Linux are case-sensitive (hello ≠ HELLO)
- Basic command execution by typing the command name and pressing Enter
- The `hello` command is used to display a greeting message

### References 
None

---

## Intro To Arguments
In this challenge, to get the flag, you must run the hello command (NOT the echo command) with a single argument of hackers.

### Solve
**Flag:** `pwn.college{ADmX0Blf_xgK3QmLLUFvwkoTtu2.QX4YjM1wyM3kjNzEzW}`
 
```bash
command hello hackers
pwn.college{ADmX0Blf_xgK3QmLLUFvwkoTtu2.QX4YjM1wyM3kjNzEzW}
```

### New Learnings
- Commands can accept arguments
- Syntax: `command argument1 argument2 ...`
- Just like the `hello` command with the `hackers` argument produces specific output 

### References 
None

---

## Command History
You can scroll through those saved commands with the up/down arrow keys, and we'll practice that in this challenge. This challenge will inject the flag into your history. Bring up a terminal, hit the up arrow, and grab it! In other challenges, the history will contain the log of the commands you've run, so if you need to run a similar command again, you can use the arrow keys to scroll through and find it!

### Solve
**Flag:** `pwn.college{Ead7X6t_UmfRmi2ngdj1c_Qpr8R.QX3YjM1wyM3kjNzEzW}`

```bash
command up arrow key
pwn.college{Y_rJv3Mb79yil8Vl1xypyGUv4Nt.0lNzEzNxwyM3kjNzEzW}
```

### New Learnings
- Terminal maintains a history of previously executed commands
- Up arrow key navigates backwards through command history
- Down arrow key navigates forwards through command history
- Command history allows reusing previously run commands hence saving time

### References 
None
