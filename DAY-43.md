
**💡 Day 43 Problem: Count Pairs with a Given Sum**

**🧠 Approach:**
To count the pairs of elements in an array that sum up to a given value 
target
target:

1️⃣ Hash Map Technique:

Use a hash map to store the frequency of each number in the array.
For each number, calculate the complement: 
complement=target−current_number.
Check if the complement exists in the hash map. If it does, add its frequency to the count.
Update the hash map to include the current number.


**code**

      class GfG {
    
    // Returns number of pairs in arr[0...n-1] with
    // sum equal to 'target'
    static int countPairs(int[] arr, int target) {
        Map<Integer, Integer> freq = new HashMap<>();
        int cnt = 0;

        for (int i = 0; i < arr.length; i++) {
          
            // Check if the complement (target - arr[i])
            // exists in the map. If yes, increment count
            if (freq.containsKey(target - arr[i])) {
                cnt += freq.get(target - arr[i]); 
            }
          
            // Increment the frequency of arr[i]
            freq.put(arr[i], 
                     freq.getOrDefault(arr[i], 0) + 1); 
        }
        return cnt;
    }
