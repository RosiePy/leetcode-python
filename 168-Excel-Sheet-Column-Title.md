##Excel Sheet Column Title
Source: https://oj.leetcode.com/problems/excel-sheet-column-title  
###Description


Given a positive integer, return its corresponding column title as appear in an Excel sheet.  



For example:  



    1 -> A
    2 -> B
    3 -> C
    ...
    26 -> Z
    27 -> AA
    28 -> AB



Credits:  
Special thanks to
@ifanchu  
 for adding this problem and creating all test cases.  
###Tags
Math  
###Solutions

#### Solution 1

This problem is essentially a base conversion problem. A number is converted from decimal to another system.
```python
class Solution:
    # @return a string
    def convertToTitle(self, num):
        res = ""
        while num > 0:
            s = chr((num-1)%26+ord('A')) + s
            num = (num-1)/26
        return s
```
