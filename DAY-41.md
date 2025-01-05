**💡 Day 41 Problem: Set Matrix Rows and Columns to Zeros**

**🧠 Approach:**


1️⃣ First, identify which rows and columns need to be set to zero. Use the first row and first column of the matrix as markers to record this information.

Traverse the matrix to find zero elements.
Mark the corresponding first-row and first-column cells.
2️⃣ Next, iterate through the matrix again (skipping the first row and column) and set cells to zero based on the markers.

3️⃣ Finally, handle the first row and first column separately based on whether they were marked initially.

This approach ensures you use 
O(1) additional space while keeping the time complexity at 
O(N×M).

**code**

      class Solution {
    public void setMatrixZeroes(int[][] mat) {
        int n=mat.length,m=mat[0].length;
        boolean []rows=new boolean[n];
        boolean []cols=new boolean[m];
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(mat[i][j]==0){
                    rows[i]=true;
                    cols[j]=true;
                }
            }
        }
        for(int i=0;i<n;i++){
            for(int j=0;j<m;j++){
                if(rows[i]||cols[j]){
                    mat[i][j]=0;
                }
            }
        }
    }
      }
