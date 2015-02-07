##Word Search
Source: https://oj.leetcode.com/problems/word-search  
###Description



Given a 2D board and a word, find if the word exists in the grid.




The word can be constructed from letters of sequentially adjacent cell, where "adjacent" cells are those horizontally or vertically neighboring. The same letter cell may not be used more than once.





For example,  

Given
board  
 =


[
  ["ABCE"],
  ["SFCS"],
  ["ADEE"]
]




word  
 =
"ABCCED"  
, -> returns
true  
,  


word  
 =
"SEE"  
, -> returns
true  
,  


word  
 =
"ABCB"  
, -> returns
false  
.  
###Tags
Array, Backtracking  
###Solutions

#### Solution 1
```python
class Solution:
    # @param board, a list of lists of 1 length string
    # @param word, a string
    # @return a boolean
    def exist(self, board, word):
        if not board:
            return True if not word else False
        visited = {(i, j): False for i in range(len(board)) for j in range(len(board[0]))}
        for i in range(len(board)):
            for j in range(len(board[0])):
                if self.search(word, visited, board, 0, i, j):
                    return True
        return False
    def search(self, word, visited, board, index, i, j):
        if i < 0 or i >= len(board) or j < 0 or j >= len(board[0]) or word[index] != board[i][j]:
            return False
        if not visited[(i, j)]:
            if len(word) == index+1:
                return True
            visited[(i,j)] = True
            res = self.search(word, visited, board, index+1, i-1, j) or self.search(word, visited, board,index+1, i+1, j) or self.search(word, visited, board, index+1, i, j-1) or self.search(word, visited, board, index+1, i, j+1)
            visited[(i,j)] = False
            return res
```
