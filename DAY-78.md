**Day 78: Sudoku Solver**
Sudoku is a 9×9 grid puzzle where each row, column, and 3×3 subgrid must contain digits from 1 to 9 without repetition.

**🔹 Approach: Backtracking**
Find an Empty Cell → Start from the top-left and find the first empty (0 or '.') cell.
Try Numbers 1-9 → Place a number and check if it follows Sudoku rules.
Check Validity → Ensure no duplicate exists in the row, column, or subgrid.
Backtrack if Needed → If no valid number fits, reset the cell and go back.
Repeat Until Solved → Continue filling until the grid is complete.

**code**

    class Solution {
    // Function to find a solved Sudoku.
    static boolean isSafe(int[][] mat,int num,int[]row,int[] col,int[]box,int i,int j ){
        if((row[i] & (1<<num)) !=0 || (col[j] & (1<< num)) !=0 || (box[i/3*3+j/3] &(1<< num)) !=0)
            return false;
        return true;
    }
    static boolean solveSudokuRec(int[][] mat,int i,int j,int[] row,int[] col,int[] box) {
        // code here
       int n=mat.length;
       if(i == n - 1 && j==n)
        return true;
       if(j == n){
           i++;
           j=0;
       }
       if(mat[i][j] != 0)
        return solveSudokuRec(mat,i,j+1,row,col,box);
       for(int num=1;num<n;num++){
           if(isSafe(mat,i,j,num,row,col,box)){
               mat[i][j]=num;
               row[i]|=(1<<num);
               col[j]|=(1<<num);
               box[i/3*3+j/3]|=(1<<num);
               if(solveSudokuRec(mat,i,j + 1,row,col,box))
                    return true;
                mat[i][j]=0;
                row[i]&= ~(1<<num);
                col[j]&= ~(1<<num);
                box[i/3*3+j/3] &= ~(1<<num);
           }
       }
       return false;
        
    }
    static void solveSudoku(int [][] mat){
        int n=mat.length;
        int [] row=new int[n];
        int [] col=new int[n];
        int [] box=new int[n];
        
        for(int i=0;i<n;i++){
            for(int j=0;j<n;j++){
                if(mat[i][j]!=0){
                    row[i]|=(1<<mat[i][j]);
                    col[j]|=(1<<mat[i][j]);
                    box[(i/3)*3+j/3] |= (1<< mat[i][j]);
                }
            }
        }
        solveSudokuRec(mat,0,0,row,col,box);
    }
    }
