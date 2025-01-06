
💡 Day 42 Problem: Two Sum – Pair with Given Sum

🧠 Approach:

Here’s how to efficiently find a pair of numbers that add up to a given target:

1️⃣ Use a hash map (dictionary) to store numbers as you iterate through the array. The key is the number itself, and the value is its index.

2️⃣ For each number in the array:

Calculate the complement needed to reach the target sum: complement = target - current_number.
Check if this complement exists in the hash map.
If found, return the indices of the current number and its complement.
3️⃣ If no such pair is found, return an appropriate result (e.g., an empty list or a message).

This method ensures a time complexity of 

O(N), making it both fast and scalable.

**code**

    class Solution {
    boolean twoSum(int arr[], int target) {
        HashSet<Integer> set=new HashSet<>();
        
        for(int i=0;i<arr.length;i++){
            int complement=target-arr[i];
            
            if(set.contains(complement)){
                return true;
            }
            set.add(arr[i]);
        }
        return false;
    }
    }
