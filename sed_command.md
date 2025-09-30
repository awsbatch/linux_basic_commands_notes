# 🟢 1. What is sed?

-  sed reads text line by line from a file or standard input.
-  It applies transformations (substitution, deletion, insertion, etc.) according to your commands.
-  By default, it prints the result to stdout (the screen). You can redirect to a file if needed.

### General syntax:
```
sed [options] 'command' file
```
### 🔹 1. Print All Lines (default behavior)
```
sed '' file.txt
```
👉 By default, sed prints every line after processing (even with no command).


### 🔹 2. Print Specific Line Numbers
```
sed -n '5p' file.txt
```
👉 Prints line 5 only.

```
sed -n '10,20p' file.txt  # lines 10–20
```
👉 Prints lines 1 through 3.

```
sed -n '1p;5p;10p' file.txt
```
👉 Prints lines 1, 5, and 10.

### 🔹 3. Print Last Line
```
sed -n '$p' file.txt
```
👉 `$` means "last line".

###🔹 4. Print Based on Patterns
```
sed -n '/error/p' file.txt
```
👉 Prints only lines containing error.

```
sed -n '/^#/p' file.txt
```
👉 Prints only lines starting with #.

### Lines NOT matching pattern:
```
sed -n '/error/!p' file.txt
```

###🔹 5. Exclude Lines (Invert)
```
sed '/error/d' file.txt
```
👉 Prints all lines except those with error.

### From line N to end:
```
sed -n '5,$p' file.txt
```

