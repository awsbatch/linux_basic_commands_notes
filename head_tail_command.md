# What is head and tail command in linux ?
`tail` is a Linux command used to view the end (last lines) of a file.
By default, it prints the last 10 lines.
It’s most commonly used for log monitoring because it can follow a file as it grows.


`head` is a Linux/Unix command used to view the beginning (top lines) of a file.
By default, it prints the first 10 lines of the file.
It’s commonly used to preview files, check headers, or quickly examine large files without opening the whole thing.

---
## head command : Displays the beginning of a file.

### Syntax
```
head [options] [file...]
```
#### Common Use Cases

**Show first 10 lines (default):**
```
head file.txt
```

**Show first N lines:**
```
head -n 20 file.txt
```

**Show first N bytes:**
```
head -c 50 file.txt
```
> (prints first 50 characters/bytes)

**Check file structure:**
```
head /etc/passwd
```

---
## tail command

**👉 Displays the end of a file.**

### Syntax
```
tail [options] [file...]
```
### Common Use Cases

**Show last 10 lines (default):**
```
tail file.txt
```

**Show last N lines:**
```
tail -n 20 file.txt
```

**Show last N bytes:**
```
tail -c 100 file.txt
```

**Monitor logs in real-time:**
```
tail -f /var/log/syslog
```
> 👉 Keeps following new lines as they are appended. Perfect for watching logs.

**Follow multiple files at once:**
```
tail -f /var/log/nginx/access.log /var/log/nginx/error.log
```

## Key Differences: head vs tail

| Feature               | `head`             | `tail`                    |
| --------------------- | ------------------ | ------------------------- |
| Default output        | First 10 lines     | Last 10 lines             |
| Use with `-n`         | Top N lines        | Bottom N lines            |
| Use with `-c`         | First N bytes      | Last N bytes              |
| Dynamic follow (`-f`) | ❌ Not supported    | ✔️ Yes, follow new data   |
| Common usage          | Preview file start | Monitor logs, file growth |
