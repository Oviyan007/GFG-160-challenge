
💡 Day 56 Problem: Find the Indexes of Subarray with a Given Sum

🧠 Approach:
1️⃣ Use a Hash Map:

Maintain a hash map to store the cumulative sum at each index.
The key will be the cumulative sum, and the value will be the index where this sum occurs.
2️⃣ Track Cumulative Sum:

As you iterate through the array, calculate the cumulative sum.
If the difference (cumulative_sum - target_sum) is found in the hash map, it means the subarray from the stored index + 1 to the current index has the required sum.

**code**

      class Solution {
    static ArrayList<Integer> subarraySum(int[] arr, int target) {
        int s=0,e=0;
        ArrayList<Integer> res=new ArrayList<>();
        int curr=0;
        for(int i=0;i<arr.length;i++){
            curr+=arr[i];
            if(curr>=target){
                e=i;
                while(curr>target && s<e){
                    curr-=arr[s];
                    ++s;
                }
                if(curr==target){
                    res.add(s + 1);
                    res.add(e  + 1);
                    return res;
                }
            }
        }
        res.add(-1);
        return res;
        
    }
    }
