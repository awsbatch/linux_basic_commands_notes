![Alt text](https://linuxhandbook.com/content/images/2020/06/mkdir-command-1.png)


# What is mkdir command

The mkdir command in Linux is used to create directories. It is a simple yet powerful command with various options to customize directory creation.
Basic Syntax

## Syntax
```
 mkdir [OPTION] DIRECTORY_NAME
```

---
## Common Options

- `-p`: Create parent directories as needed.
- `-m`: Set permissions for the directory.
- `-v`: Display a message for each created directory.

### Some common use case of mkdir command

---

**👉  Create a Single Directory**
```
mkdir my_folder
```

> This creates a directory named my_folder in the current working directory.


**👉  Create Multiple Directories**
```
mkdir folder1 folder2 folder3
```

> This creates three directories: folder1, folder2, and folder3.

**👉  Create Parent Directories**
```
mkdir -p parent/child/grandchild
```

>The -p option creates the entire directory structure, even if the parent directories do not exist.

**👉  Set Permissions While Creating**
```
mkdir -m 755 secure_folder
```

> The -m option sets permissions (e.g., 755) for the directory during creation.

**👉  Verbose Output**
```
mkdir -v new_folder
```

>The -v option provides a message confirming the creation of the directory.


**👉  Avoid Overwriting Existing Directories**
```
mkdir -p existing_folder
```

> Using -p ensures no error is thrown if the directory already exists.

## Advance form of `mkdir` command

**👉 Basic Example: Create a tree in one go**
```
mkdir -p project/{docs,src/{frontend,backend},tests}
```

### This Creates:
```
project/
├── docs/
├── src/
│   ├── frontend/
│   └── backend/
└── tests/
```

**👉 Nested folders for a file server**
```
mkdir -p /srv/shares/{staff,students,finance/{reports,2025}}
```
**Structure:**
```
/srv/shares/
├── staff/
├── students/
└── finance/
    ├── reports/
    └── 2025/
```
