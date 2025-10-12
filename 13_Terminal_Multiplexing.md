# Terminal Multiplexing

## Launching Screen
Create a detachable `screen` session to run persistent tasks across disconnects.

### Solve
**Flag:** `pwn.college{4PQte3ngUk3Kvx76gYEhQDHdXSq.0VN4IDOxwyM3kjNzEzW}`

```bash
command screen
pwn.college{4PQte3ngUk3Kvx76gYEhQDHdXSq.0VN4IDOxwyM3kjNzEzW}
```

### New Learnings
- `screen` creates detachable terminal sessions you can detach and reattach to.
- Detaching preserves running programs across disconnects or logouts.

```bash
# example:
screen -S mysession    # start a named session
screen -ls              # list sessions
```

### References 
None

## Detaching and Attaching
Detach sessions (`Ctrl-A d`) and reattach them later with `screen -r`.

### Solve
**Flag:** `pwn.college{023tGGMpPPE1lClT6WvizaiE674.0lN4IDOxwyM3kjNzEzW}`

```bash
command screen
command screen -r
pwn.college{023tGGMpPPE1lClT6WvizaiE674.0lN4IDOxwyM3kjNzEzW}
```

### New Learnings
- Detach with `Ctrl-A d`; reattach with `screen -r` or `screen -r name`.
- Named sessions (`-S`) make reattachment easy on multi-session hosts.

```bash
# reattach named session:
screen -r mysession
```

### References 
None

## Finding Sessions
List and identify `screen` sessions with `screen -ls` and reattach by id or name.

### Solve
**Flag:** `pwn.college{kwDJSyacyM-ank3K-sS4Ncrnqw_.01N4IDOxwyM3kjNzEzW}`

```bash
command screen -ls
pwn.college{kwDJSyacyM-ank3K-sS4Ncrnqw_.01N4IDOxwyM3kjNzEzW}
```

### New Learnings
- `screen -ls` shows session IDs like `PID.name` you can pass to `screen -r`.
- Use `screen -S name` to create, `screen -X` to send commands to sessions remotely.

```bash
# example:
screen -ls
screen -r 12345.mysession
```

### References 
None

## Switching Windows
Use screen's window controls (`Ctrl-A c`, `Ctrl-A n/p`, `Ctrl-A 0..9`) to manage multiple shells.

### Solve
**Flag:** `pwn.college{8XAfoZXJZEcgOtujjRziUc_LExj.0FO4IDOxwyM3kjNzEzW}`

```bash
command screen -ls
command screen -r challenge_session
command Ctrl+A 0
pwn.college{8XAfoZXJZEcgOtujjRziUc_LExj.0FO4IDOxwyM3kjNzEzW}
```

### New Learnings
- Create windows with `Ctrl-A c`, navigate with `Ctrl-A n`/`p` and jump to numbered windows with `Ctrl-A 0..9`.
- Use `Ctrl-A "` to list windows and switch interactively.

```bash
# no direct bash example for key bindings; practice inside a screen session
```

### References 
None

## Using tmux
Create and manage detachable sessions with `tmux` (modern alternative to screen).

### Solve
**Flag:** `pwn.college{I7W_jOUNHN05xBXQc9YBpipMdkx.0VO4IDOxwyM3kjNzEzW}`

```bash
command tmux
command /challenge/run
command  tmux a
pwn.college{I7W_jOUNHN05xBXQc9YBpipMdkx.0VO4IDOxwyM3kjNzEzW}
```

### New Learnings
- `tmux` is a modern multiplexer with `Ctrl-B` prefix; create sessions with `tmux new -s name`.
- Detach with `Ctrl-B d`, reattach with `tmux attach -t name` or `tmux a`.

```bash
# example:
tmux new -s mysession
tmux ls
tmux attach -t mysession
```

### References 
None

## tmux Window Controls
Use tmux's keybindings (`Ctrl-B c`, `Ctrl-B n/p`, `Ctrl-B w`) to create and navigate windows and panes.

### Solve
**Flag:** `pwn.college{I7W_jOUNHN05xBXQc9YBpipMdkx.0VO4IDOxwyM3kjNzEzW}`

```bash
command tmux a
pwn.college{I7W_jOUNHN05xBXQc9YBpipMdkx.0VO4IDOxwyM3kjNzEzW}
```

### New Learnings
- `Ctrl-B c` creates a new window; `Ctrl-B n`/`p` navigate; `Ctrl-B w` shows window list.
- tmux panes let you split a window (`Ctrl-B %` vertical, `Ctrl-B "` horizontal) for side-by-side tasks.

```bash
# example:
tmux a
```
