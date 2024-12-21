
**💡 Day 28 Problem: Number of Occurrence**

**🧠 Approach:**

1️⃣ Understand the Problem:

Given a sorted array, find how many times the target element appears.
2️⃣ Steps to Solve:

Step 1: Use binary search to find the first occurrence of the target.
Step 2: Use binary search again to find the last occurrence of the target.
Step 3: The number of occurrences = (last occurrence index - first occurrence index + 1).
3️⃣ Edge Cases:

If the target is not found, return 0.
Arrays with repeated elements or single elements.
4️⃣ Time Complexity:

Since binary search is used, the time complexity is O(log n).

**code**

    class Solution {
    int countFreq(int[] arr, int target) {
        // code here
        int count=0;
        for(int i=0;i<arr.length;i++){
            if(arr[i] == target){
                count++;
            }
        }
        return count;
    }
    }
