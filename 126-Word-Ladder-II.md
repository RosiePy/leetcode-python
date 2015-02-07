##Word Ladder II
Source: https://oj.leetcode.com/problems/word-ladder-ii  
###Description



Given two words (  
start  
 and
end  
), and a dictionary, find all shortest transformation sequence(s) from
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





Return  



  [
    ["hit","hot","dot","dog","cog"],
    ["hit","hot","lot","log","cog"]
  ]







Note:  




All words have the same length.  


All words contain only lowercase alphabetic characters.  
###Tags
Array, Backtracking, Breadth-first Search, String  
###Solutions

### Solution 1

```python
class Solution:
    # @param start, a string
    # @param end, a string
    # @param dict, a set of string
    # @return a list of lists of string
    def findLadders(self, start, end, dict):
        def build_path(word, path):
            for neighbor in parent_dict[word]:
                if neighbor == start:
                    res.append([start] + path[::-1] + [end])
                else:
                    path.append(neighbor)
                    build_path(neighbor, path)
                    path.pop()
        res = []
        isReachable = False
        dict.add(start)
        dict.add(end)
        #graph = collections.defaultdict(set)
        #visited = collections.defaultdict(int)
        #parent_dict = collections.defaultdict(set)
        graph = {word: set() for word in dict}
        visited = {word: 0 for word in dict}
        parent_dict = {word: set() for word in dict}
        for word in dict:
            for i in range(len(word)):
                for char in "abcdefghijklmnopqrstuvwxyz":
                    if char != word[i]:
                        new_word = word[:i] + char + word[i+1:]
                        if new_word in dict:
                            graph[word].add(new_word)
        q = collections.deque()
        q.append((start, 1))
        visited[start] = 1
        end_level = 1000
        while q:
            word, level = q.popleft()
            if level > end_level:
                break
            for neighbor in graph[word]:
                if neighbor in dict:
                    if visited[neighbor] in set([0, level+1]):
                        visited[neighbor] = level+1
                        parent_dict[neighbor].add(word)
                        q.append((neighbor, level+1))
                        if neighbor == end:
                            isReachable = True
                            end_level = level + 1
        if isReachable:
            build_path(end, [])
        return res
```
