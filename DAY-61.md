Day 61 of GFG 160 Challenge 🚀
💡 Day 61 Problem: Equilibrium Point

🧠 Approach:
An equilibrium point in an array is an index where the sum of elements on the left equals the sum of elements on the right.

Steps to Solve:
1️⃣ Calculate Total Sum:

Compute the total sum of the array elements.
2️⃣ Traverse the Array:

Maintain a variable left_sum initialized to 0.
For each index, calculate the right_sum as:

right_sum=total_sum−left_sum−arr[i]
If left_sum == right_sum, the current index is the equilibrium point.
3️⃣ Update Left Sum:

Add the current element to left_sum and continue traversing.
4️⃣ Edge Case:

If no equilibrium point exists, return -1.


**code**

  
    class Solution {
    // Function to find equilibrium point in the array.
    public static int findEquilibrium(int arr[]) {
        // code here
        int preSum=0,total=0;
        for(int ele:arr){
            total+=ele;
        }
        for(int pivot=0;pivot<arr.length;pivot++){
            int suffsum=total-preSum-arr[pivot];
            if(preSum == suffsum){
                return pivot;
            }
            preSum +=arr[pivot];
        }
        return -1;
    }
    }
