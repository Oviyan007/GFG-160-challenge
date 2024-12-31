
**💡 Day 36 Problem: Spirally Traversing a Matrix**

🧠 Approach:

1️⃣ Understand the Problem:

Given a 2D matrix, traverse it in a spiral order starting from the top-left corner, moving towards the right, then down, left, and back up in a circular pattern until all elements are visited.

2️⃣ Steps to Solve:

Initialize four boundaries:
top (starting row), bottom (last row), left (starting column), and right (last column).
Use a while loop to traverse the matrix as long as top <= bottom and left <= right:
Move Right: Traverse from left to right along the top row, then increment top.
Move Down: Traverse from top to bottom along the right column, then decrement right.
Move Left: Traverse from right to left along the bottom row, then decrement bottom.
Move Up: Traverse from bottom to top along the left column, then increment left.
Continue until all elements are visited.

**code**

    class Solution {
    // Function to return a list of integers denoting spiral traversal of matrix.
    public ArrayList<Integer> spirallyTraverse(int mat[][]) {
        // code here
        int m =mat.length;
        int n=mat[0].length;
        ArrayList<Integer> res=new ArrayList<>();
        
        int top=0,bottom=m-1,left=0,right=n-1;
        while(top<=bottom&&left<=right){
            for(int i=left;i<=right;++i){
                res.add(mat[top][i]);
            }
            top++;
            for(int i=top;i<=bottom;++i){
                res.add(mat[i][right]);
            }
            right--;
            if(top<=bottom){
                for(int i=right;i>=left;--i){
                    res.add(mat[bottom][i]);
                }
                bottom--;
                
            }
            if(left<=right){
                for(int i=bottom;i>=top;--i){
                    res.add(mat[i][left]);
                }
                left++;
            }
        }
        return res;
    }
    }
  

