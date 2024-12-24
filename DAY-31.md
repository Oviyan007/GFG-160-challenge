
**💡 Day 31 Problem: Find Peak Element
**
**🧠 Approach:**
1️⃣ Understand the Problem:

A peak element is an element that is strictly greater than its neighbors.
The task is to find a peak element in the array (multiple peaks are possible).
2️⃣ Steps to Solve:

Binary Search Approach:
Start with the entire array as the search space.
Find the middle element.
Check if it is a peak:
If yes, return it.
If not, decide which half to continue searching:
If the left neighbor is greater, move to the left half.
Otherwise, move to the right half.
Repeat until the peak is found.


**code**

    class Solution {

    public int peakElement(int[] arr) {
        // code here
         int n = arr.length;

        
        if (n == 1)
            return 0;

        if (arr[0] > arr[1])
            return 0;


        if (arr[n - 1] > arr[n - 2])
            return n - 1;

 
        int lo = 1, hi = n - 2;

        while (lo <= hi) {
            int mid = lo + (hi - lo) / 2;

            
            if (arr[mid] > arr[mid - 1] && arr[mid] > arr[mid + 1])
                return mid;

     
            if (arr[mid] < arr[mid + 1])
                lo = mid + 1;

         
            else
                hi = mid - 1;
        }

        return 0;
    
    }
    }
