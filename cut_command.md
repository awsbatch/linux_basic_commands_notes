# What is `cut`?
  - The `cut` command in Linux is used to extract specific sections (columns/fields/characters) from each line of a file or from standard input (stdin).
  - Think of it as a way to “slice” text by character position, byte position, or delimiter-based fields.

## Syntax
```
cut OPTION... [FILE]...
```

# Key Options
| Option              | Description                                       |
|---------------------|---------------------------------------------------|
| `-b`                | Select bytes (useful for fixed-width text)        |
| `-c`                | Select characters (character positions)           |
| `-f`                | Select fields (columns based on delimiter)        |
| `-d`                | Specify a custom delimiter (default is TAB)       |
| `--complement`      | Output everything except the selected part        |
| `--output-delimiter`| Change output delimiter                           |

### Extract by Character Positions (-c)
```
cut -c1-5 file.txt
```
  - Meaning: Extract characters 1 to 5 from each line.

**Example Input (file.txt):**
```
HelloWorld
LinuxRocks
```
**Output:**

```
Hello
Linux
```

### Extract Specific Characters (Non-Contiguous)
```
cut -c1,3,5 file.txt
```
  - **Meaning: Extract only characters 1, 3, and 5.**

**Example Input:**
```
HelloWorld
LinuxRocks
```

**Output:**
```
Hlo
Lnx
```

### Extract by Byte Positions (-b)
```
cut -b1-4 file.txt
```
  - **Meaning: Extract the first 4 bytes (useful for binary-safe fixed-length records).**

### Extract Fields with Default Delimiter (Tab) (-f)
```
cut -f2 file.txt
```
  - **Meaning: Extract second field (column) from a TAB-separated file.**

### Extract Fields with Custom Delimiter (-d)
```
cut -d':' -f1 /etc/passwd
```
  - **Meaning: Extract the first field from /etc/passwd file (username).**

**Output (example):**
```
root
daemon
bin
```

### Extract Multiple Fields
```
cut -d',' -f1,3 file.csv
```
  - **Meaning: Extract first and third columns from a CSV file.**

### Exclude (Complement) Selected Fields
```
cut -d',' --complement -f2 file.csv
```
  - **Meaning: Print all fields except the 2nd one.**

### Change Output Delimiter
```
cut -d',' -f1,3 --output-delimiter='|' file.csv
```
  - **Meaning: Extract fields 1 and 3 but separate them with | instead of ,.**

### Use with Pipe
```
cat /etc/passwd | cut -d':' -f1
```
**or simply:**

```
cut -d':' -f1 /etc/passwd
```
