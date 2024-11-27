**💡 Day 9 Problem: Minimize the Heights II**

**🧠 Approach:**

1️⃣ Understand the Problem:

You are given an array of heights, and you can either increase or decrease each height by a fixed value k.
The goal is to minimize the difference between the maximum and minimum heights after these adjustments.
2️⃣ Steps to Solve:

Sort the array to analyze height adjustments systematically.
Adjust the smallest height by adding k and the largest height by subtracting k.
Iterate through the array to check all possible combinations of adjusted heights and find the minimum difference.
3️⃣ Key Observations:

Only the extreme values (largest and smallest) determine the difference.
Careful analysis of edge cases is crucial, like when height adjustments result in negative values.


**📌 Key Takeaways:** 
🔹 Sorting helps narrow down possibilities and optimizes the solution to O(n log n).
🔹 Always account for edge cases, such as arrays with one element or very large/small k.
🔹 This problem emphasizes balancing between maximizing and minimizing values efficiently.

**code**
        
        class Solution {
        
        int getMinDiff(int[] arr, int k) {
        // code here
        int size=arr.length;
        Array.sort();
        int res=arr[n-1]-arr[0];
        for(int i=0;i<size;i++){
            if(arr[i]-k<0)
                continue;
            int minH=Math.min(arr[0]+k,arr[i]-k);
            int maxH = Math.max(arr[i - 1] + k, arr[n - 1] - k);
             res = Math.min(res, maxH - minH);
            
        }
        return res;
    }
}
