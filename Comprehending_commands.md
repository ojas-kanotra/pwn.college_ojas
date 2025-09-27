# Comprehending Commands

---

## CAT: Not The Pet, But The Command!
In this challenge, we have to copy the flag to the flag file in the home directory.

### Solutions
**Flag:** `pwn.college{gL42aIIiwe4UzIS8t7QPkJCjr4r.QXxcTN0wyM3kjNzEzW}`

```bash
command cat flag
pwn.college{gL42aIIiwe4UzIS8t7QPkJCjr4r.QXxcTN0wyM3kjNzEzW}
```

### New Learnings
- `cat` command displays the contents of files to the terminal
- Can concatenate and display multiple files when given multiple arguments
- Syntax: `cat filename` or `cat file1 file2 file3`
- Essential command for reading file contents in Linux 

### References 
None

---

## Catting Absolute Paths
Using the absolute path for /flag

### Solutions
**Flag:** `pwn.college{wzRMkeXuf2BJxP1qQ7E2c-S0g5b.QX5ETO0wyM3kjNzEzW}`

```bash
command cat /flag
pwn.college{wzRMkeXuf2BJxP1qQ7E2c-S0g5b.QX5ETO0wyM3kjNzEzW}
```

### New Learnings
- `cat` works with absolute paths to access files from any location
- Absolute paths eliminate ambiguity about file location
- `/flag` demonstrates accessing files at root level
- Combining `cat` with absolute paths provides reliable file access

### References 
None

---

## More Catting Practice
It puts the flag in some crazy directory, and we aren't allowed to change directories with cd, so no cat flag for this question

### Solutions
**Flag:** `pwn.college{IC226XLziorjbXNUSpPdMcFkK0Y.QXwITO0wyM3kjNzEzW}`

```bash
command cd /flag
command cat /usr/include/nfs/flag
pwn.college{IC226XLziorjbXNUSpPdMcFkK0Y.QXwITO0wyM3kjNzEzW}
```

### New Learnings
- Demonstrates advanced use of `cat` with complex absolute paths
- Navigating deep directory structures using absolute paths
- Understanding that restrictions on `cd` don't affect absolute path access
- Long paths can be typed directly without navigating through directories

### References 
None

---

## Grepping For A Needle In A Haystack
In this challenge, I've put a hundred thousand lines of text into the /challenge/data.txt file. grep it for the flag!

### Solutions
**Flag:** `pwn.college{oT3iDT4vVmv4d6s7w6kPrco77dd.QX3EDO0wyM3kjNzEzW}`   

```bash
command grep "pwn.college" /challenge/data.txt
pwn.college{oT3iDT4vVmv4d6s7w6kPrco77dd.QX3EDO0wyM3kjNzEzW}
```

### New Learnings
- `grep` searches for specific text patterns within files
- Essential for finding needles in haystacks (specific content in large files)
- Syntax: `grep "search_pattern" /path/to/file`
- Efficiently handles large files that would be impractical to read manually
- Returns only lines containing the matching pattern

### References 
None

---

## Comparing Files
Now for your challenge! There are two files in /challenge:

/challenge/decoys_only.txt contains 100 fake flags
/challenge/decoys_and_real.txt contains all 100 fake flags plus the one real flag
Use diff to find what's different between these files and get your flag!

### Solutions
**Flag:** `pwn.college{0_IpS4ExEXv3gbJwCOebgSiRRHZ.01MwMDOxwyM3kjNzEzW}`

```bash
command diff decoys_only.txt decoys_and_real.txt
98a99
pwn.college{0_IpS4ExEXv3gbJwCOebgSiRRHZ.01MwMDOxwyM3kjNzEzW}
```

### New Learnings
- `diff` compares two files line by line and highlights differences
- Syntax: `diff file1 file2`
- Output format: `<` indicates lines from first file, `>` from second file
- Numbers show line positions and change types (a=added, c=changed, d=deleted)
- Useful for finding unique content between similar files

### References 
None

---

## Listing Files
In this challenge, we've named /challenge/run with some random name! List the files in /challenge to find it.

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
- `ls` lists the contents (files and directories) of a directory
- Essential for exploring filesystem structure and finding files
- Can be used with paths to list contents of specific directories
- Helpful for discovering renamed or unknown filenames

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