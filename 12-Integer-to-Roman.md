##Integer to Roman
Source: https://oj.leetcode.com/problems/integer-to-roman  
###Description


Given an integer, convert it to a roman numeral.




Input is guaranteed to be within the range from 1 to 3999.  
###Tags
Math, String  
###Solutions

#### Solution 1


```python

class Solution:
    # @return a string
    def intToRoman(self, num):
        res = []
        anums = [1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1]
        rnums = "M CM D CD C XC L XL X IX V IV I".split()
        for a, r in zip(anums, rnums):
            n, num = divmod(num, a)
            res.append(r*n)
        return ''.join(res)
```
