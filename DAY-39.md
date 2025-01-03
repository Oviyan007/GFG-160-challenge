Day 39 of GFG 160 Challenge 🚀
💡 Day 39 Problem: Search in a Row-Wise Sorted Matrix

🧠 Approach:

Treat the matrix as a flattened sorted array with indices mapped as:
Row = index//𝑀 index//M
Column = index%𝑀index%M.
Use binary search:
Start with low = 0 and high = 𝑁×𝑀−1
Calculate the mid-point and map it to matrix coordinates.
Compare mid-value with the target and adjust the search range accordingly.

**code**
        class Solution {
    // Function to search a given number in row-column sorted matrix.
    
    static boolean search(int[]arr,int x){
        int lo=0,hi=arr.length-1;
        while(lo<=hi){
            int mid =(lo+hi)/2;
            if(x==arr[mid])
                return true;
            if(x<arr[mid])
                hi=mid-1;
            else
                lo=mid+1;
        }
        return false;
    }
    public boolean searchRowMatrix(int[][] mat, int x) {
        // code here
        int n=mat.length,m=mat[0].length;
        for(int i=0;i<n;i++){
            if(search(mat[i],x))
                return true;
        }
        return false;
    }
      }
