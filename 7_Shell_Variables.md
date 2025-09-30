# Shell Variables

## Printing Variables
Have your shell print out the FLAG variable and solve this challenge!

### Solve
**Flag:** `pwn.college{wNUAT11SDmP3Z6O1E4sqH8PM1Kf.QX3UTN0wyM3kjNzEzW}`


```bash
command echo $FLAG
pwn.college{wNUAT11SDmP3Z6O1E4sqH8PM1Kf.QX3UTN0wyM3kjNzEzW}
```

### New Learnings
You can also print out variables with echo, by prepending the variable name with a $. For example, there is a variable, PWD, that always holds the current working directory of the current shell.

### References 
None

---

## Setting Variables
To solve this level, you must set the PWN variable to the value COLLEGE. Be careful: both the names and values of variables are case-sensitive! PWN is not the same as pwn and COLLEGE is not the same as College.

### Solve
**Flag:** `pwn.college{Ywxeyat_fOujK1VEkUmilZh2VDP.QX5UTN0wyM3kjNzEzW}`


```bash
command PWN=COLLEGE
pwn.college{Ywxeyat_fOujK1VEkUmilZh2VDP.QX5UTN0wyM3kjNzEzW}
```

### New Learnings
- Just like many other languages you can use VAR=SOMETHING to set the value
- Note that there are no spaces around the =! If you put spaces (e.g., VAR = 1337), the shell won't recognize a variable assignment and will, instead, try to run the VAR command
- Also note that this uses VAR and not $VAR: the $ is only prepended to access variables

### References 
None

---

## Multi-word Variables
In this level, you'll need to set the variable PWN to COLLEGE YEAH. Good luck!

### Solve
**Flag:** `pwn.college{Av2jUwG0O_DJ3H7n-D_p4wMvKc8.QXwYTN0wyM3kjNzEzW}`


```bash
command PWN="COLLEGE YEAH"
pwn.college{Av2jUwG0O_DJ3H7n-D_p4wMvKc8.QXwYTN0wyM3kjNzEzW}
```

### New Learnings
- To set VAR to 1337 SAUCE, you need to quote it VAR="1337 SAUCE"

### References 
None

---

## Exporting Variables
In this challenge, you must invoke /challenge/run with the PWN variable exported and set to the value COLLEGE, and the COLLEGE variable set to the value PWN but not exported (e.g., not inherited by /challenge/run)

### Solve
**Flag:** `pwn.college{YoGbvCEtimKSFHz1jdbnWSgujZr.QXyYTN0wyM3kjNzEzW}`


```bash
command PWN=COLLEGE
command COLLEGE=PWN
pwn.college{YoGbvCEtimKSFHz1jdbnWSgujZr.QXyYTN0wyM3kjNzEzW}
```

### New Learnings
- By default, variables that you set in a shell session are local to that shell process
- This makes sense because your shell variables might have sensitive or weird data, and you don't want it leaking to other programs you run unless it explicitly shoul
- You export your variables. When you export your variables, they are passed into the environment variables of child processes.

### References 
None

---

## Printing Exported Variables
Trying env command

### Solve
**Flag:** `pwn.college{helloworld}`


```bash
command env
pwn.college{oPrsyOVJ-SNITl22mSlCK6BOyWU.QX4UTN0wyM3kjNzEzW}
```

### New Learnings
-  env command: it'll print out every exported variable set in your shell

### References 
None

---

## Storing Command Output
Read the output of the /challenge/run command directly into a variable called PWN, and it will contain the flag!

### Solve
**Flag:** `pwn.college{QhTT7_kyFtNIV2-77afocZH41mw.QX1cDN1wyM3kjNzEzW}`


```bash
command PWN=$(/challenge/run)
command echo $PWN
pwn.college{QhTT7_kyFtNIV2-77afocZH41mw.QX1cDN1wyM3kjNzEzW}
```

### New Learnings
- Use of Command Substitution
- Trivia: You can also use backticks instead of $(): FLAG=`cat /flag` instead of FLAG=$(cat /flag) in the example above. This is an older format, and has some disadvantages (for example, imagine if you wanted to nest command substitutions. How would you do $(cat $(find / -name flag)) with backticks? The official stance of pwn.college is that you should use $(blah) instead of `blah`

### References 
None

---

## Reading Input
In this challenge, your job is to use read to set the PWN variable to the value COLLEGE

### Solve
**Flag:** `pwn.college{gl_rg4BDRTivTIWB4OW930tpdvs.QX4cTN0wyM3kjNzEzW}`


```bash
command read PWN
pwn.college{gl_rg4BDRTivTIWB4OW930tpdvs.QX4cTN0wyM3kjNzEzW}
```

### New Learnings
- reading input from the user (you). That's done using the aptly named read builtin, which reads input into a variable!
- Here is an example using the -p argument, which lets you specify a prompt (otherwise, it would be hard for you, reading this now, to separate input from output)
`read -p "INPUT: " MY_VARIABLE`
- Keep in mind, read reads data from your standard input! The first Hello!, above, was inputted rather than outputted.
-

### References 
None

---

## Reading Files
Read /challenge/read_me into the PWN environment variable, and we'll give you the flag! The /challenge/read_me will keep changing, so you'll need to read it right into the PWN variable with one command!

### Solve
**Flag:** `pwn.college{cOhAugE8y_boxm4i4M8DWfm8k0X.QXwIDO0wyM3kjNzEzW}`


```bash
command read PWN < /challenge/read_me
pwn.college{cOhAugE8y_boxm4i4M8DWfm8k0X.QXwIDO0wyM3kjNzEzW}
```

### New Learnings
- Instead of doing VAR=$(cat some_file) whcih is what grouchy hackers call a "Useless Use of Cat"
- Previously, you read user input into a variable. You've also previously redirected files into command input! Put them together

### References 
None

---