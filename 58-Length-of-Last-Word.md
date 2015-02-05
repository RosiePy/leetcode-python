##Length of Last Word
Source: https://oj.leetcode.com/problems/length-of-last-word  
###Description


Given a string
s  
 consists of upper/lower-case alphabets and empty space characters
' '  
, return the length of last word in the string.  



If the last word does not exist, return 0.  



Note:  
 A word is defined as a character sequence consists of non-space characters only.  




For example,

Given
s  
 =
"Hello World"  
,  

return
5  
.  
###Tags
String  
###Solutions

####Solution 1
```
class Solution:
    # @param s, a string
    # @return an integer
    def lengthOfLastWord(self, s):
        return len(s.split()[-1].strip()) if s.strip() else 0
```
