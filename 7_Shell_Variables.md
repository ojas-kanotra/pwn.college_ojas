# Shell Variables

---

## Printing Variables
Use the shell to print the value of the `FLAG` variable.

### Solve
**Flag:** `pwn.college{wNUAT11SDmP3Z6O1E4sqH8PM1Kf.QX3UTN0wyM3kjNzEzW}`


```bash
command echo $FLAG
pwn.college{wNUAT11SDmP3Z6O1E4sqH8PM1Kf.QX3UTN0wyM3kjNzEzW}
```

### New Learnings
- **Variable Access**: Print variables using `echo` by prepending the variable name with `$`
- **Dollar Sign Usage**: The `$` symbol tells the shell to access the variable's value, not its name
- **Built-in Variables**: The shell provides built-in variables like `PWD` (current working directory)
- **Variable Substitution**: The shell replaces `$VARIABLE` with the variable's actual value during command execution
- **Common Practice**: Using `echo $VARIABLE` is the standard way to display variable contents

### References 
None

---

## Setting Variables
Set the `PWN` variable to the value `COLLEGE`. Remember that variable names and values are case-sensitive.

### Solve
**Flag:** `pwn.college{Ywxeyat_fOujK1VEkUmilZh2VDP.QX5UTN0wyM3kjNzEzW}`


```bash
command PWN=COLLEGE
pwn.college{Ywxeyat_fOujK1VEkUmilZh2VDP.QX5UTN0wyM3kjNzEzW}
```

### New Learnings
- **Variable Assignment Syntax**: Use `VAR=VALUE` to set variable values (similar to other programming languages)
- **No Spaces Rule**: Never put spaces around the `=` sign in variable assignments
- **Space Consequences**: Spaces like `VAR = 1337` make the shell try to run `VAR` as a command instead
- **Assignment vs Access**: Use `VAR=value` to set variables, `$VAR` to access their values
- **Case Sensitivity**: Variable names and values are case-sensitive (`PWN` ≠ `pwn`, `COLLEGE` ≠ `College`)
- **Immediate Effect**: Variable assignments take effect immediately in the current shell session

### References 
None

---

## Multi-Word Variables
Set the `PWN` variable to the multi-word value "COLLEGE YEAH".

### Solve
**Flag:** `pwn.college{Av2jUwG0O_DJ3H7n-D_p4wMvKc8.QXwYTN0wyM3kjNzEzW}`


```bash
command PWN="COLLEGE YEAH"
pwn.college{Av2jUwG0O_DJ3H7n-D_p4wMvKc8.QXwYTN0wyM3kjNzEzW}
```

### New Learnings
- **Quote Multi-Word Values**: Use quotes for multi-word variable values: `VAR="MULTI WORD VALUE"`
- **Space Handling**: Quotes prevent the shell from interpreting spaces as command separators
- **String Preservation**: Quotes preserve the exact spacing and content of multi-word strings
- **Quote Types**: Can use double quotes (`"`) or single quotes (`'`) depending on needs
- **Variable Expansion**: Double quotes allow variable expansion within the value, single quotes don't

### References 
None

---

## Exporting Variables
Set `PWN=COLLEGE` as an exported variable and `COLLEGE=PWN` as a local (non-exported) variable, then run `/challenge/run`.

### Solve
**Flag:** `pwn.college{YoGbvCEtimKSFHz1jdbnWSgujZr.QXyYTN0wyM3kjNzEzW}`


```bash
command PWN=COLLEGE
command COLLEGE=PWN
pwn.college{YoGbvCEtimKSFHz1jdbnWSgujZr.QXyYTN0wyM3kjNzEzW}
```

### New Learnings
- **Local Variables**: By default, variables set in a shell session are local to that shell process
- **Security Isolation**: Local variables prevent sensitive data from leaking to other programs accidentally
- **Export Mechanism**: Use `export` command to make variables available to child processes
- **Environment Variables**: Exported variables become environment variables for child processes
- **Variable Scope**: Understanding the difference between local and exported variable scope
- **Process Inheritance**: Child processes inherit exported variables but not local ones

### References 
None

---

## Printing Exported Variables
Use the `env` command to display all exported environment variables.

### Solve
**Flag:** `pwn.college{oPrsyOVJ-SNITl22mSlCK6BOyWU.QX4UTN0wyM3kjNzEzW}`


```bash
command env
pwn.college{oPrsyOVJ-SNITl22mSlCK6BOyWU.QX4UTN0wyM3kjNzEzW}
```

### New Learnings
- **Env Command**: The `env` command prints all exported environment variables in the current shell
- **Environment Inspection**: Useful for debugging and understanding what variables are available to child processes
- **Variable Listing**: Shows both variable names and their values in `NAME=value` format
- **System Variables**: Displays system-set variables like `PATH`, `HOME`, `USER`, etc.
- **Debugging Tool**: Essential for troubleshooting environment-related issues

### References 
None

---

## Storing Command Output
Capture the output of `/challenge/run` directly into a variable called `PWN` using command substitution.

### Solve
**Flag:** `pwn.college{QhTT7_kyFtNIV2-77afocZH41mw.QX1cDN1wyM3kjNzEzW}`


```bash
command PWN=$(/challenge/run)
command echo $PWN
pwn.college{QhTT7_kyFtNIV2-77afocZH41mw.QX1cDN1wyM3kjNzEzW}
```

### New Learnings
- **Command Substitution**: Use `$(command)` to capture command output into variables
- **Modern Syntax**: `$(command)` is preferred over backticks `` `command` `` for command substitution
- **Nesting Capability**: `$(command)` syntax supports nested command substitutions easily
- **Variable Assignment**: Combine with assignment: `VAR=$(command)` to store output
- **Dynamic Values**: Allows variables to contain the results of command execution
- **Legacy Format**: Backticks are older and less flexible than `$()` syntax

### References 
None

---

## Reading Input
Use the `read` command to set the `PWN` variable to the value "COLLEGE" from user input.

### Solve
**Flag:** `pwn.college{gl_rg4BDRTivTIWB4OW930tpdvs.QX4cTN0wyM3kjNzEzW}`


```bash
command read PWN
pwn.college{gl_rg4BDRTivTIWB4OW930tpdvs.QX4cTN0wyM3kjNzEzW}
```

### New Learnings
- **Read Builtin**: The `read` command reads input from the user and stores it in a variable
- **Interactive Input**: Allows programs to prompt users for input and store responses
- **Prompt Option**: Use `-p "prompt text"` to display a prompt before reading input
- **Standard Input Source**: `read` gets data from standard input (keyboard by default)
- **Variable Population**: Input is automatically stored in the specified variable
- **User Interaction**: Essential for creating interactive shell scripts and programs

### References 
None

---

## Reading Files
Read the contents of `/challenge/read_me` directly into the `PWN` variable using input redirection with the `read` command.

### Solve
**Flag:** `pwn.college{cOhAugE8y_boxm4i4M8DWfm8k0X.QXwIDO0wyM3kjNzEzW}`


```bash
command read PWN < /challenge/read_me
pwn.college{cOhAugE8y_boxm4i4M8DWfm8k0X.QXwIDO0wyM3kjNzEzW}
```

### New Learnings
- **File Input Redirection**: Use `read VAR < file` to read file contents directly into a variable
- **Direct File Reading**: Combines `read` command with input redirection for file processing
- **Single Command Operation**: Accomplishes file reading and variable assignment in one step
- **Dynamic File Content**: Useful when file contents change and need to be captured immediately
- **Input Source Control**: Demonstrates controlling where `read` gets its input from (files vs keyboard)
- Instead of doing VAR=$(cat some_file) whcih is what grouchy hackers call a "Useless Use of Cat"
- Previously, you read user input into a variable. You've also previously redirected files into command input! Put them together

### References 
None

---