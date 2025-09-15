# What is rm command

`rm` stands for ‘remove‘, as the name suggests rm command is used to delete or remove files and directory in Linux and UNIX like operating systems. If you are new to Linux then you should be very careful while running rm command because once you delete the file or directory then you can not recover the contents of file and directory
The `rm` command in Linux is used to remove files or directories. It is a powerful tool, so caution is advised as deleted files cannot be easily recovered.


## Syntax
```
rm [options] file_or_directory
```

---
## Examples


**👉  Remove a Single File**
```
rm file.txt
```

> This deletes file.txt from the current directory.

**👉  Remove Multiple Files**
```
rm file1.txt file2.txt
```
> Deletes both file1.txt and file2.txt.

**👉  Remove Files Interactively**
```
rm -i file.txt
```
> Prompts for confirmation before deleting file.txt.

**👉  Remove All Files in a Directory**
```
rm *
```
> Deletes all files in the current directory (but not subdirectories).

**👉  Remove a Directory and Its Contents Recursively**
```
rm -r directory_name
```
> Deletes the directory directory_name and all its contents (files and subdirectories).

**👉  Force Deletion Without Prompt**
```
rm -f file.txt
```
> Deletes file.txt without asking for confirmation.

**👉  Combine Options for Recursive and Forceful Deletion**
```
rm -rf directory_name
```
> Deletes directory_name and all its contents without any prompts.

## 👉  Important Notes

**Be Careful:** 
> The rm command does not move files to a trash bin; they are permanently deleted.
Use -i for Safety: Adding the -i option ensures you confirm each deletion, reducing accidental data loss.
Avoid rm -rf /: This command can delete the entire filesystem and should never be used unless you are absolutely sure of its consequences.
