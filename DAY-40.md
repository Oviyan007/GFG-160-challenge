
**💡 Day 40 Problem: Search in a Sorted Matrix**

🧠 Approach:

When you’re dealing with a matrix sorted both row-wise and column-wise, you can leverage its structure for a faster search. Here's the plan:

1️⃣ Start from the top-right corner of the matrix. Why here? It allows you to decide where to move next based on the comparison:

If the target is smaller than the current element, move left.
If the target is larger, move down.
2️⃣ Continue this process. You’ll either find the target or run out of bounds, confirming it’s not there.

This approach keeps things efficient with a time complexity of O(N+M), as you’re only traversing rows or columns once.

Check out my solution and code here.

What’s your go-to strategy for matrix problems? Let’s discuss in the comments! 🙌



**code**

    class Solution {
    // Function to search a given number in row-column sorted matrix.
    public boolean searchMatrix(int[][] mat, int x) {
        int n=mat.length,m=mat[0].length;
        int lo=0,high=n*m-1;
        while(lo<=high){
            int mid=(lo+high)/2;
            int row=mid/m;
            int col=mid%m;
            if(mat[row][col] == x)
                return true;
            if(mat[row][col]<x){
                lo=mid+1;
            }
            else{
                high=mid-1;
            }
        }
        return false;
    }
    }
