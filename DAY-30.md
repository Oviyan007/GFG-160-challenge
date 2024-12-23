
**💡 Day 30 Problem: Search in Rotated Sorted Array**

**🧠 Approach:**

1️⃣ Understand the Problem:

Given a rotated sorted array, the task is to find the position of a target element in the array.
2️⃣ Steps to Solve:

Modified Binary Search:
Step 1: Identify the middle element.
Step 2: Check which half of the array is sorted.
Step 3: Depending on which half is sorted:
If the target lies in the sorted half, search that half.
If the target lies outside the sorted half, search the other half.
Step 4: Repeat the process recursively or iteratively until the target is found or the search space is exhausted.

**code **

    class Solution {
    int search(int[] arr, int key) {
        // Complete this function
        
            int lo = 0, hi = arr.length - 1;

        while (lo <= hi) {
            int mid = lo + (hi - lo) / 2;

            
            if (arr[mid] == key)
                return mid;

            
            if (arr[mid] >= arr[lo]) {
              
            
                if (key >= arr[lo] && key < arr[mid])
                    hi = mid - 1;
              
            
                else
                    lo = mid + 1;
            }
          
            
            else {
              
            
                if (key > arr[mid] && key <= arr[hi])
                    lo = mid + 1;
              
            
                else
                    hi = mid - 1;
            }
        }
      
        
        return -1; 
    }
    }
