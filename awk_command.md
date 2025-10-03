# What is `awk`?

  - `AWK` is a pattern scanning and text processing language.
  - It works line by line, breaking each line into fields (columns).
  - Fields are separated by a delimiter (default = whitespace).

## Syntax:
```
awk 'pattern { action }' file
```
### Data

```
Model				Country			Cost

BMW					Germany			$25000
Volvo				Sweden			$15000
Subaru			Japan			  $2500
Ferrari 		Italy			  $2000000
SAAB				USA				  $3000
```

### Print Entire Line
```
awk '{print}' file.txt
```
> Prints every line (like cat).

### Print Specific Column (Field)
```
awk '{print $1}' file.txt
```
> Prints the first field (column).

**If file.txt contains:**
```
Alice 25 Developer
Bob 30 Admin
```

**Output:**
```
Alice
Bob
```

### Print Multiple Columns
```
awk '{print $1, $3}' file.txt
```
> Prints 1st and 3rd fields:

```
awk '{print $2 "\t" $3}' file.txt
```

### Printing all lines that match a specific pattern
> if you want to print lines that match a certain pattern, the syntax is as shown
```
awk '/variable_to_be_matched/ {print $0}' file.txt
```

### Print Line Numbers
```
awk '{print NR, $0}' file.txt
```
> NR = line number, $0 = whole line.

### Use a Custom Delimiter
```
awk -F: '{print $1}' /etc/passwd
```
> Prints usernames (first field) from /etc/passwd where : is delimiter.

## Pattern Matching
```
awk '/Alice/ {print $0}' file.txt
```
> Prints lines that contain Alice.


## AWK built-in variable

| Variable  | Meaning                            |
| --------- | ---------------------------------- |
| `$0`      | Entire line                        |
| `$1,$2..` | Fields                             |
| `NR`      | Line number                        |
| `NF`      | Number of fields                   |
| `FNR`     | Line number per file               |
| `FS`      | Field separator (input)            |
| `OFS`     | Output field separator             |
| `RS`      | Record separator (default newline) |
| `ORS`     | Output record separator            |

---
## Sample File (data.txt)
```
Alice 25 Developer
Bob 30 Admin
Charlie 28 Manager
```
## Example:

### `$0` → Entire line
```
awk '{print $0}' data.txt
```

### `$1, $2, ...` → Fields
```
awk '{print $1, $2}' data.txt
```
> `$1` = first column, `$2` = second column.

### `NR` → Line number
```
awk '{print NR, $0}' data.txt
```

### `NF` → Number of fields
```
awk '{print $1, "has", NF, "fields"}' data.txt
```

**OR**

```
awk '{print $1, "has", NF }' data.txt
```

### `FNR` → Line number per file
```
awk '{print FILENAME, FNR, $0}' data.txt data-1.txt
```

