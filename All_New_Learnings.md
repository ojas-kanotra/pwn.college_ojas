# Compact Linux Cheat-sheet: Real Examples & Forgotten Tips

- **cd**
    - `cd` changes your current working directory, letting you navigate the filesystem.
    - Example: `cd /var/log` moves to system logs; `cd ..` goes up one level. `cd -` toggles between last two directories.
    - Mastering `cd` is key for efficient movement and file management in the shell.

- **Absolute-paths**
    - Absolute paths begin with `/` and point to a location from the root of the filesystem, making them unambiguous.
    - Example: `/usr/bin/python3` runs Python from anywhere, regardless of your current directory.
    - Use absolute paths when you need to reference files or executables reliably across scripts and commands.

- **Explicit-relative (./)**
    - Explicit relative paths use `./` or `../` to specify files or executables relative to your current directory.
    - Example: `./script.sh` runs a script in the current folder; `../program` accesses one level up.
    - This avoids confusion with similarly named files elsewhere and ensures you run the intended file.

- **Home (~)**
    - The tilde `~` represents your home directory, a shortcut for user-specific files and folders.
    - Example: `cd ~/Downloads` quickly navigates to your Downloads folder from anywhere.
    - Useful for scripts and commands that need to work across different user accounts.

- **ls**
    - `ls` lists files and directories, with options to control format and sorting.
    - Example: `ls -lh` shows sizes in readable units; `ls -ltr` sorts by modification time, newest last.
    - Use `ls` to explore directory contents and check file details quickly.

- **cat**
    - `cat` displays the contents of files, useful for quick viewing or combining files.
    - Example: `cat file.txt` prints the file; for large files, use `less` or `head` to avoid overwhelming output.
    - Great for inspecting logs, configs, or chaining file contents in scripts.

- **grep**
    - `grep` searches for patterns in files or input, making it essential for finding information fast.
    - Example: `grep error logfile.txt` finds lines with "error"; `grep -r TODO .` searches recursively. Use `-i` for case-insensitive, `-n` for line numbers, `-v` to exclude matches.
    - Master regex and options for powerful text processing and troubleshooting.

- **diff**
    - `diff` compares files line by line, showing differences and changes between them.
    - Example: `diff file1.txt file2.txt` highlights additions, deletions, and changes; `diff -u` gives unified output for patches.
    - Use with process substitution to compare command outputs directly, streamlining troubleshooting and version control.

- **ls -a**
    - `ls -a` lists all files, including hidden ones that start with a dot (`.`).
    - Example: `ls -a` reveals config files and folders not shown by default.
    - Essential for finding system or application settings and debugging issues.

- **touch**
    - `touch` creates empty files or updates the modification time of existing ones.
    - Example: `touch new.txt` makes a new file; running again updates its timestamp.
    - Useful for scripting, placeholder files, or triggering automated tasks.

- **rm**
    - `rm` deletes files and directories permanently, with no trash or undo.
    - Example: `rm file.txt` removes a file; `rm -r folder/` deletes a folder and its contents. Use `-i` for confirmation before deleting.
    - Always double-check before using `rm`, especially with wildcards or recursive options.

- **mv**
    - `mv` moves files or directories, and can also rename them in place.
    - Example: `mv old.txt new.txt` renames a file; `mv file.txt folder/` moves it to another folder.
    - Efficient for organizing, refactoring, or batch renaming files.

- **mkdir**
    - `mkdir` creates new directories, with options for nested folder creation.
    - Example: `mkdir newdir` makes a single folder; `mkdir -p parent/child/grandchild` builds a full path at once.
    - Use for project setup, organizing files, or preparing directory structures in scripts.

- **find**
    - `find` searches for files and directories based on name, type, size, and more, recursively. `find /path/to/search -name "filename"`
    - Example: `find . -name '*.log'` finds all log files; `find /tmp -type d` lists directories. Use `-exec` to run commands on results.
    - Powerful for automation, cleanup, and locating files in large projects.

- **man / --help**
    - `man` shows manual pages for commands, while `--help` gives quick usage info directly in the terminal.
    - Example: `man grep` opens the full manual; `grep --help` lists options and examples. 
    - Use `/pattern` to search inside man pages.
    - Use `n` for next search result, `N` for previous search result
    - Essential for learning new commands, troubleshooting, and finding advanced options.

 - **help (builtins)**
     - `help` provides documentation for shell built-in commands, which may not have separate manual pages.
     - Example: `help cd` explains directory changes; `help` alone lists all builtins.
     - Use to understand shell-specific features and differences from external programs.

 - **globbing (* ? [])**
     - Globbing uses wildcards to match multiple files or patterns, saving time and keystrokes.
     - Example: `ls *.txt` lists all text files; `ls file?.txt` matches single-character variations. Use `[ab]*.txt` for files starting with `a` or `b`.
     - Quotes prevent unwanted expansion, useful for literal matches or scripting.
     - `[^characters]` or `[!characters]` creates negated character classes

 - **tab-completion**
     - Tab completion speeds up typing by auto-filling filenames, commands, or options.
     - Press Tab once to complete; twice to list all possibilities. Works for files, folders, and executables.
     - Reduces errors and helps discover available commands or files quickly.

 - **> and >>**
     - `>` and `>>` redirect command output to files, either overwriting (`>`) or appending (`>>`).
     - Example: `echo hi > file.txt` replaces content; `echo bye >> file.txt` adds to the end. Use `> /dev/null` to discard output.
     - Essential for logging, automation, and controlling where results are stored.

 - **<**
     - `<` redirects a file's contents as input to a command, replacing standard input.
     - Example: `sort < file.txt` sorts lines from the file instead of typing them manually.
     - Useful for automating tasks and processing files in scripts.

 - **2> and 2>&1**
     - `2>` redirects error messages (stderr) to a file, while `2>&1` merges errors with normal output (stdout).
     - Example: `command 2> errors.txt` saves errors; `command > out.txt 2>&1` combines everything in one file.
     - Vital for debugging, logging, and capturing all output for review.

 - **|**
     - `|` pipes the output of one command into another, creating powerful data processing chains.
     - Example: `cat file.txt | grep error | sort | uniq -c` filters and counts errors. Use with `less` for paging through large results.
     - Pipes enable modular workflows and efficient command chaining.

 - **tee**
     - `tee` splits output, saving it to a file while also displaying it in the terminal.
     - Example: `ls | tee files.txt` logs and shows results; `tee -a` appends instead of overwriting.
     - Great for debugging pipelines or keeping a record of command output.

 - **process substitution**
     - Process substitution lets you use command output as if it were a file, without creating temporary files.
     - Example: `diff <(ls dir1) <(ls dir2)` compares directory listings directly.
     - Ideal for advanced scripting and comparing dynamic data.

 - **mkfifo**
     - `mkfifo` creates a named pipe (FIFO), allowing two processes to communicate through a file-like interface.
     - Example: `mkfifo mypipe`; then use `cat < mypipe` to read and `echo hi > mypipe` to write.
     - Useful for inter-process communication and advanced shell scripting.

 - **VAR=$(cmd)**
     - `VAR=$(cmd)` assigns the output of a command to a variable, enabling dynamic scripting.
     - Example: `files=$(ls *.txt)` stores filenames in `files` for later use.
     - Preferred over backticks for nesting and readability in modern shell scripts.

 - **VAR=value**
     - `VAR=value` sets a shell variable, which you can reference later with `$VAR`.
     - Example: `MYVAR=hello` creates a variable; use `$MYVAR` to access its value. No spaces around `=`!
     - Variables are essential for storing data, customizing scripts, and passing information between commands.

 - **read**
     - `read` takes input from the user or a file and stores it in a variable.
     - Example: `read name` waits for user input; `read line < file.txt` reads the first line of a file.
     - Crucial for interactive scripts and processing file contents efficiently.

 ```

