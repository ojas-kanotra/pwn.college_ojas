# Hello Hackers

---

## Intro To Commands
Invoke the hello command to get the flag! Keep in mind: commands in Linux are case sensitive: hello is different from HELLO.

### Solve
**Flag:** `pwn.college{Ead7X6t_UmfRmi2ngdj1c_Qpr8R.QX3YjM1wyM3kjNzEzW}`

```bash
command hello
pwn.college{Ead7X6t_UmfRmi2ngdj1c_Qpr8R.QX3YjM1wyM3kjNzEzW}
```

### New Learnings
- **Case Sensitivity**: Commands in Linux are case-sensitive, meaning `hello` is different from `HELLO`
- **Basic Command Execution**: Execute commands by typing the command name followed by pressing Enter
- **Hello Command**: The `hello` command displays a greeting message when invoked
- **Command Structure**: Simple commands can be executed directly without additional arguments

### References 
None



## Intro To Arguments
In this challenge, to get the flag, you must run the hello command (NOT the echo command) with a single argument of hackers.

### Solve
**Flag:** `pwn.college{ADmX0Blf_xgK3QmLLUFvwkoTtu2.QX4YjM1wyM3kjNzEzW}`
 
```bash
command hello hackers
pwn.college{ADmX0Blf_xgK3QmLLUFvwkoTtu2.QX4YjM1wyM3kjNzEzW}
```

### New Learnings
- **Command Arguments**: Commands can accept arguments to modify their behavior or specify targets
- **Argument Syntax**: Use space-separated arguments after the command: `command argument1 argument2 ...`
- **Hello with Arguments**: The `hello` command with the `hackers` argument produces specific customized output
- **Parameter Passing**: Arguments are passed to commands to provide additional information or instructions 

### References 
None

---

## Command History
You can use the up and down arrow keys to scroll through previously saved commands. This challenge puts the flag in your command history. Open a terminal, press the up arrow key to see the flag! In other challenges, you'll see the history of commands you've run, making it easy to reuse similar commands.

### Solve
**Flag:** `pwn.college{Ead7X6t_UmfRmi2ngdj1c_Qpr8R.QX3YjM1wyM3kjNzEzW}`

```bash
command up arrow key
pwn.college{Y_rJv3Mb79yil8Vl1xypyGUv4Nt.0lNzEzNxwyM3kjNzEzW}
```

### New Learnings
- **Command History**: Terminal maintains a history of all previously executed commands for easy access
- **Up Arrow Navigation**: Press the up arrow key to navigate backwards through command history
- **Down Arrow Navigation**: Press the down arrow key to navigate forwards through command history
- **Efficiency Benefits**: Command history allows quick reuse of previously run commands, saving time and reducing typing errors
- **Session Persistence**: Command history is preserved across terminal sessions for continued productivity

### References 
None
