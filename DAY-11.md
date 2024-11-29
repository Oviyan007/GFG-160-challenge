**Maximum Product Subarray**

🧠 Approach:
1️⃣ Understand the Problem:

Find the maximum product of a contiguous subarray in a given array of integers (which may include positive, negative, and zero values).
2️⃣ Steps to Solve:

Use two variables, maxProduct and minProduct, to track the maximum and minimum product at the current index. This is essential because a negative number can flip the maximum and minimum values.
Initialize globalMax with the first element to store the maximum product encountered so far.
Traverse the array from the second element:
Swap maxProduct and minProduct if the current number is negative.
Update maxProduct to be the maximum of the current number or the product of the current number with the previous maxProduct.
Update minProduct similarly to track the minimum product.
Update globalMax with the maximum of globalMax and maxProduct.


**code**
    
  

    class Solution {
    static int max(int a, int b, int c) {
        return Math.max(a, Math.max(b, c));
    }

    static int min(int a, int b, int c) {
        return Math.min(a, Math.min(b, c));
    }
    // Function to find maximum product subarray
    int maxProduct(int[] arr) {
        
        int n = arr.length;

        // max product ending at the current index
        int currMax = arr[0];

        // min product ending at the current index
        int currMin = arr[0];

        // Initialize overall max product
        int maxProd = arr[0];

        // Iterate through the array
        for (int i = 1; i < n; i++) {
            
            // Temporary variable to store the maximum product ending 
            // at the current index
            int temp = max(arr[i], arr[i] * currMax, arr[i] * currMin);

            // Update the minimum product ending at the current index
            currMin = min(arr[i], arr[i] * currMax, arr[i] * currMin);

            // Update the maximum product ending at the current index
            currMax = temp;
            
            // Update the overall maximum product
            maxProd = Math.max(maxProd, currMax);
        }

        return maxProd;
        // code here
    }
    }
