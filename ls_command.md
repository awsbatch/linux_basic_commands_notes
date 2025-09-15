# Linux File Server Setup

## 🚀 Installation
1. Update your system:
   ```bash
   sudo apt update && sudo apt upgrade -y
# What is ls Command Arguments in Linux

The `ls` command is a fundamental utility in Linux used to list files and directories.  
It supports various arguments (options) to customize its output, making it versatile for file management tasks.  

---

## Syntax:


---

## 📑 Commonly Used Arguments (Table)

| Argument       | Description                                                                 |
|----------------|-----------------------------------------------------------------------------|
| `-l`           | Long listing format (permissions, owner, size, date, etc.)                 |
| `-a`           | Show **all** files, including hidden ones (`.` files)                      |
| `-A`           | Like `-a`, but excludes `.` (current dir) and `..` (parent dir)            |
| `-h`           | Human-readable sizes (1K, 234M, 2G)                                        |
| `-t`           | Sort by modification time (newest first)                                   |
| `-r`           | Reverse sort order                                                        |
| `-R`           | Recursively list subdirectories                                            |
| `-S`           | Sort by file size (largest first)                                          |
| `-i`           | Show inode numbers                                                        |
| `-d`           | Show directories themselves, not their contents                           |
| `-F`           | Append symbol to names (`/` dir, `*` executable, `@` symlink)             |
| `--color=auto` | Add colors to output (to distinguish file types)                          |

---

## 📝 Practical Examples

👉 **List all files, including hidden ones:**
