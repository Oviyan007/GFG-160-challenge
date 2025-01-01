
**💡 Day 37 Problem: Rotate Matrix by 90 Degrees**


🧠 Approach:
1️⃣ Understand the Problem:

Given an 
𝑁×𝑁
N×N matrix, rotate it 90 degrees clockwise in place.

2️⃣ Steps to Solve:
Transpose the Matrix:
Swap elements 
This converts rows into columns.
Reverse Rows:
For each row in the transposed matrix, reverse the order of elements to achieve the 90-degree rotation.

**code**

    class Solution {
    // Function to rotate matrix anticlockwise by 90 degrees.
    static void rotateby90(int mat[][]) {
        // code here
        int n=mat.length;
        int res[][]=new int[n][n];
        for(int i=0;i<n;i++){
            for(int j=0;j<n;j++){
                res[n-j-1][i]=mat[i][j];
            }
            
        }
        for(int i=0;i<n;i++){
            System.arraycopy(res[i],0,mat[i],0,n);
        }
    }
    }
