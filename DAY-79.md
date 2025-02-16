**Day 79: Word Search**

Given a 2D board of letters and a word, check if the word exists in the grid. The word can be formed by adjacent letters (up, down, left, right) but cannot reuse the same letter in a single word path.

**🔹 Approach: Backtracking & DFS**
Start from Each Cell → If the first letter matches, explore further.
Depth-First Search (DFS) → Move in 4 directions (up, down, left, right) to form the word.
Mark Visited Cells → Temporarily change the cell value to avoid reusing it.
Backtrack if Needed → If a path fails, revert the cell and try another.
Return True if Found → If the entire word is formed, return true; otherwise, continue searching.



**code**

    class Solution {
    static boolean findMatch(char[][] mat, String word,int x,int y, int wIdx){
        int wLen= word.length();
        int n=mat.length;
        int m=mat[0].length;
        if(wIdx == wLen)
            return true;
        if(x<0 || y<0 || x >= n || y >= m)
            return false;
        if(mat[x][y] == word.chatAt(wIdx)){
            char temp=mat[x][y];
            mat[x][y]='#';
            
            boolean res=findMatch(mat, word, x-1,y,wIdx + 1) || findMatch(mat, word, x+1,y,wIdx + 1) || findMatch(mat, word, x,y-1,wIdx + 1)||findMatch(mat, word, x,y+1,wIdx + 1);
            mat[x][y]=temp;
            return res;
                        
        }
        
        return false;
    }
    static public boolean isWordExist(char[][] mat, String word) {
        // Code here
        int wLen= word.length();
        int n=mat.length;
        int m=mat[0].length;
        if(wLen > n*m)
            return false;
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(mat[i][j] == word.chatAt(0)){
                    if(findMatch(mat,word,i,j,0))
                        return true;
                }
            }
        }
        return false;
    }
    }
