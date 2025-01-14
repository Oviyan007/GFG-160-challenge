
**💡 Day 50 Problem: Count Subarrays with Given XOR**

🧠 Approach:

1️⃣ Using Prefix XOR and Hashing:

Initialize a hash map to store prefix XOR values and their frequencies.
Start with a prefix XOR of 0 and add it to the hash map with a count of 1.
As you iterate through the array, compute the running prefix XOR.
For each prefix XOR, check if prefix_XOR ^ K exists in the hash map.
If it does, the count of that key indicates the number of subarrays with XOR equal to K.
Update the hash map with the current prefix XOR to account for future subarrays.


**code**

    class Solution {
    public long subarrayXor(int arr[], int k) {
        // code here
        int res=0;
        HashMap<Integer, Integer> mp=new HashMap<>();
        int prefXOR=0;
        for(int val:arr){
            prefXOR^=val;
            res+=mp.getOrDefault(prefXOR^k,0);
            if(prefXOR == k)
                res++;
            mp.put(prefXOR,mp.getOrDefault(prefXOR,0)+1);
        }
        
        return res;
    }
    }
