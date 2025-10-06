# `sort` Command

- The sort command is used to arrange lines of text files in ascending or descending order.

## Basic Usage

### Sort Alphabetically
```
sort names.txt
```

**Input (names.txt):**
```
banana
apple
cherry
apple
```

**Output:**

apple
apple
banana
cherry

### Sort in Reverse Order
```
sort -r names.txt
```

**Output:**

cherry
banana
apple
apple


### Sort Numbers
```
sort -n numbers.txt
```

**Input (numbers.txt):**

10
5
20
3

### Sort by Column
```
sort -k2 -n data.txt
```

**Input (data.txt):**

Alice 25
Bob 30
Charlie 20

---
# `uniq` Command

- The uniq command filters out repeated lines from a file.
- ⚠️ Important: uniq works only on sorted data, so usually you use sort | uniq.

## Basic Usage

### Remove Duplicates
```
uniq names.txt
```

**Input (names.txt):**

apple
apple
banana
banana
cherry


### Count Duplicates
```
uniq -c names.txt
```

### Show Only Duplicates
```
uniq -d names.txt
```

### Show Only Unique Lines
```
uniq -u names.txt
```

## Combining sort + uniq

### Get Unique Values
```
sort names.txt | uniq
```

### Count Frequency
```
sort names.txt | uniq -c
```
