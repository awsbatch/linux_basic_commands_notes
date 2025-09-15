
#  what is touch command

The touch command in Linux is primarily used to modify the timestamps of a file. However, it is commonly used to create empty files. The command can change the access, modification, and change times of files and directories.

## Syntax
```
touch <options> <file or directory name>
```

**👉  To create an empty file, simply use the touch command followed by the filename:**
```
touch filename
```

**👉  Creating Multiple Files**
```
touch file1 file2 file3
```

**👉  For creating a series of files with appended numbering, use curly braces:**
```
touch file{1..10}
```

**👉  To change only the access time, use the -a option:**
```
touch -a filename
```

**👉  To change only the modification time, use the -m option:**
```
touch -m filename
```
