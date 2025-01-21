
💡 Day 57 Problem: Count Distinct Elements in Every Window

🧠 Approach:
1️⃣ Use a Hash Map:

Maintain a hash map to store the frequency of elements in the current window.
2️⃣ Sliding Window Technique:

Initialize the first window by iterating over the first k elements and updating the hash map.
For subsequent windows, slide the window one element at a time:
Decrease the frequency of the outgoing element in the hash map.
Remove it from the hash map if its frequency becomes zero.
Add the incoming element to the hash map or increase its frequency if it already exists.
3️⃣ Count Distinct Elements:

The size of the hash map at each step represents the count of distinct elements in the current window.

**code**

      class Solution {
    ArrayList<Integer> countDistinct(int arr[], int k) {
        // code here
        int n=arr.length;
        ArrayList<Integer> res =new ArrayList<>();
        Map<Integer,Integer> freq =new HashMap<>();
        for(int i=0;i<k;i++){
            freq.put(arr[i],freq.getOrDefault(arr[i],0) + 1);
        }
        res.add(freq.size());
        for(int i=k;i<n;i++){
            freq.put(arr[i],freq.getOrDefault(arr[i],0) + 1);
            freq.put(arr[i-k],freq.get(arr[i-k]) - 1);
            
            if(freq.get(arr[i-k]) == 0){
                freq.remove(arr[i-k]);
            }
            res.add(freq.size());
        }
        
        return res;
        
    }
    }
