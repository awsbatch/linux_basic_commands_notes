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

# sed Search & Replace Concepts

### Basic Syntax
```
sed 's/pattern/replacement/' file
```
  - `s` → substitute command
  - `pattern` → regex pattern to search for
  - `replacement` → text to replace it with
> **Note** : By default, only the first occurrence per line is replaced.

### Replace All Occurrences in a Line
Use the g (global) flag:
```
sed 's/cat/dog/g' animals.txt
```
> ➡️ Every "cat" becomes "dog" in each line.

### Case-Insensitive Replacement
Use the i flag:
```
sed 's/cat/dog/gi' animals.txt
```
> ➡️ Replaces "cat", "Cat", "CAT", etc.

### In-Place Editing
Modify the file directly with -i:
```
sed -i 's/cat/dog/g' animals.txt
```
> ➡️ File is updated in-place (⚠️ irreversible unless you back it up).

**Backup version:**
```
sed -i.bak 's/cat/dog/g' animals.txt
```
> ➡️ Creates animals.txt.bak before editing.


### Replace by Line Numbers
Replace only in a specific line:
```
sed '3s/cat/dog/' animals.txt
```
> ➡️ Replaces only on line 3.

### Replace in a range:
```
sed '2,5s/cat/dog/g' animals.txt
```
> ➡️ Replaces from line 2 to 5.

### From line 2 to end:
```
sed '2,$s/cat/dog/g' animals.txt
```

### Replace Only the Nth Occurrence
```
sed 's/cat/dog/2' animals.txt
```

### Delete or Blank Out Matches
Delete lines containing pattern:
```
sed '/cat/d' animals.txt
```

### Replace match with nothing:
```
sed 's/cat//g' animals.txt
```

### Multiple Replacements
Chain replacements with `-e` or semicolons:
```
sed -e 's/cat/dog/g' -e 's/mouse/rabbit/g' file
```
```
sed 's/cat/dog/g; s/mouse/rabbit/g' file
```

### Conditional Replacement
Only replace if another pattern matches:
```
sed '/lion/s/cat/dog/g' animals.txt
```
> **➡️ Replace "cat" with "dog" only on lines containing "lion".**


## Advanced Tricks

### Replace and print modified lines only:
```
sed -n 's/cat/dog/p' animals.txt
```

### Insert before replacement:
```
sed 's/cat/[ANIMAL]&/' animals.txt
```
> ➡️ Turns "cat" → "[ANIMAL]cat".
