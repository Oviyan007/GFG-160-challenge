Day 62 of GFG 160 Challenge 🚀
💡 Day 62 Problem: Longest Subarray with Sum K

🧠 Approach:
The goal is to find the length of the longest subarray in an array whose elements sum up to a given value K.

Steps to Solve:
1️⃣ Using HashMap for Optimal Solution:

Initialize a prefix_sum variable to keep track of the running sum.
Use a HashMap to store the first occurrence of every prefix_sum.
Traverse the array:
Add the current element to prefix_sum.
Check if prefix_sum == K:
If true, update the maximum length to the current index + 1.
If (prefix_sum - K) exists in the HashMap:
Calculate the subarray length and update the maximum length.
Store prefix_sum in the HashMap if it’s not already present.


**code**

      class Solution {
    public int longestSubarray(int[] arr, int k) {
        // code here
        Map<Integer,Integer> mp=new HashMap<>();
        int res=0;
        int prefSum=0;
        for(int i=0;i<arr.length;++i){
            prefSum +=arr[i];
            if(prefSum == k)
                res=i+1;
            else if(mp.containsKey(prefSum - k))
                res=Math.max(res,i-mp.get(prefSum - k));
            if(!mp.containsKey(prefSum))
                mp.put(prefSum,i);
        }
        return res;
    }
    }
