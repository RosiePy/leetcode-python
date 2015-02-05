##Substring with Concatenation of All Words
Source: https://oj.leetcode.com/problems/substring-with-concatenation-of-all-words  
###Description



You are given a string,
S  
, and a list of words,
L  
, that are all of the same length. Find all starting indices of substring(s) in S that is a concatenation of each word in L exactly once and without any intervening characters.





For example, given:  


S  
:
"barfoothefoobarman"  


L  
:
["foo", "bar"]  






You should return the indices:
[0,9]  
.  

(order does not matter).  
###Tags
Hash Table, Two Pointers, String  
###Solutions

####Solution 1
```python
class Solution:
    # @param S, a string
    # @param L, a list of string
    # @return a list of integer
    def findSubstring(self, S, L):
        if not S or not L:
            return
        words = collections.defaultdict(int)
        for word in L:
            words[word] += 1

        res = []
        len_l, len_word = len(L)*len(L[0]), len(L[0])
        i = 0
        while i <= len(S) - len_l:
            word_set_temp = words.copy()
            j = 0
            while j < len(L):
                sub_string = S[i+j*len_word: i+(j+1)*len_word]
                if sub_string in word_set_temp:
                    if word_set_temp[sub_string] == 1:
                        del word_set_temp[sub_string]
                    else:
                        word_set_temp[sub_string] -= 1
                    j += 1
                else:
                    break
            if not word_set_temp:
                res.append(i)
            i += 1
        return res
```
