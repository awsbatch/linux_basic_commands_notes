sort Command

The sort command is used to arrange lines of text files in ascending or descending order.

🔹 Basic Usage
1️⃣ Sort Alphabetically
sort names.txt


Input (names.txt):

banana
apple
cherry
apple


Output:

apple
apple
banana
cherry

2️⃣ Sort in Reverse Order
sort -r names.txt


Output:

cherry
banana
apple
apple

3️⃣ Sort Numbers
sort -n numbers.txt


Input (numbers.txt):

10
5
20
3


Output:

3
5
10
20

4️⃣ Sort by Column
sort -k2 -n data.txt


Input (data.txt):

Alice 25
Bob 30
Charlie 20


Output (sorted by 2nd column, numeric):

Charlie 20
Alice 25
Bob 30

5️⃣ Ignore Case
sort -f words.txt


👉 Treats lowercase and uppercase as same.

📝 uniq Command

The uniq command filters out repeated lines from a file.
⚠️ Important: uniq works only on sorted data, so usually you use sort | uniq.

🔹 Basic Usage
1️⃣ Remove Duplicates
uniq names.txt


Input (names.txt):

apple
apple
banana
banana
cherry


Output:

apple
banana
cherry

2️⃣ Count Duplicates
uniq -c names.txt


Output:

2 apple
2 banana
1 cherry

3️⃣ Show Only Duplicates
uniq -d names.txt


Output:

apple
banana

4️⃣ Show Only Unique Lines
uniq -u names.txt


Output:

cherry

📝 Combining sort + uniq

Most often, we pipe sort into uniq.

1️⃣ Get Unique Values
sort names.txt | uniq

2️⃣ Count Frequency
sort names.txt | uniq -c


Output:

2 apple
1 banana
3 cherry

3️⃣ Find Most Frequent Word
sort names.txt | uniq -c | sort -nr | head -1


Output:

3 cherry


✅ With sort + uniq, you can do things like:

Sort data by column/number

Remove duplicates

Count occurrences

Find max/min frequency
