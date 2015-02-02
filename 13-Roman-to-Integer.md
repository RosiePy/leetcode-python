##Roman to Integer
Source: https://oj.leetcode.com/problems/roman-to-integer  
###Description


Given a roman numeral, convert it to an integer.  



Input is guaranteed to be within the range from 1 to 3999.  
###Tags
Math, String  
###Solutions

#### Solution 1

Roman numerals to decimal.

```python
class Solution:
    # @return an integer
    def romanToInt(self, s):
        result = 0
        convert_dict = {
        'I': 1,
        'V': 5,
        'X': 10,
        'L': 50,
        'C': 100,
        'D': 500,
        'M': 1000
        }
        for i, v in enumerate(s):
            if i > 0 and convert_dict[v] > convert_dict[s[i-1]]:
                result += convert_dict[v] - 2*convert_dict[s[i-1]]
            else:
                result += convert_dict[s[i]]
        return result
```
