# Comprehending Commands

---

## Cat: Not The Pet But The Command!
In this challenge, we have to read the flag file in the home directory using the cat command. The cat command is one of the most commonly used commands for displaying file contents to the terminal.

### Solutions
**Flag:** `pwn.college{gL42aIIiwe4UzIS8t7QPkJCjr4r.QXxcTN0wyM3kjNzEzW}`

```bash
command cat flag
pwn.college{gL42aIIiwe4UzIS8t7QPkJCjr4r.QXxcTN0wyM3kjNzEzW}
```

### New Learnings
- **Cat Command Function**: The `cat` command displays the contents of files directly to the terminal
- **Multiple File Support**: Can concatenate and display multiple files when given multiple arguments sequentially
- **Basic Syntax**: Use `cat filename` for single files or `cat file1 file2 file3` for multiple files
- **Essential File Reading**: Fundamental command for reading and viewing file contents in Linux systems
- **Output Display**: Contents are printed to standard output (terminal) for immediate viewing 

### References 
None

---

## Catting Absolute Paths
In this challenge, we need to use the cat command with the absolute path to read the flag file located at /flag. This demonstrates how cat works with absolute paths to access files from any location in the filesystem.

### Solutions
**Flag:** `pwn.college{wzRMkeXuf2BJxP1qQ7E2c-S0g5b.QX5ETO0wyM3kjNzEzW}`

```bash
command cat /flag
pwn.college{wzRMkeXuf2BJxP1qQ7E2c-S0g5b.QX5ETO0wyM3kjNzEzW}
```

### New Learnings
- **Absolute Path Compatibility**: The `cat` command works with absolute paths to access files from any location
- **Location Independence**: Absolute paths eliminate ambiguity about file location regardless of current directory
- **Root Level Access**: `/flag` demonstrates accessing files directly at the root level of the filesystem
- **Reliable File Access**: Combining `cat` with absolute paths provides consistent and reliable file access
- **Path Flexibility**: Can access files anywhere in the filesystem using their full absolute path

### References 
None

---

## More Catting Practice
In this challenge, the flag is placed in a deeply nested directory structure. Since we cannot use the cd command to navigate to the directory, we must use cat with the complete absolute path to read the flag file. This teaches us that absolute paths allow us to access files from anywhere in the filesystem without changing our current directory.

### Solutions
**Flag:** `pwn.college{IC226XLziorjbXNUSpPdMcFkK0Y.QXwITO0wyM3kjNzEzW}`

```bash
command cd /flag
command cat /usr/include/nfs/flag
pwn.college{IC226XLziorjbXNUSpPdMcFkK0Y.QXwITO0wyM3kjNzEzW}
```

### New Learnings
- **Advanced Cat Usage**: Demonstrates advanced use of `cat` with complex nested absolute paths
- **Deep Directory Navigation**: Accessing files in deep directory structures using complete absolute paths
- **Command Restriction Bypass**: Understanding that restrictions on `cd` don't limit absolute path access with other commands
- **Direct Path Access**: Long complex paths can be typed directly without the need to navigate through intermediate directories
- **Filesystem Independence**: Absolute paths work regardless of current working directory or navigation restrictions

### References 
None

---

## Grepping For A Needle In A Haystack
In this challenge, there's a massive file with 100,000 lines of text, and somewhere in that haystack is our needle - the flag! We need to use the grep command to search through this enormous file and find the line that contains the flag. This demonstrates how grep is essential for finding specific content in large files.

### Solutions
**Flag:** `pwn.college{oT3iDT4vVmv4d6s7w6kPrco77dd.QX3EDO0wyM3kjNzEzW}`   

```bash
command grep "pwn.college" /challenge/data.txt
pwn.college{oT3iDT4vVmv4d6s7w6kPrco77dd.QX3EDO0wyM3kjNzEzW}
```

### New Learnings
- **Grep Command Function**: The `grep` command searches for specific text patterns within files efficiently
- **Pattern Matching**: Essential tool for finding specific content in large files (finding needles in haystacks)
- **Grep Syntax**: Basic syntax is `grep "search_pattern" /path/to/file`
- **Large File Handling**: Efficiently processes large files that would be impractical to read manually with `cat`
- **Filtered Output**: Returns only the lines containing the matching pattern, filtering out irrelevant content
- **Text Processing**: Fundamental tool for text processing and content extraction in Linux systems

### References 
None

---

## Comparing Files
In this challenge, we have two files to work with. One file contains 100 fake flags as decoys, while the other file contains those same 100 fake flags PLUS the real flag we need. We need to use the diff command to compare these files and identify what's different between them - that difference will be our real flag!

### Solutions
**Flag:** `pwn.college{0_IpS4ExEXv3gbJwCOebgSiRRHZ.01MwMDOxwyM3kjNzEzW}`

```bash
command diff decoys_only.txt decoys_and_real.txt
98a99
pwn.college{0_IpS4ExEXv3gbJwCOebgSiRRHZ.01MwMDOxwyM3kjNzEzW}
```

### New Learnings
- **Diff Command Function**: The `diff` command compares two files line by line and highlights differences between them
- **Basic Syntax**: Use `diff file1 file2` to compare two files
- **Output Format**: `<` indicates lines from the first file, `>` indicates lines from the second file  
- **Change Types**: Numbers show line positions and change types (a=added, c=changed, d=deleted)
- **File Comparison**: Essential tool for finding unique content between similar files
- **Version Control**: Foundation for understanding version control systems and file change tracking

### References 
None

---

## Listing Files
In this challenge, the /challenge/run program has been renamed to something else! We need to use the ls command to list all the files in the /challenge directory to discover what the program has been renamed to, then execute it to get our flag.

### Solutions
**Flag:** `pwn.college{A9xRXdtHG4Ym0QHA0ZX2Lj73YNj.QX4IDO0wyM3kjNzEzW}`

```bash
command cd /challenge
command ls
32406-renamed-run-25388  DESCRIPTION.md
command /challenge/32406-renamed-run-25388
pwn.college{A9xRXdtHG4Ym0QHA0ZX2Lj73YNj.QX4IDO0wyM3kjNzEzW}
```

### New Learnings
- **LS Command Function**: The `ls` command lists the contents (files and directories) of a directory
- **Filesystem Exploration**: Essential tool for exploring filesystem structure and discovering files
- **Path Flexibility**: Can be used with specific paths to list contents of any directory: `ls /path/to/directory`
- **File Discovery**: Helpful for finding renamed, hidden, or unknown filenames in directories
- **Directory Navigation**: Fundamental command for understanding directory contents before navigation

### References 
None

---

## Touching Files
create two files: /tmp/pwn and /tmp/college, and run /challenge/run to get the flag

### Solutions
**Flag:** `pwn.college{k05W63N0rdf4BHrdwd9yO8p59pJ.QXwMDO0wyM3kjNzEzW}`

```bash
command touch /tmp/pwn
command touch /tmp/college
pwn.college{k05W63N0rdf4BHrdwd9yO8p59pJ.QXwMDO0wyM3kjNzEzW}
```

### New Learnings
- `touch` command creates new empty files or updates file timestamps
- Syntax: `touch filename` or `touch /path/to/file`
- Creates files instantly without opening an editor
- Useful for creating placeholder files or meeting file existence requirements

### References 
None

---

## Removing Files
This challenge will create a delete_me file in your home directory! Delete it, then run /challenge/check

### Solutions
**Flag:** `pwn.college{EKtzxQls4sXR_IIaVUACE-1xcXs.QX2kDM1wyM3kjNzEzW}`

```bash
command rm ~/delete_me
command /challenge/check
pwn.college{EKtzxQls4sXR_IIaVUACE-1xcXs.QX2kDM1wyM3kjNzEzW}
```

### New Learnings
- `rm` command removes (deletes) files from the filesystem
- Syntax: `rm filename` or `rm /path/to/file`
- Deletion is permanent - files are not moved to trash
- Use with caution as deleted files are typically unrecoverable

### References 
None

---

## Moving Files
This challenge wants you to move the /flag file into /tmp/hack-the-planet and When you're done, run /challenge/check

### Solutions
**Flag:** `pwn.college{MpfI_bLpF9VMkZoENNRg2oyJeIb.0VOxEzNxwyM3kjNzEzW}`

```bash
command mv /flag /tmp/hack-the-planet
pwn.college{MpfI_bLpF9VMkZoENNRg2oyJeIb.0VOxEzNxwyM3kjNzEzW}
```

### New Learnings
- `mv` command moves files from one location to another
- Syntax: `mv source_path destination_path`
- Can also rename files by moving within same directory
- Efficiently relocates files without copying and deleting

### References 
None

---

## Hidden Files
Go find the flag, hidden as a dot-prepended file in /

### Solutions
**Flag:** `pwn.college{U0XBHvxIvY0Sj-24D9DfbG_wcFL.QXwUDO0wyM3kjNzEzW}`

```bash
command ls -a ~
command cat /.flag-95252496416636
pwn.college{U0XBHvxIvY0Sj-24D9DfbG_wcFL.QXwUDO0wyM3kjNzEzW}
```

### New Learnings
- Hidden files in Linux start with a dot (.) and are not shown by default
- `ls -a` displays all files including hidden ones
- Hidden files are commonly used for configuration and system files
- Understanding hidden file conventions is important for complete filesystem exploration

### References 
None

---

## An Epic Filesystem Quest
Your first clue is in /. Head on over there.
Look around with ls. There'll be a file named HINT or CLUE or something along those lines!
cat that file to read the clue!
Depending on what the clue says, head on over to the next directory (or don't!).
Follow the clues to the flag!

### Solutions
**Flag:** `pwn.college{8vnpMAJW0SSyl9y3jK7Rz2ME10q.QX5IDO0wyM3kjNzEzW}`

```bash
command ls /
command cat /README
command cd /usr/share/javascript/mathjax/jax/output/SVG/fonts/Latin-Modern
command cat BRIEF
command cd /usr/local/lib/python3.8/dist-packages/jedi/third_party/typeshed/stdlib/2/multiprocessing/dummy
command cat GIST
command cd /opt/linux/linux-5.4/drivers/gpu/drm/amd/display/dc/dce100
command ls -a
command cat .DISPATCH
command cd /usr/share/racket/pkgs/data-doc/data/scribblings/compiled
command cat MEMO
command cat /usr/local/lib/python3.8/dist-packages/networkx/algorithms/link_analysis/tests/__pycache__/BLUEPRINT-TRAPPED
command cd /usr/share/icons/Humanity/status/16
command cat POINTER
command cd /usr/share/racket/pkgs/typed-racket-compatibility/typed/scheme/base/compiled
command cat REVELATION
command cd /opt/linux/linux-5.4/drivers/staging/media/tegra-vde
command cat MESSAGE
pwn.college{8vnpMAJW0SSyl9y3jK7Rz2ME10q.QX5IDO0wyM3kjNzEzW}
```

### New Learnings
- Combines multiple fundamental commands: `cd`, `ls`, `cat`
- Demonstrates following clues through filesystem navigation
- Practices reading files and interpreting directions
- Shows real-world application of basic Linux commands in sequence

### References 
None

---

## Making Directories
create a /tmp/pwn directory and make a college file in it! Then run /challenge/run, which will check your solution and give you the flag

### Solutions
**Flag:** `pwn.college{s91iG6b7wuqu8bc6pS3clBcbs6h.QXxMDO0wyM3kjNzEzW}`

```bash
command mkdir /tmp/pwn
command touch /tmp/pwn/college
command /challenge/run
pwn.college{s91iG6b7wuqu8bc6pS3clBcbs6h.QXxMDO0wyM3kjNzEzW}
```

### New Learnings
- `mkdir` command creates new directories
- Syntax: `mkdir directory_name` or `mkdir /path/to/directory`
- Essential for organizing files and creating folder structures
- Can be combined with other commands like `touch` to create files within directories 

### References 
None

---

## Finding Files
 I've hidden the flag in a random directory on the filesystem. It's still called flag

### Solutions
**Flag:** `pwn.college{sefSGqJ5rB3C4qdzd23xUgItBvY.QXyMDO0wyM3kjNzEzW}`

```bash
command find / -name flag
command  cat /usr/local/lib/python3.8/dist-packages/pwnlib/flag
command cat /usr/share/racket/pkgs/realm/chapter6/flag
pwn.college{sefSGqJ5rB3C4qdzd23xUgItBvY.QXyMDO0wyM3kjNzEzW}
```

### New Learnings
- `find` command searches for files and directories across the filesystem
- Syntax: `find /path/to/search -name "filename"`
- `-name` criteria searches by filename or pattern
- Searches recursively through directory trees
- Powerful tool for locating files when you know the name but not the location 

### References 
None

---

## Linking Files
This section is incomplete and needs to be filled with the actual challenge details.

### Solutions
**Flag:** `[Challenge not completed]`

```bash
command
commands
```

### New Learnings
- Hard links and symbolic links in Linux filesystem
- `ln` command for creating file links

### References 
None