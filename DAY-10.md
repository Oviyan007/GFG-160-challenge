**💡 Day 10 Problem: Kadane's Algorithm**

**🧠 Approach:**

1️⃣ Understand the Problem:

Find the maximum sum of a contiguous subarray within a given array of integers (which may include negative numbers).
2️⃣ Steps to Solve Using Kadane's Algorithm:

Initialize two variables:

currentSum to track the sum of the current subarray (start with 0).

maxSum to store the maximum sum found so far (initialize with the smallest possible integer).

Traverse the array:

Add the current element to currentSum.

Update maxSum if currentSum exceeds it.

Reset currentSum to 0 if it becomes negative, as a negative sum won’t contribute to the maximum.
**Code**

      class Solution {

    // arr: input array
    // Function to find the sum of contiguous subarray with maximum sum.
    int maxSubarraySum(int[] arr) {

       int n = arr.length;
        
        // Initialize with the first element
        int maxEndingHere = arr[0];
        int maxSoFar = arr[0];
        
        // Traverse the array starting from the second element
        for (int i = 1; i < n; i++) {
            // Update maxEndingHere
            maxEndingHere = Math.max(arr[i], maxEndingHere + arr[i]);
            
            // Update maxSoFar
            maxSoFar = Math.max(maxSoFar, maxEndingHere);
        }
        
        return maxSoFar;
    }
    }
