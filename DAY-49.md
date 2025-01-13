
💡 Day 49 Problem: Subarrays with Sum K

🧠 Approach:
1️⃣ Using Prefix Sum and Hashing:

Initialize a hash map to store prefix sums and their frequencies.
Start with a prefix sum of 0 and add it to the hash map with a count of 1.
As you iterate through the array, calculate the running prefix sum.
For each prefix sum, check if prefix_sum - K exists in the hash map.
If it does, the count of that key indicates how many subarrays have a sum equal to K.
Update the hash map with the current prefix sum to handle future subarrays.

**code**

    class Solution {
    public int countSubarrays(int arr[], int k) {
        Map<Integer, Integer> prefixsum=new HashMap<>();
        int res=0;
        int csum=0;
        for(int i=0;i<arr.length;i++){
            csum+=arr[i];
            if(csum == k){
                res++;
            
            }
            if(prefixsum.containsKey(csum - k))
                res+=prefixsum.get(csum-k);
            prefixsum.put(csum, prefixsum.getOrDefault(csum,0)+ 1);
        }
        return res;
        // code here
    }
    }
