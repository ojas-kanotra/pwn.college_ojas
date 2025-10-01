# File Globbing

---

## Matching With Asterisk
Navigate to `/challenge` using globbing patterns with the `*` wildcard, keeping your argument to `cd` to four characters or less. Then run `/challenge/run` for the flag.

### Solve
**Flag:** `pwn.college{gN_NruhlzkA4ezAG-HzHDB0oAoC.QXxIDO0wyM3kjNzEzW}`

```bash
command cd /ch*
command /c*/run
pwn.college{gN_NruhlzkA4ezAG-HzHDB0oAoC.QXxIDO0wyM3kjNzEzW}
```

### New Learnings
- **Asterisk Wildcard**: The `*` symbol is a wildcard that matches any sequence of characters (except `/` and leading `.`)
- **Shell Expansion**: The shell performs glob expansion before passing arguments to commands
- **Typing Efficiency**: Globbing helps reduce typing by matching multiple files with concise patterns
- **Pattern Flexibility**: `*` can be used anywhere in a filename pattern to match variable parts of names
- **Pattern Examples**: Pattern `/ch*` matches `/challenge`, `/chdir`, `/chrome`, etc.
- **Character Limitation**: Useful for working within character count restrictions while maintaining functionality

### References 
None

---

## Matching With Question Mark
Navigate to `/challenge` using the `?` wildcard to replace specific characters (`c` and `l`) in the path. Then run `/challenge/run` for the flag.

### Solve
**Flag:** `pwn.college{UQ6qe9WT8CMYvcviwSyabD31-9y.QXyIDO0wyM3kjNzEzW}`

```bash
command cd /?ha??enge
command /?ha??enge/run
pwn.college{UQ6qe9WT8CMYvcviwSyabD31-9y.QXyIDO0wyM3kjNzEzW}
```

### New Learnings
- **Question Mark Wildcard**: The `?` symbol is a single-character wildcard that matches exactly one character
- **Precision Control**: More precise than `*` when you know the exact number of characters to match
- **Structured Patterns**: Useful for patterns with known structure but variable individual characters
- **Pattern Example**: `/?ha??enge` matches `/challenge` by replacing `c` and `l` with `?`
- **Pattern Combination**: Can be combined with other wildcards for flexible and precise filename matching
- **Character Substitution**: Ideal for replacing specific known characters while maintaining pattern structure

### References 
None

---

## Matching With Brackets
Navigate to `/challenge/files` and run `/challenge/run` with a single argument using bracket globbing to match `file_b`, `file_a`, `file_s`, and `file_h`.

### Solve
**Flag:** `pwn.college{8jkBH53y8LBBZuplzhbf4t6v9mw.QXzIDO0wyM3kjNzEzW}`

```bash
command cd /challenge/files
command /challenge/run file_[absh]
pwn.college{8jkBH53y8LBBZuplzhbf4t6v9mw.QXzIDO0wyM3kjNzEzW}
```

### New Learnings
- **Bracket Character Classes**: `[]` brackets define character classes that match any single character from the specified set
- **Specific Matching**: `[absh]` matches exactly one character: either `a`, `b`, `s`, or `h`
- **Precision Control**: More specific than `?` when you want to limit which characters can match a position
- **Range Specification**: Can specify ranges like `[a-z]` for lowercase letters or `[0-9]` for digits
- **Pattern Efficiency**: Useful for matching files with similar names but different single characters
- **Character Selection**: Allows precise control over which characters are acceptable in a pattern position

### References 
None

---

## Matching Paths With Brackets
From your home directory, run `/challenge/run` with a single argument using bracket globbing to match the absolute paths to `file_b`, `file_a`, `file_s`, and `file_h`.

### Solve
**Flag:** `pwn.college{s_9FXXkApjOLrZ1rFKUCLnObf-G.QX0IDO0wyM3kjNzEzW}`

```bash
command /challenge/run /challenge/files/file_[absh]
pwn.college{s_9FXXkApjOLrZ1rFKUCLnObf-G.QX0IDO0wyM3kjNzEzW}
```

### New Learnings
- **Full Path Globbing**: Globbing works with complete absolute paths, not just filenames
- **Path Pattern Combination**: Can combine directory paths with glob patterns: `/path/to/file_[abc]`
- **Shell Path Expansion**: Shell expands the entire path pattern before executing the command
- **Multi-Directory Matching**: Enables matching files across different directories in a single command
- **Absolute Path Precision**: Absolute path globbing provides precise file targeting regardless of current directory
- **Location Independence**: Works from any directory since absolute paths are used

### References 
None

---

## Multiple Globs
Navigate to `/challenge/files` and run `/challenge/run` with a single argument: create a short (3 characters or less) globbed pattern using two `*` wildcards that matches every file containing the letter `p`.

### Solve
**Flag:** `pwn.college{MAPAePB8GLtRJw7Rhq5AR10VQKV.0lM3kjNxwyM3kjNzEzW}`

```bash
command cd /challenge/files
command /challenge/run *p*
pwn.college{MAPAePB8GLtRJw7Rhq5AR10VQKV.0lM3kjNxwyM3kjNzEzW}
```

### New Learnings
- **Multiple Wildcard Usage**: Multiple glob patterns can be combined in a single argument for complex matching
- **Pattern Structure**: `*p*` uses two wildcards: matches any characters, then `p`, then any characters
- **Efficient Matching**: Enables complex pattern matching with minimal typing and maximum flexibility
- **Pattern Examples**: Pattern `*p*` matches `apple`, `pepper`, `arp`, `laptop`, etc.
- **Character Sequence Matching**: Powerful technique for finding files containing specific character sequences anywhere in the name
- **Minimal Pattern Maximum Coverage**: Short patterns can match extensive file sets when designed properly

### References 
None

---

## Mixing Globs
Combine different globbing techniques from previous lessons to create sophisticated pattern matching expressions. 

### Solve
**Flag:** `pwn.college{0o0EyF46N6__6lzwoEaBvqV-Bwk.QX1IDO0wyM3kjNzEzW}`

```bash
command /challenge/run [cep]*
pwn.college{0o0EyF46N6__6lzwoEaBvqV-Bwk.QX1IDO0wyM3kjNzEzW}
```

### New Learnings
- **Pattern Combination**: Combines bracket notation `[]` with wildcard `*` for sophisticated pattern matching
- **Complex Pattern Example**: `[cep]*` matches files starting with `c`, `e`, or `p` followed by any characters
- **Glob Synergy**: Demonstrates the power of mixing different glob types for enhanced pattern control
- **Precision and Flexibility**: Creates patterns that are both precise in requirements and flexible in matching
- **Advanced Scripting**: Essential skill for advanced shell scripting and automated file operations
- **Pattern Optimization**: Combining glob types allows for more efficient and expressive file matching patterns

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
