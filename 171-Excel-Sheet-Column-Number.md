##Excel Sheet Column Number
Source: https://oj.leetcode.com/problems/excel-sheet-column-number  
###Description


Related to question
Excel Sheet Column Title  


Given a column title as appear in an Excel sheet, return its corresponding column number.  



For example:  


    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28



Credits:  
Special thanks to
@ts  
 for adding this problem and creating all test cases.  
###Tags
Math  
###Solutions

#### Solution 1

```python
class Solution:
    # @param s, a string
    # @return an integer
    def titleToNumber(self, s):
        base = ord('A') - 1
        col = 0
        for char in s:
            col = col*(ord('Z')-base)+(ord(char)-base)
            return col
```
