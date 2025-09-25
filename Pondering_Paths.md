# Pondering Paths

---

## The Root
The use of absolute path to open a file

### Solution
**Flag:** `pwn.college{ANqONht6ClS4bWI68ywT-tRTIXd.QX4cTO0wyM3kjNzEzW}`

```bash
command /pwn
pwn.college{ANqONht6ClS4bWI68ywT-tRTIXd.QX4cTO0wyM3kjNzEzW}
```

### New Learnings
We used the absolute path to run a file

### References 
None

---

## Program and absolute paths
This challenge again required us to execute it by invoking its absolute path. We would have to execute the run file that is in the challenge directory that is, in turn, in the / directory

### Solution
**Flag:** `pwn.college{wJP8IujEZiTfQGMEHWmhneUruZr.QX1QTN0wyM3kjNzEzW}`

```bash
command /challenge/run
pwn.college{wJP8IujEZiTfQGMEHWmhneUruZr.QX1QTN0wyM3kjNzEzW}
```

### New Learnings
/ is used to tell the root directory in linux... everything in linux starts from / as it is the parent of all directories

### References 
None

---

## Position thy self
This challenge will required us to execute the /challenge/run program from a specific path. We had to cd to that directory before rerunning the challenge program

### Solution
**Flag:** `pwn.college{U2ZXDI2BsJwj9kMZNCKrryAxr5J.QX2QTN0wyM3kjNzEzW}`

```bash
command /challenge/run
command cd /usr/include
hacker@paths~position-thy-self:/usr/include$ /challenge/run
pwn.college{U2ZXDI2BsJwj9kMZNCKrryAxr5J.QX2QTN0wyM3kjNzEzW}
```

### New Learnings
cd is used to change directory 

### References 
None

---

## Position elsewhere
This challenge required us to execute the /challenge/run program from a specific path. We had to cd to that directory before rerunning the challenge program.

### Solution
**Flag:** `pwn.college{Arewe6ZoipdT1gG5a-76f0_mSpP.QX3QTN0wyM3kjNzEzW}`

```bash
command /challenge/run
command cd /usr/bin
command /challenge/run
pwn.college{Arewe6ZoipdT1gG5a-76f0_mSpP.QX3QTN0wyM3kjNzEzW}
```

### New Learnings
cd is used to change directory 

Similar to __position_thy_self__

### References 
None

---

## Position yet elsewhere
This challenge required us to execute the /challenge/run program from a specific path. We had to cd to that directory before rerunning the challenge program.


### Solution
**Flag:** `pwn.college{EGxO8c-T0XSlE9Jaq5XmKGDrKAx.QX4QTN0wyM3kjNzEzW}`

```bash
command /challenge/run
command cd /var/log
command /challenge/run
pwn.college{EGxO8c-T0XSlE9Jaq5XmKGDrKAx.QX4QTN0wyM3kjNzEzW}
```

### New Learnings
cd is used to change directory 

Similar to __position_thy_self__ and __position_elsewhere__

### References 
None

---

## implicit relative paths, from /
We need to run /challenge/run using a relative path while having a current working directory of /

### Solution
**Flag:** `pwn.college{k4ME7s7RozotXz4EGgtlSX_WaBI.QX5QTN0wyM3kjNzEzW}`

```bash
command cd /
command challenge/run
pwn.college{k4ME7s7RozotXz4EGgtlSX_WaBI.QX5QTN0wyM3kjNzEzW}
```

### New Learnings
We need not specify / before a relative path i.e. to execute something from current working directory

### References 
None

---

## explicit relative paths, from /
To run /challenge/run using relative path in a specific directory

### Solution
**Flag:** `pwn.college{o98epbraDrKXVfYwQ8nEo62-80f.QXwUTN0wyM3kjNzEzW}`

```bash
command /
command ./challenge/run
pwn.college{o98epbraDrKXVfYwQ8nEo62-80f.QXwUTN0wyM3kjNzEzW}
```

### New Learnings
./challenge means to run it in the current working directory. Where absolute needs the full path from the beginning for relative we can just begin from anywhere and continue further... via ./ which translates to from here.....

### References 
None

---

## implicit relative path
In this challenge, we'll learn how to explicitly use relative paths to launch run in this scenario. The way to do this is to tell Linux that you explicitly want to execute a program in the current directory, using . like in the previous levels.

### Solution
**Flag:** `pwn.college{4vFQNkOvl-GO4_rwopzh5caoF6p.QXxUTN0wyM3kjNzEzW}`

```bash
command cd /challenge
command ./run
pwn.college{4vFQNkOvl-GO4_rwopzh5caoF6p.QXxUTN0wyM3kjNzEzW}
```

### New Learnings
We should use ./run even to run files as a security measure in order not to get confused in file names to be run and system commands... 

### References 
None

---

## home sweet home
In this challenge, /challenge/run will write a copy of the flag to any file you specify as an argument on the commandline, with these constraints:

1. Your argument must be an absolute path.

2. The path must be inside your home directory.

3. Before expansion, your argument must be three characters or less.

Again, you must specify your path as an argument to /challenge/run

### Solution
**Flag:** `pwn.college{c79Vo_z227vdbHDGKMgdMkzbxgV.QXzMDO0wyM3kjNzEzW}`

```bash
command cd ~
command > l
command /challenge/run ~/l
pwn.college{c79Vo_z227vdbHDGKMgdMkzbxgV.QXzMDO0wyM3kjNzEzW}
```

### New Learnings
~ being shorthand for /home/hacker

Bash provides and uses this shorthand because, again, most of your time will be spent in your home directory. Hence ~ is expanded as /home/hacker

cd uses home directory as default destination

>l is used to create a file or touch l can also be used

### References 
[How_to_create_an_empty_file](https://stackoverflow.com/questions/9381463/how-to-create-a-file-in-linux-from-terminal-window)