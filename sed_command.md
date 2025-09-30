# 🟢 1. What is sed?

-  sed reads text line by line from a file or standard input.
-  It applies transformations (substitution, deletion, insertion, etc.) according to your commands.
-  By default, it prints the result to stdout (the screen). You can redirect to a file if needed.

# Line printing using `sed` command
---
### General syntax:
```
sed [options] 'command' file
```
### 🔹 1. Print All Lines (default behavior)
```
sed '' file.txt
```
> 👉 By default, sed prints every line after processing (even with no command).


### Specific line
```
sed -n '5p' file.txt      # line 5
```

### Range of lines
```
sed -n '10,20p' file.txt  # lines 10–20
```

### First N lines
```
sed -n '1,5p' file.txt    # lines 1–5
```

### Last line
```
sed -n '$p' file.txt
```

### Multiple non-continuous lines
```
sed -n '1p;5p;10p' file.txt
```

## 2️⃣ Print by Pattern

### Lines containing pattern
```
sed -n '/error/p' file.txt
```

### Lines NOT containing pattern
```
sed -n '/error/!p' file.txt
```

###  Exclude Lines (Invert)
```
sed '/error/d' file.txt
```

### Lines starting with #
```
sed -n '/^#/p' file.txt
```

### Lines between two patterns
```
sed -n '/BEGIN/,/END/p' file.txt
```

## 3️⃣ Advanced Tricks

### Every Nth line (GNU sed only)
```
sed -n '1~3p' file.txt    # every 3rd line
```

### From line N to end
```
sed -n '5,$p' file.txt
```


# 📌 Deleting Lines with sed
---

### Delete a single line:
```
sed '5d' file.txt
```
👉 Removes line 5.

### Delete a range of lines:
```
sed '10,20d' file.txt
```
👉 Removes lines 10–20.

### Delete from line N to the end:
```
sed '5,$d' file.txt
```
👉 Removes lines 5 to last.

## Delete by Pattern

### Delete lines containing a word:
```
sed '/error/d' file.txt
```

### Delete lines not containing a word:
```
sed '/error/!d' file.txt
```

### Delete lines starting with # (comments):
```
sed '/^#/d' file.txt
```

## Delete Ranges by Pattern

### Delete between two patterns:
```
sed '/BEGIN/,/END/d' file.txt
```
👉 Removes everything between BEGIN and END (inclusive).

## Advanced Deletion

### Delete every Nth line (GNU sed only):
```
sed '1~3d' file.txt
```
👉 Removes every 3rd line starting from line 1.

### Delete the last line:
```
sed '$d' file.txt
```

### Delete all blank lines:
```
sed '/^$/d' file.txt
```
