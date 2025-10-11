# Terminal Multiplexing

## Launching Screen 
Job Control Is Wonderful

### Solve
**Flag:** `pwn.college{4PQte3ngUk3Kvx76gYEhQDHdXSq.0VN4IDOxwyM3kjNzEzW}`

```bash
command screen
pwn.college{4PQte3ngUk3Kvx76gYEhQDHdXSq.0VN4IDOxwyM3kjNzEzW}
```

### New Learnings
- screen is a program that creates virtual terminals inside your terminal. It's somewhat like having multiple browser tabs, but for your command line!

### References 
None

## Detaching and Attaching
Jobs and Sessions

### Solve
**Flag:** `pwn.college{023tGGMpPPE1lClT6WvizaiE674.0lN4IDOxwyM3kjNzEzW}`

```bash
command screen
command screen -r
pwn.college{023tGGMpPPE1lClT6WvizaiE674.0lN4IDOxwyM3kjNzEzW}
```

### New Learnings
- Imagine you're working on something important over a remote connection, and your connection drops. With a normal terminal (outside of this awesome dojo environment), everything's gone
- With screen, your work keeps running, and you can reattach later!
- You detach by pressing Ctrl-A, followed by d (for detach). This leaves your session running in the background while you return to your normal termina
- To reattach, you can use the -r argument to screen

### References 
None

## Fidning Sessions
Disowning Processes

### Solve
**Flag:** `pwn.college{kwDJSyacyM-ank3K-sS4Ncrnqw_.01N4IDOxwyM3kjNzEzW}`

```bash
command screen -ls
pwn.college{kwDJSyacyM-ank3K-sS4Ncrnqw_.01N4IDOxwyM3kjNzEzW}
```

### New Learnings
- The identifiers of the sessions are the PID of each respective screen process, a dot, and the name of the screen session. To attach to a specific one, you use its name or its PID by giving it as an argument to screen -r.
- In this challenge, we've created three screen sessions for you. One of them contains the flag. The other two are decoys!

### References 
None

## Switching Windows
Foregrounding and Backgrounding

### Solve
**Flag:** ` pwn.college{8XAfoZXJZEcgOtujjRziUc_LExj.0FO4IDOxwyM3kjNzEzW}`

```bash
command screen -ls
command screen -r challenge_session
command Ctrl+A 0
pwn.college{8XAfoZXJZEcgOtujjRziUc_LExj.0FO4IDOxwyM3kjNzEzW}
```

### New Learnings
- Inside a single screen session, you can have multiple windows, like your browser has multiple tabs. This can be super handy for organizing different tasks!
- These windows are handled with different keyboard shortcuts, all starting with Ctrl-A:
    - Ctrl-A c - Create a new window
    - Ctrl-A n - Next window
    - Ctrl-A p - Previous window
    - Ctrl-A 0 through Ctrl-A 9 - Jump directly to window 0-9
    - Ctrl-A " - bring up a selection menu of all of the windows


### References 
None

## Detaching And Attaching
Suspending Jobs

### Solve
**Flag:** `pwn.college{I7W_jOUNHN05xBXQc9YBpipMdkx.0VO4IDOxwyM3kjNzEzW}`

```bash
command tmux
command /challenge/run
command  tmux a
pwn.college{I7W_jOUNHN05xBXQc9YBpipMdkx.0VO4IDOxwyM3kjNzEzW}
```

### New Learnings
- tmux (terminal multiplexer) is screen's younger, more modern cousin. It does all the same things but with some different key bindings. The biggest difference? Instead of Ctrl-A, tmux uses Ctrl-B as its command prefix.
- So to detach from tmux, you press Ctrl-B followed by d.
- tmux ls - List sessions
- tmux attach or tmux a - Reattach to session

### References 
None

## Switching Windows
Killing Processes

### Solve
**Flag:** `pwn.college{I7W_jOUNHN05xBXQc9YBpipMdkx.0VO4IDOxwyM3kjNzEzW}`

```bash
command tmux a
pwn.college{I7W_jOUNHN05xBXQc9YBpipMdkx.0VO4IDOxwyM3kjNzEzW}
```

### New Learnings
- Just like screen, tmux has windows. The key combos are different, but the concept is the same:
    - Ctrl-B c - Create a new window
    - Ctrl-B n - Next window
    - Ctrl-B p - Previous window
    - Ctrl-B 0 through Ctrl-B 9 - Jump to window 0-9
    - Ctrl-B w - See a nice window picker

### References 
None
