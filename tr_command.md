# What `tr` Does

- `tr` reads from standard input (stdin) and writes to standard output (stdout).
-  It performs one of these actions:
    1. Translate characters — replace one set with another
    2. Delete characters
    3. Squeeze repeated characters

**It does not read files directly — you must use redirection or a pipe.**

## Basic Syntax
```
tr [options] SET1 [SET2]
```
| Parameter | Meaning                                           |
| --------- | ------------------------------------------------- |
| `SET1`    | Characters to match                               |
| `SET2`    | Characters to replace them with (for translation) |


### Basic Character Translation

**Replace all lowercase letters with uppercase:**
```
echo "linux server" | tr 'a-z' 'A-Z'
```

### Delete Characters (-d)

**Delete all digits:**
```
echo "abc123def456" | tr -d '0-9'
```

### Delete all spaces:
```
echo "text with spaces" | tr -d ' '
```

### Squeeze Repeated Characters `(-s)`
**s = squeeze (or “shrink”) consecutive identical characters into one.**
```
echo "hello     world" | tr -s ' '
```

### Combine Squeeze and Translation

**Convert spaces to tabs (like we used in your earlier example):**
```
df -h | tr -s ' ' '\t'
```

### Complement (`-c`)

**-c means complement the set — match everything except those characters.**

##### Example: remove everything except digits:
```
echo "abc123def456" | tr -cd '0-9\n'
```

| Set         | Matches                             |
| ----------- | ----------------------------------- |
| `a-z`       | Lowercase letters                   |
| `A-Z`       | Uppercase letters                   |
| `0-9`       | Digits                              |
| `[:alpha:]` | All letters                         |
| `[:digit:]` | All digits                          |
| `[:lower:]` | Lowercase letters                   |
| `[:upper:]` | Uppercase letters                   |
| `[:space:]` | Whitespace (spaces, tabs, newlines) |
| `[:punct:]` | Punctuation                         |
| `[:alnum:]` | Letters + digits                    |


```
echo "Hello, world!" | tr -d '[:punct:]'
```


## Limitations

  - `tr` works on single characters only, not words or strings.
  - → For multi-character replacements, use `sed` or `awk`.
  - It processes streams, not files directly — always `pipe` or `redirect`.
  - Doesn’t support regex — only character sets.


