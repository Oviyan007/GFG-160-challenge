
💡 Day 63 Problem: Largest Subarray of 0's and 1's

🧠 Approach:
The task is to find the length of the largest subarray with an equal number of 0's and 1's.

Steps to Solve:
1️⃣ Transform the Array:

Replace all 0's with -1's.
The problem now reduces to finding the longest subarray with a sum of 0.
2️⃣ Using HashMap for Optimization:

Use a HashMap to store the first occurrence of each prefix sum.
Traverse the array:
Maintain a prefix_sum.
If prefix_sum == 0:
Update the maximum length to the current index + 1.
If the prefix_sum is already in the HashMap:
Calculate the length of the subarray and update the maximum length.
Otherwise, store the prefix_sum with its index in the HashMap.


**code**

      class Solution {
    public int maxLen(int[] arr) {
        // Your code here
        HashMap<Integer,Integer> mp=new HashMap<>();
        int preSum=0;
        int res=0;
        for(int i=0;i<arr.length;i++){
            preSum+=(arr[i]==0)? -1 : 1;
            
            if(preSum == 0)
                res=i+1;
            if(mp.containsKey(preSum))
                res=Math.max(res,i-mp.get(preSum));
            else
                mp.put(preSum,i);
        }
        return res;
    }
    }
