
**💡 Day 33 Problem: Aggressive Cows**

**🧠 Approach:**

1️⃣ Understand the Problem:

You are given n stalls and their respective positions in a 1D array arr[].
Place c cows in these stalls such that the minimum distance between any two cows is maximized.
2️⃣ Steps to Solve:

Sorting the Stalls:

Sort the array to ensure logical placement of cows.
Binary Search on Answer:

The search space for the answer lies between 1 (minimum possible distance) and the difference between the maximum and minimum stall positions.
Use binary search to find the maximum minimum distance.
Greedy Check:

For a mid-point in the binary search, check if it's possible to place all c cows in the stalls while maintaining the minimum distance.
Start with the first stall and place the next cow only if the distance condition is satisfied.
Adjust the search space based on whether placing the cows is possible or not.

**code **

    class Solution {
      static boolean check(int[] stalls, int k, int dist) {
        

        int cnt = 1;  
        int prev = stalls[0]; 
        for (int i = 1; i < stalls.length; i++) {
          
            if (stalls[i] - prev >= dist) {
                prev = stalls[i]; 
                cnt++;
            }
        }

      
        return (cnt >= k);
    }

    static int aggressiveCows(int[] stalls, int k) {
      
  
        Arrays.sort(stalls);
        int res = 0; 
        int lo = 1;
        int hi = stalls[stalls.length - 1] - stalls[0]; 

        while(lo <= hi) {
            int mid = lo + (hi - lo) / 2;
            
          
            if(check(stalls, k, mid)) {
                res = mid;
                lo = mid + 1;
            }
            else {
                hi = mid - 1;
            }
        }
        
        return res;
    }
    }
