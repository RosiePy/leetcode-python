##Word Break
Source: https://oj.leetcode.com/problems/word-break  
###Description



Given a string
s  
 and a dictionary of words
dict  
, determine if
s  
 can be segmented into a space-separated sequence of one or more dictionary words.




For example, given  


s  
 =
"leetcode"  
,  


dict  
 =
["leet", "code"]  
.





Return true because
"leetcode"  
 can be segmented as
"leet code"  
.  
###Tags
Dynamic Programming  
###Solutions

#### Solution 1

动态规划的一个典型题目。

```python
class Solution:
    # @param s, a string
    # @param dict, a set of string
    # @return a boolean
    def wordBreak(self, s, dict):
        s_len = len(s)
        DP = [False]*(s_len+1)
        DP[0] = True
        for i in range(s_len):
            for j in range(i, s_len):
                if s[i:j+1] in dict and DP[i]:
                    DP[j+1] = True
        return DP[-1]
```
