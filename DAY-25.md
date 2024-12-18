

**💡 Day 25 Problem: Insert Interval**

**🧠 Approach:**

1️⃣ Understand the Problem:

Given a list of non-overlapping intervals and a new interval, insert the new interval into the list while maintaining the order and merging any overlapping intervals.
Example: Intervals = [[1,3],[6,9]], New Interval = [2,5] → [[1,5],[6,9]].
2️⃣ Steps to Solve:

Step 1: Iterate through the existing intervals.
Step 2: Handle three cases:
If the current interval ends before the new interval starts, add it to the result list.
If the new interval ends before the current interval starts, add the new interval, update it as processed, and add the remaining intervals.
If the intervals overlap, merge them by updating the start to the minimum of the two starts and the end to the maximum of the two ends.
Step 3: If the new interval is still unprocessed, add it to the result list

**code**

class Solution {
    static ArrayList<int[]> insertInterval(int[][] intervals, int[] newInterval) {
       ArrayList<int[]> res = new ArrayList<>();
        int i = 0;
        int n = intervals.length;

        while (i < n && intervals[i][1] < newInterval[0]) {
            res.add(intervals[i]);
            i++;
        }

      
        while (i < n && intervals[i][0] <= newInterval[1]) {
            newInterval[0] = Math.min(newInterval[0], intervals[i][0]);
            newInterval[1] = Math.max(newInterval[1], intervals[i][1]);
            i++;
        }
        res.add(newInterval);

        
        while (i < n) {
            res.add(intervals[i]);
            i++;
        }

        
        return res;
    }
    }
