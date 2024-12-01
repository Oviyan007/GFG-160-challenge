💡 Day 13 Problem: Maximum Circular Subarray Sum

🧠 Approach:
1️⃣ Understand the Problem:

Find the maximum sum of a contiguous subarray in a circular array, where the end of the array connects to the beginning.
2️⃣ Steps to Solve:

Step 1: Use Kadane's Algorithm to find the maximum sum of a standard subarray.
Step 2: Compute the total sum of the array.
Step 3: Use Kadane’s Algorithm on the inverted array (changing signs of all elements) to find the minimum subarray sum.
Step 4: The circular maximum sum is calculated as totalSum - minSubarraySum.
Step 5: Return the maximum of the result from Step 1 and Step 4, ensuring that the array has at least one non-negative element.


**code**
  
    class Solution {

    // a: input array
    // n: size of array
    // Function to find maximum circular subarray sum.
    public int circularSubarraySum(int arr[]) {

        // Your code here
         int totalSum = 0;    
        int currMaxSum = 0, currMinSum = 0;
        int maxSum = arr[0], minSum = arr[0];
        
        for(int i = 0; i < arr.length; i++) {
          
            // Kadane's to find maximum sum subarray
            currMaxSum = Math.max(currMaxSum + arr[i], arr[i]);
            maxSum = Math.max(maxSum, currMaxSum); 
          
            // Kadane's to find minimum sum subarray
            currMinSum = Math.min(currMinSum + arr[i], arr[i]);
            minSum = Math.min(minSum, currMinSum);
            
            // Sum of all the elements of input array
            totalSum += arr[i];
        }
        
        int normalSum = maxSum;
        int circularSum = totalSum - minSum;
        
        // If the minimum subarray is equal to total Sum
        // then we just need to return normalSum
        if(minSum == totalSum)
            return normalSum;
        
        return Math.max(normalSum, circularSum);
    }
    }
