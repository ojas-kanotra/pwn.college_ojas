# Data Manipulation

## Translating Characters
Output uses inverted case; swap letter case with `tr` to recover the flag.

### Solve
**Flag:** `pwn.college{cdBOj9tyovExfljSNBLz3uYe9y_.01MxEzNxwyM3kjNzEzW}`

```bash
command /challenge/run | tr [A-Z,a-z] [a-z,A-Z]
pwn.college{cdBOj9tyovExfljSNBLz3uYe9y_.01MxEzNxwyM3kjNzEzW}
```

### New Learnings
- **tr (translate)**: translate characters from stdin to stdout (e.g., change case).
- **Basic usage**: provide two character sets to map from -> to, or use `-d` to delete characters.
- **Deletion mode**: `tr -d SET` removes all characters in SET from the stream.
- **Pipeline-friendly**: use `cmd | tr ...` to transform streaming data without creating temporary files.
- **Quoting & escaping**: quote escape sequences like `"\n"` and escape backslashes (`\\`) so `tr` receives them literally.

```bash
# examples:
echo 'AbC' | tr 'A-Z' 'a-z'       # change to lowercase
echo '1^f%lag' | tr -d '^%'       # delete decoy chars
```

### References 
None

## Deleting Characters
Remove decoy characters (e.g., ^, %) with `tr -d` to reveal the real flag characters.

### Solve
**Flag:** `pwn.college{0fHEow_7KdcQDCbiWcKkUjh0c_-.0FNxEzNxwyM3kjNzEzW}`

```bash
command /challenge/run | tr -d [^,*,%]
pwn.college{0fHEow_7KdcQDCbiWcKkUjh0c_-.0FNxEzNxwyM3kjNzEzW}
```

### New Learnings
- **Delete with -d**: `tr -d SET` removes all characters in SET from the input.
- **Character sets**: specify single chars, ranges or escape sequences in the SET.
- **Pipeline use**: `command | tr -d '%^'` is a fast way to strip unwanted characters.
- **No side-effects**: `tr -d` writes cleaned output to stdout for further piping or redirection.

```bash
# example:
echo 'a^b%cd' | tr -d '%^'       # outputs: abcd
```

### References 
None

## Deleting Newlines
The flag is split across lines; remove newlines (`tr -d "\\n"`) to join it into one line.

### Solve
**Flag:** `pwn.college{wJlj3TmYyIgIaPWbrb3QtsOs8Wk.0VNxEzNxwyM3kjNzEzW}`

```bash
command /challenge/run | tr -d "\n"
pwn.college{wJlj3TmYyIgIaPWbrb3QtsOs8Wk.0VNxEzNxwyM3kjNzEzW}
```

### New Learnings
- **Newline token**: `\n` represents a newline; include it in quotes so the shell passes it to `tr`.
- **Quoting & escaping**: use quotes and double-escapes for backslashes (e.g., `\\`) when needed.
- **Concatenate safely**: remove newlines (`tr -d "\n"`) to join multi-line output into a single line.
- **Use in pipelines**: combine `tr` with other tools (cut/sort/grep) to clean and process streamed data.

```bash
# example:
printf "pwn\n.college\n" | tr -d "\n"   # outputs: pwn.college
```

### References 
None

## Extracting the First Lines with Head
Use `head -n` to select the first N lines of streaming output and pass them on to the next command to obtain the flag.

### Solve
**Flag:** `pwn.college{8z-nttGabtoSImQFu6GwVsFqojT.0lNxEzNxwyM3kjNzEzW}`

```bash
command /challenge/pwn | head -n 7 | /challenge/college
pwn.college{8z-nttGabtoSImQFu6GwVsFqojT.0lNxEzNxwyM3kjNzEzW}
```

### New Learnings
- **head basics**: `head` prints the first N lines of input (default 10); use `-n` to set N.
- **Early-output extraction**: useful for sampling verbose or streaming output without processing everything.
- **Combine with pipes**: `cmd | head -n 7 | next_cmd` to limit downstream work and CPU usage.
- **Efficiency**: `head` stops reading after N lines, saving time on large streams.

```bash
# example:
some_big_command | head -n 7
```

### References 
None

## Extracting Specific Sections of Text
Columns contain flag pieces; use `cut` (or `awk`) to pick the correct field and then join pieces (e.g., `tr -d "\\n"`).

### Solve
**Flag:** `pwn.college{YvttT4HaeFosE2q0vfmS8_Aftpa.01NxEzNxwyM3kjNzEzW}`

```bash
command /challenge/run | cut -d " " -f 2 | tr -d "\n"
pwn.college{YvttT4HaeFosE2q0vfmS8_Aftpa.01NxEzNxwyM3kjNzEzW}
```

### New Learnings
- **cut for columns**: `cut -d DELIM -f N` extracts the Nth field using DELIM (e.g., space, comma).
- **Field selection**: use `-f` with single numbers, ranges (`1-3`), or lists (`1,4,7`).
- **Pipe-friendly**: `cmd | cut -d' ' -f2` isolates columns from streaming output for further processing.
- **Delimiter care**: when whitespace is inconsistent consider `awk` for robust parsing.

```bash
# example:
echo "1 flag_value" | cut -d' ' -f2
```

### References 
None

## Sorting Data
Sort the list to find the canonical or last/first entry (use `sort`, optionally `-r`/`-n`), then extract the target line.

### Solve
**Flag:** `pwn.college{UcIPiayy4TfZESEYLP8NRo85MNu.0FM0MDOxwyM3kjNzEzW}`

```bash
command sort /challenge/flags.txt
pwn.college{UcIPiayy4TfZESEYLP8NRo85MNu.0FM0MDOxwyM3kjNzEzW}
```

### New Learnings
- **sort overview**: `sort` orders lines lexicographically by default; useful to locate min/max or canonical ordering.
- **Common flags**: `-r` (reverse), `-n` (numeric), `-u` (unique), `-k` (key/column), `-t` (delimiter).
- **Practical uses**: find the last/first item, remove duplicates (`sort -u`), or prepare input for `uniq`.
- **Combine safely**: `sort | tail -n1` gets the alphabetically-last line; `sort -n` for numeric rankings.

```bash
# example:
sort /challenge/flags.txt | tail -n1
```

### References 
None
