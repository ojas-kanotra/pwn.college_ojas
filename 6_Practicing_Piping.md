# Practicing Piping

## Redirecting output
In this challenge, you must use this output redirection to write the word PWN (all uppercase) to the filename COLLEGE (all uppercase).

### Solve
**Flag:** `pwn.college{QtgTnqy52bUlGeLltuz0tY3eIdG.QX0YTN0wyM3kjNzEzW}`


```bash
command echo PWN > COLLEGE
pwn.college{QtgTnqy52bUlGeLltuz0tY3eIdG.QX0YTN0wyM3kjNzEzW}
```

### New Learnings
- Redirecting stdout to files. You can accomplish this with the > character
- hacker@dojo:~$ echo hi > asdf
- This will redirect the output of echo hi (which will be hi) to the file asdf

### References 
None

---

## Redirecting more output
Add challenge description here

### Solve
**Flag:** `pwn.college{A0XSkkO6pVyALJ6ialgUKDyQE7S.QX1YTN0wyM3kjNzEzW}`


```bash
command /challenge/run > myflag
command cat myflag
pwn.college{A0XSkkO6pVyALJ6ialgUKDyQE7S.QX1YTN0wyM3kjNzEzW}
```

### New Learnings
- Aside from redirecting the output of echo, you can, of course, redirect the output of any command.
- command > file

### References 
None

---

## Appending output
To practice, run /challenge/run with an append-mode redirect of the output to the file /home/hacker/the-flag. The practice will write the first half of the flag to the file, and the second half to stdout if stdout is redirected to the file. If you properly redirect in append-mode, the second half will be appended to the first, but if you redirect in truncation mode (>), the second half will overwrite the first and you won't get the flag!

### Solve
**Flag:** `pwn.college{Ynmx4-QxJt3ggoeGwlBjo1ZgBdO.QX3ATO0wyM3kjNzEzW}`

```bash
command /challenge/run > /home/hacker/the-flag
command /challenge/run >> /home/hacker/the-flag
command cat /home/hacker/the-flag
pwn.college{Ynmx4-QxJt3ggoeGwlBjo1ZgBdO.QX3ATO0wyM3kjNzEzW}
```

### New Learnings
- > simply writes over the file
- >> appends to the file
- Often times, you want to do this in aggregate: run a bunch of commands, save their output, and grep through it later. In this case, you might want all that output to keep appending to the same file, but > will create a new output file every time, deleting the old contents.
- You can redirect input in append mode using >> instead of >

### References 
None

---

## Redirecting errors
Add challenge description here

### Solve
**Flag:** `pwn.college{helloworld}`


```bash
command 1
command 2
pwn.college{helloworld}
```

### New Learnings
Brief note on what you learned from the challenge

### References 
None

---

## Redirecting input
Add challenge description here

### Solve
**Flag:** `pwn.college{helloworld}`


```bash
command 1
command 2
pwn.college{helloworld}
```

### New Learnings
Brief note on what you learned from the challenge

### References 
None

---

## Grepping stored results
Add challenge description here

### Solve
**Flag:** `pwn.college{helloworld}`


```bash
command 1
command 2
pwn.college{helloworld}
```

### New Learnings
Brief note on what you learned from the challenge

### References 
None

---

## Grepping live output
Add challenge description here

### Solve
**Flag:** `pwn.college{helloworld}`


```bash
command 1
command 2
pwn.college{helloworld}
```

### New Learnings
Brief note on what you learned from the challenge

### References 
None

---

## Grepping errors
Add challenge description here

### Solve
**Flag:** `pwn.college{helloworld}`


```bash
command 1
command 2
pwn.college{helloworld}
```

### New Learnings
Brief note on what you learned from the challenge

### References 
None

---

## Filtering With grep -v
Add challenge description here

### Solve
**Flag:** `pwn.college{helloworld}`


```bash
command 1
command 2
pwn.college{helloworld}
```

### New Learnings
Brief note on what you learned from the challenge

### References 
None

---

## Duplicating piped data with tee
Add challenge description here

### Solve
**Flag:** `pwn.college{helloworld}`


```bash
command 1
command 2
pwn.college{helloworld}
```

### New Learnings
Brief note on what you learned from the challenge

### References 
None

---

## Process substitution for input
Add challenge description here

### Solve
**Flag:** `pwn.college{helloworld}`


```bash
command 1
command 2
pwn.college{helloworld}
```

### New Learnings
Brief note on what you learned from the challenge

### References 
None

---

## Writing to multiple programs
Add challenge description here

### Solve
**Flag:** `pwn.college{helloworld}`


```bash
command 1
command 2
pwn.college{helloworld}
```

### New Learnings
Brief note on what you learned from the challenge

### References 
None

---

## Split-piping stderr and stdout
Add challenge description here

### Solve
**Flag:** `pwn.college{helloworld}`


```bash
command 1
command 2
pwn.college{helloworld}
```

### New Learnings
Brief note on what you learned from the challenge

### References 
None

---

## Named pipes
Add challenge description here

### Solve
**Flag:** `pwn.college{helloworld}`


```bash
command 1
command 2
pwn.college{helloworld}
```

### New Learnings
Brief note on what you learned from the challenge

### References 
None

---