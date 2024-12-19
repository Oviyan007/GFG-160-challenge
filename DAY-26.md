**💡 Day 26 Problem: Minimum Number of Intervals to Remove**

**🧠 Approach:**

1️⃣ Understand the Problem:

Given overlapping intervals, find the minimum number of intervals to remove to make the rest of the intervals non-overlapping.
2️⃣ Steps to Solve:

Step 1: Sort the intervals by their end times.

Step 2: Use a greedy approach to minimize overlap by keeping track of the end time of the last added interval.

Step 3: Iterate through the intervals:

If the current interval's start time is greater than or equal to the end time of the last added interval, update the end time.
Otherwise, increment the count of intervals to remove.

**Code**

      class Solution {
    static int minRemoval(int intervals[][]) {
        
         int cnt = 0;

        
        Arrays.sort(intervals, (a, b) -> a[1] - b[1]);

        int end = intervals[0][1];

        for (int i = 1; i < intervals.length; i++) {

            
            if (intervals[i][0] < end)
                cnt++;

            
            else
                end = intervals[i][1];
        }

        
        return cnt;
    }
    }

  
