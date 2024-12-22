**💡 Day 29 Problem: Sorted and Rotated Minimum**

**🧠 Approach:**

1️⃣ Understand the Problem:

In a sorted and rotated array, find the minimum element in optimal time.
2️⃣ Steps to Solve:

Use a modified binary search:
Step 1: Identify the mid-point of the array.
Step 2: Check if the mid is the minimum element (compare it with its neighbors).
Step 3: If the left half is sorted, the minimum lies in the right half.
Step 4: If the right half is sorted, the minimum lies in the left half.
Repeat until the minimum is found.

**code**

    class Solution {
    public int findMin(int[] arr) {
        // complete the function here
        int lo = 0, hi = arr.length - 1;

        while (lo < hi) {
          
            
            if (arr[lo] < arr[hi])        
                return arr[lo];
               
           
          
            int mid = (lo + hi) / 2;

            
            if (arr[mid] > arr[hi])
                lo = mid + 1;
          
           
            else
                hi = mid;
        }

        return arr[lo]; 
    }
    }
