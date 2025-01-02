
**💡 Day 38 Problem: Search in a Row-Column Sorted Matrix**

🧠 Approach:
1️⃣ Understand the Problem:

Given an 
𝑁
×
𝑀
N×M matrix where each row and column is sorted in ascending order, find whether a target element exists in the matrix.
2️⃣ Steps to Solve:

Start from the top-right corner of the matrix.
If the current element equals the target, return true.
If the current element is larger than the target, move left.
If the current element is smaller than the target, move down.
Repeat until you find the element or go out of bounds.

**code**

    class Solution {
    public static boolean matSearch(int mat[][], int x) {
        // your code here
        int n=mat.length,m=mat[0].length;
        int i=0,j=m-1;
        while(i<n&&j>=0){
            if(x>mat[i][j]){
                i++;
            }
            else if(x<mat[i][j]){
                j--;
            }
            else{
                return true;
            }
        }
        return false;
    }
    }
