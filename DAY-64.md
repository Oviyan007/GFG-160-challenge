
💡 Day 64 Problem: Product of Array Except Self

🧠 Approach:
The task is to find a new array where each element at index i is the product of all the elements in the array except the one at i.

Key Constraint:
Solve the problem without division.
Steps to Solve:
1️⃣ Two Pass Solution (Left and Right Products):

Create two auxiliary arrays:
left[]: Stores the cumulative product of elements to the left of each index.
right[]: Stores the cumulative product of elements to the right of each index.
Multiply the values from left[] and right[] to get the result.

**code**

    class Solution {
    public static int[] productExceptSelf(int arr[]) {
        // code here
        
        int n =arr.length;
        int [] prefProduct=new int[n];
        int [] suffProduct=new int[n];
        int [] res=new int[n];
        prefProduct[0]=1;
        for(int i=1;i<n;i++)
            prefProduct[i]=arr[i-1]*prefProduct[i-1];
            
        suffProduct[n-1]=1;
        for(int j=n-2;j>=0;j--)
            suffProduct[j]=arr[j+1]*suffProduct[j+1];
            
        for(int i=0;i<n;i++)
            res[i]=prefProduct[i]*suffProduct[i];
        return res;
        
    }
    }
