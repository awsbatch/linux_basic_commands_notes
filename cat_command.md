# what is `cat` Command ?
cat is one of the most common and useful Linux commands. Its name comes from concatenate because it can join files together, but people often use it just to quickly read file contents.

## Syntax
```
cat [options] [file...]
```
### Common Use Cases
**1. View file content**
```
cat file.txt
```
> 👉 Prints the entire file to standard output.

**2. View multiple files**
```
cat file1.txt file2.txt
```
> 👉 Prints both files one after another (concatenated).

**3. Create a new file**
```
cat > newfile.txt
```
> 👉 Starts taking input from keyboard. Type your text and press CTRL+D to save and exit.
> (Be careful: if file exists, it will be overwritten ❗)

**4. Append text to a file**
```
cat >> existing.txt
```
> 👉 Appends your typed text to the end of existing.txt. Exit with CTRL+D.

**5. Number lines**
```
cat -n file.txt
```
> 👉 Displays file with line numbers.

**6. Show non-printing characters**
```
cat -v file.txt
```
> 👉 Useful for debugging invisible characters.

**7. Redirect output to another file**
```
cat file1.txt file2.txt > combined.txt
```
> 👉 Merges files into combined.txt.

**8. Use with pipe**
```
cat file.txt | grep "ERROR"
```
> 👉 Combine cat with tools like grep, less, sort, etc.

## Options Cheatsheet
| Option | Description                           |
| ------ | ------------------------------------- |
| `-n`   | Number all output lines               |
| `-b`   | Number non-blank lines only           |
| `-s`   | Squeeze multiple blank lines into one |
| `-E`   | Show `$` at end of each line          |
| `-T`   | Show `^I` instead of tab characters   |

### 💡 Pro tip: If a file is huge, don’t use cat file.log (it will flood your terminal). Instead use:

`less file.log`
