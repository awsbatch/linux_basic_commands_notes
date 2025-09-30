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
