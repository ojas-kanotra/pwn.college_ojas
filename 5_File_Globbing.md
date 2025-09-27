# File Globbing

---

## Matching With *
Starting from your home directory, change your directory to /challenge, but use globbing to keep the argument you pass to cd to at most four characters! Once you're there, run /challenge/run for the flag!

### Solve
**Flag:** `pwn.college{gN_NruhlzkA4ezAG-HzHDB0oAoC.QXxIDO0wyM3kjNzEzW}`

```bash
command cd /ch*
command /c*/run
pwn.college{gN_NruhlzkA4ezAG-HzHDB0oAoC.QXxIDO0wyM3kjNzEzW}
```

### New Learnings
- `*` is a wildcard that matches any sequence of characters (except `/` and leading `.`)
- Shell performs glob expansion before passing arguments to commands
- Globbing helps reduce typing by matching multiple files with patterns
- `*` can be used anywhere in a filename pattern to match variable parts
- Pattern `/ch*` matches `/challenge`, `/chdir`, etc.

### References 
None

---

## Matching With ?
Starting from your home directory, change your directory to /challenge, but use the ? character instead of c and l in the argument to cd! Once you're there, run /challenge/run for the flag!

### Solve
**Flag:** `pwn.college{UQ6qe9WT8CMYvcviwSyabD31-9y.QXyIDO0wyM3kjNzEzW}`

```bash
command cd /?ha??enge
command /?ha??enge/run
pwn.college{UQ6qe9WT8CMYvcviwSyabD31-9y.QXyIDO0wyM3kjNzEzW}
```

### New Learnings
- `?` is a single-character wildcard that matches exactly one character
- More precise than `*` when you know the exact number of characters to match
- Useful for patterns with known structure but variable characters
- `/?ha??enge` matches `/challenge` by replacing `c` and `l` with `?`
- Combines with other patterns for flexible filename matching

### References 
None

---

## Matching With []
We've placed a bunch of files in /challenge/files. Change your working directory to /challenge/files and run /challenge/run with a single argument that bracket-globs into file_b, file_a, file_s, and file_h

### Solve
**Flag:** `pwn.college{8jkBH53y8LBBZuplzhbf4t6v9mw.QXzIDO0wyM3kjNzEzW}`

```bash
command cd /challenge/files
command /challenge/run file_[absh]
pwn.college{8jkBH53y8LBBZuplzhbf4t6v9mw.QXzIDO0wyM3kjNzEzW}
```

### New Learnings
- `[]` brackets define character classes that match any single character from the set
- `[absh]` matches exactly one character: either `a`, `b`, `s`, or `h`
- More specific than `?` when you want to limit which characters can match
- Can specify ranges like `[a-z]` or `[0-9]` for character ranges
- Useful for matching files with similar names but different single characters

### References 
None

---

## Matching Paths With []
Once more, we've placed a bunch of files in /challenge/files. Starting from your home directory, run /challenge/run with a single argument that bracket-globs into the absolute paths to the file_b, file_a, file_s, and file_h files!

### Solve
**Flag:** `pwn.college{s_9FXXkApjOLrZ1rFKUCLnObf-G.QX0IDO0wyM3kjNzEzW}`

```bash
command /challenge/run /challenge/files/file_[absh]
pwn.college{s_9FXXkApjOLrZ1rFKUCLnObf-G.QX0IDO0wyM3kjNzEzW}
```

### New Learnings
- Globbing works with full absolute paths, not just filenames
- Can combine directory paths with glob patterns: `/path/to/file_[abc]`
- Shell expands the entire path before executing the command
- Enables matching files across different directories in one command
- Absolute path globbing provides precise file targeting

### References 
None

---

## Multiple Globs
This challenge has diversely-named files in /challenge/files. Go cd there and run /challenge/run, providing a single argument: a short (3 characters or less) globbed word with two * globs in it that covers every word that contains the letter p.

### Solve
**Flag:** `pwn.college{MAPAePB8GLtRJw7Rhq5AR10VQKV.0lM3kjNxwyM3kjNzEzW}`

```bash
command cd /challenge/files
command /challenge/run *p*
pwn.college{MAPAePB8GLtRJw7Rhq5AR10VQKV.0lM3kjNxwyM3kjNzEzW}
```

### New Learnings
- Multiple glob patterns can be combined in a single argument
- `*p*` uses two wildcards: matches any characters, then `p`, then any characters
- Enables complex pattern matching with minimal typing
- Pattern `*p*` matches `apple`, `pper`, `arp`, etc.
- Powerful technique for matching files with specific character sequences

### References 
None

---

## Mixing Globs
This challenge combines techniques from previous levels, requiring you to mix different globbing patterns together. 

### Solve
**Flag:** `pwn.college{0o0EyF46N6__6lzwoEaBvqV-Bwk.QX1IDO0wyM3kjNzEzW}`

```bash
command /challenge/run [cep]*
pwn.college{0o0EyF46N6__6lzwoEaBvqV-Bwk.QX1IDO0wyM3kjNzEzW}
```

### New Learnings
- Combines bracket notation `[]` with wildcard `*` for sophisticated patterns
- `[cep]*` matches files starting with `c`, `e`, or `p` followed by anything
- Demonstrates the power of mixing different glob types
- Creates precise yet flexible file matching patterns
- Essential skill for advanced shell scripting and file operations

### References 
None

---

## Exclusionary Globbing
Go forth to /challenge/files and run /challenge/run with all files that don't start with p, w, or n!

### Solve
**Flag:** `pwn.college{IsQo5BeC2nT-hDtjatiUvLRek0w.QX2IDO0wyM3kjNzEzW}`

```bash
command cd /challenge/files
command /challenge/run [^pwn]*
pwn.college{IsQo5BeC2nT-hDtjatiUvLRek0w.QX2IDO0wyM3kjNzEzW}
```

### New Learnings
- `[^characters]` or `[!characters]` creates negated character classes
- `[^pwn]*` matches files that do NOT start with `p`, `w`, or `n`
- Useful for excluding specific patterns from matches
- More efficient than listing all acceptable characters when exclusions are shorter
- Essential for filtering operations and selective file processing

### References 
None

---

## Tab Completion
This challenge has copied the flag into /challenge/pwncollege, and you can freely cat that file. But you can't type the filename directly - you must use tab completion to complete it.

### Solve
**Flag:** `pwn.college{4xlm6jFb1Hi93nn7Cm2DL88AtCL.0FN0EzNxwyM3kjNzEzW}`

```bash
command cat /challenge/pwncollege
pwn.college{4xlm6jFb1Hi93nn7Cm2DL88AtCL.0FN0EzNxwyM3kjNzEzW}
```

### New Learnings
- Tab completion provides safer alternative to wildcards for specific files
- Press `Tab` key to automatically complete partial filenames
- Shell analyzes available files and completes unambiguous portions
- Reduces typing errors and increases command accuracy
- More precise than wildcards when targeting specific files

### References 
None

---

## Multiple Options For Tab Completion
This challenge has a /challenge/files directory with a bunch of files starting with pwncollege. Tab-complete from /challenge/files/p or so, and make your way to the flag!

### Solve
**Flag:** `pwn.college{4l4cztehrRFiM-jJKuIAnJP2IDm.0lN0EzNxwyM3kjNzEzW}`

```bash
command cat pwncollege-flag
pwn.college{4l4cztehrRFiM-jJKuIAnJP2IDm.0lN0EzNxwyM3kjNzEzW}
```

### New Learnings
- Tab completion handles ambiguous matches by completing common prefixes
- When multiple files match, bash completes up to the point of divergence
- Press `Tab` twice to see all available options when completion stops
- Interactive feedback helps navigate files with similar names
- Essential for efficient file system navigation and command completion

### References 
None

---

## Tab Completion On Commands
Type pwncollege and hit the tab key to auto-complete it!

### Solve
**Flag:** `pwn.college{A0JPna84wVicfXHhMHpPuh3W0h4.0VN0EzNxwyM3kjNzEzW}`

```bash
command pwncollege-21878
pwn.college{A0JPna84wVicfXHhMHpPuh3W0h4.0VN0EzNxwyM3kjNzEzW}
```

### New Learnings
- Tab completion works for commands, not just filenames
- Shell can complete executable names in PATH directories
- Helps discover available commands starting with specific letters
- Reduces memorization burden for complex command names
- Universal feature that speeds up all types of shell interaction

### References 
None
