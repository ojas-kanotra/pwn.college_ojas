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
cat is used for reading out files 

It will concatenate multiple files if provided multiple arguments 

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
You can read it with cat at its absolute path: /flag

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
You can read it with cat at its absolute path: /flag

### References 
None

---

## Grepping for A Needle in A Haystack
In this challenge, I've put a hundred thousand lines of text into the /challenge/data.txt file. grep it for the flag!

### Solutions
**Flag:** `pwn.college{oT3iDT4vVmv4d6s7w6kPrco77dd.QX3EDO0wyM3kjNzEzW}`   

```bash
command grep "pwn.college" /challenge/data.txt
pwn.college{oT3iDT4vVmv4d6s7w6kPrco77dd.QX3EDO0wyM3kjNzEzW}
```

### New Learnings
For a longer file we can use grep to find the line containing specific text and it's traditional representation is 'grep SEARCH_STRING /path/to/file'

### References 
None

---

## comparing files
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
diff compares two files line by line and shows you exactly what's different between them
'diff file1 file2'
Output: 2c2
< world
---
> universe
The output tells us that line 2 changed (2c2), with world in the first file (<) being replaced by universe in the second file (>).

### References 
None

---

## listing files
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
ls is used to list the directories and files

### References 
None

---

## touching files
create two files: /tmp/pwn and /tmp/college, and run /challenge/run to get the flag

### Solutions
**Flag:** `pwn.college{k05W63N0rdf4BHrdwd9yO8p59pJ.QXwMDO0wyM3kjNzEzW}`

```bash
command touch /tmp/pwn
command touch /tmp/college
pwn.college{k05W63N0rdf4BHrdwd9yO8p59pJ.QXwMDO0wyM3kjNzEzW}
```

### New Learnings
You can create a new, blank file by touching it with the touch command

### References 
None

---

## removing files
This challenge will create a delete_me file in your home directory! Delete it, then run /challenge/check

### Solutions
**Flag:** `pwn.college{EKtzxQls4sXR_IIaVUACE-1xcXs.QX2kDM1wyM3kjNzEzW}`

```bash
command rm ~/delete_me
command /challenge/check
pwn.college{EKtzxQls4sXR_IIaVUACE-1xcXs.QX2kDM1wyM3kjNzEzW}
```

### New Learnings
In Linux, you remove files with the rm command

### References 
None

---

## moving files
This challenge wants you to move the /flag file into /tmp/hack-the-planet and When you're done, run /challenge/check

### Solutions
**Flag:** `pwn.college{MpfI_bLpF9VMkZoENNRg2oyJeIb.0VOxEzNxwyM3kjNzEzW}`

```bash
command mv /flag /tmp/hack-the-planet
pwn.college{MpfI_bLpF9VMkZoENNRg2oyJeIb.0VOxEzNxwyM3kjNzEzW}
```

### New Learnings
You can move files around with the mv command

### References 
None

---

## hidden files
Go find the flag, hidden as a dot-prepended file in /

### Solutions
**Flag:** `pwn.college{U0XBHvxIvY0Sj-24D9DfbG_wcFL.QXwUDO0wyM3kjNzEzW}`

```bash
command ls -a ~
command cat /.flag-95252496416636
pwn.college{U0XBHvxIvY0Sj-24D9DfbG_wcFL.QXwUDO0wyM3kjNzEzW}
```

### New Learnings
Interestingly, ls doesn't list all the files by default. Linux has a convention where files that start with a . don't show up by default in ls and in a few other contexts. To view them with ls, you need to invoke ls with the -a

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
Implementing knowledge of cd, ls, and cat

### References 
None

---

## making directories
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
We can make directories using mkdir command 

### References 
None

---

## finding files
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
The find command takes optional arguments describing the search criteria and the search location. If you don't specify a search criteria, find matches every file. If you don't specify a search location, find uses the current working directory (.)

find location_to_look_for criteria name_looking_for

criteria could be -name 

### References 
None

---

## linking files
Add challenge description here

### Solutions
**Flag:** `pwn.college{}`

```bash
command 1
command 2
pwn.college{}
```

### New Learnings
Brief note on what you learned from the challenge

### References 
None

---