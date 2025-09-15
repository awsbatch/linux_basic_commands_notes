# What is less Command in Linux

The less command in Linux is a file pager used to view the contents of files or output one screen at a time.
It allows both forward and backward navigation, searching, and many powerful viewing options.

---

## Syntax:
```
less [options] [file...]
```

## 📑 Commonly Used Arguments (Table)
| Option       | Description                                                           |
|--------------|-----------------------------------------------------------------------|
| -E           | Automatically exit when reaching the end of the file                  |
| -f           | Force non-regular files (like device files) to be opened              |
| -F           | Exit if the entire file can be displayed on the first screen          |
| -g           | Highlight only the string found by the last search command            |
| -G           | Suppress highlighting of search matches                               |
| -i           | Ignore case while searching                                           |
| -n           | Suppress line numbers                                                 |
| -p pattern   | Start displaying at the first occurrence of the given pattern         |
| -s           | Squeeze multiple blank lines into a single line                       |


# ============ Practical Examples ==============

**👉 Open a file with less**
```
less file.txt
```
> 👉 Search for a word (press / then type the word)
> `/file`


**👉 Open a file and exit automatically if it fits on one screen**
```
less -F file.txt
```

**👉 Start at the first occurrence of a pattern**
```
less -p "error" logfile.txt
```

**👉 Ignore case when searching**
```
less -i file.txt
```

**👉 View compressed log files with zless**
```
zless file.log.gz
```
# 📌 less Command (Advanced Usage)

## 👉 1. Navigation keys

`Space` → Next screen

`b` → Previous screen

`Enter` → Next line

`k / ↑` → Up one line

`j / ↓` → Down one line

`G` → End of file

`g` → Beginning of file

**👉 2. Searching**
---
`/pattern` → Search forward

`?pattern` → Search backward

`n` → Repeat last search

`N` → Repeat last search in opposite direction
---
**👉 3. Follow a file (like tail -f)**
```
less +F logfile.txt
```

**👉 4. Quit less**
`q`
