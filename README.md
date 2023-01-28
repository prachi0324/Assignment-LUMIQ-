# Assignment-LUMIQ-
Title: Matrix script

Neo has a complex matrix script. The matrix script is a  N * M  grid of strings. It consists of alphanumeric characters, spaces and symbols (!,@,#,$,%,&).

![Alt text](1442753362-1075bd12d9-Capture.jpeg "Screen")

To decode the script, Neo needs to read each column and select only the alphanumeric characters and connect them. Neo reads the column from top to bottom and starts reading from the leftmost column.

If there are symbols or spaces between two alphanumeric characters of the decoded script, then Neo replaces them with a single space '' for better readability.

Neo feels that there is no need to use 'if' conditions for decoding.
Alphanumeric characters consist of: [A-Z, a-z, and 0-9].

Input Format

The first line contains space-separated integers N (rows) and M (columns) respectively.
The next  lines contain the row elements of the matrix script.
Constraints

0 < N, M < 100

Note: A 0 Score will be awarded for using 'if' conditions in your code.

Output Format

Print the decoded matrix script.

Sample Input 0

7 3
Tsi
h%x
i #
sM 
$a 
#t%
ir!


Sample Output

This is Matrix#  %!



Solution:
```
#!/bin/python3

import math
import os
import random
import re
import sys




first_multiple_input = input().rstrip().split()

n = int(first_multiple_input[0])

m = int(first_multiple_input[1])

matrix = []

for _ in range(n):
    matrix_item = input()
    matrix.append(matrix_item)

matrix = list(zip(*matrix))

sample = str()

for words in matrix:
    for char in words:
        sample += char
       
print(re.sub(r'(?<=\w)([^\w\d]+)(?=\w)', ' ', sample)) 

```






Tile: Regex and Parsing

A valid postal code  have to fullfil both below requirements:

1. P must be a number in the range from 100000 to 999999 inclusive.
2. P must not contain more than one alternating repetitive digit pair.
Alternating repetitive digits are digits which repeat immediately after the next digit. In other words, an alternating repetitive digit pair is formed by two equal digits that have just a single digit between them.

For example:
```
121426 # Here, 1 is an alternating repetitive digit.
523563 # Here, NO digit is an alternating repetitive digit.
552523 # Here, both 2 and 5 are alternating repetitive digits.
```
Your task is to provide two regular expressions ```regex_integer_in_range``` and ```regex_alternating_repetitive_digit_pair```. Where:
```regex_integer_in_range``` should match only integers range from 100000 to 999999  inclusive
```regex_alternating_repetitive_digit_pair``` should find alternating repetitive digits pairs in a given string.

Both these regular expressions will be used by the provided code template to check if the input string P is a valid postal code using the following expression:

```
(bool(re.match(regex_integer_in_range, P)) 
and len(re.findall(regex_alternating_repetitive_digit_pair, P)) < 2)
```

Input Format

Locked stub code in the editor reads a single string denoting P from stdin and uses provided expression and your regular expressions to validate if P is a valid postal code.

Output Format

You are not responsible for printing anything to stdout. Locked stub code in the editor does that.

Sample Input 0
```
110000
```
Sample Output 0
```
False
```


Solution:

```
regex_integer_in_range = r"^[1-9][\d]{5}$"	
regex_alternating_repetitive_digit_pair = r"(\d)(?=\d\1)"


import re
P = input()

print (bool(re.match(regex_integer_in_range, P)) 
and len(re.findall(regex_alternating_repetitive_digit_pair, P)) < 2)
```
