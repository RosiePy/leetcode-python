##Word Ladder
Source: https://oj.leetcode.com/problems/word-ladder  
###Description



Given two words (  
start  
 and
end  
), and a dictionary, find the length of shortest transformation sequence from
start  
 to
end  
, such that:





Only one letter can be changed at a time  


Each intermediate word must exist in the dictionary  






For example,




Given:  


start  
 =
"hit"  


end  
 =
"cog"  


dict  
 =
["hot","dot","dog","lot","log"]  





As one shortest transformation is
"hit" -> "hot" -> "dot" -> "dog" -> "cog"  
,  

return its length
5  
.






Note:  




Return 0 if there is no such transformation sequence.  


All words have the same length.  


All words contain only lowercase alphabetic characters.  
###Tags
Breadth-first Search  
###Solutions

### Solution 1
```python
class Solution:
    # @param start, a string
    # @param end, a string
    # @param dict, a set of string
    # @return an integer
    def ladderLength(self, start, end, dict):
        if len(dict) == 0:
            return 0
        wordsQueue = collections.deque()
        wordsQueue.append((start, 1))
        dict.add(end)
        while(wordsQueue):
            cur, curDistance = wordsQueue.popleft()
            for i in range(len(cur)):
                for j in 'abcdefghijklmnopqrstuvwxyz':
                    newWord = cur[:i]+j+cur[i+1:]
                    if newWord == end:
                        return curDistance + 1
                    if newWord in dict:
                        wordsQueue.append((newWord, curDistance + 1))
                        dict.remove(newWord)
        return 0
```
