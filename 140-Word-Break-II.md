##Word Break II
Source: https://oj.leetcode.com/problems/word-break-ii  
###Description



Given a string
s  
 and a dictionary of words
dict  
, add spaces in
s  
 to construct a sentence where each word is a valid dictionary word.





Return all such possible sentences.





For example, given  


s  
 =
"catsanddog"  
,  


dict  
 =
["cat", "cats", "and", "sand", "dog"]  
.





A solution is
["cats and dog", "cat sand dog"]  
.  
###Tags
Dynamic Programming, Backtracking  
###Solutions

#### Solution 1

这道题我先用了DP判断是否能构造这个词。并用一个dictionary记录构造的信息。
然后从后往前构造。

```python
class Solution:
    # @param s, a string
    # @param dict, a set of string
    # @return a list of strings
    def wordBreak(self, s, dict):
        res = []
        def buildPath(path, index):
            if index == 0:
                res.append(" ".join(reversed(path[:])))
                return
            else:
                for neighbor in marks[index]:
                    path.append(neighbor[1])
                    buildPath(path, neighbor[0])
                    path.pop()

        wordDict = set(dict)
        indicator, marks = [False]*(len(s)+1), {}
        indicator[0] = True
        for i in range(len(s)):
            for j in range(i, len(s)):
                if s[i:j+1] in wordDict and indicator[i]:
                        indicator[j+1] = True
                        if j+1 not in marks:
                            marks[j+1] = set([(i,s[i:j+1])])
                        else:
                            marks[j+1].add((i, s[i:j+1]))
        if not indicator[-1]:
            return []
        buildPath([], len(s))
        return res
```
