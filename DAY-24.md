
💡 Day 24 Problem: Merge Overlapping Intervals

🧠 Approach:
1️⃣ Understand the Problem:

Given a list of intervals, merge all overlapping intervals into a single interval.
Example: [[1,3],[2,4],[6,8],[9,10]] → [[1,4],[6,8],[9,10]].
2️⃣ Steps to Solve:

Step 1: Sort all the intervals based on their start times.
Step 2: Use a stack or a result list to merge intervals:
Compare the end time of the current interval with the start time of the next interval.
If they overlap, merge them by updating the end time to the maximum of the two overlapping intervals.
Otherwise, add the current interval to the result list.
Time Complexity: O(n log n) (due to sorting).
Space Complexity: O(n) for storing the result.


**code**

      class Solution {
    public List<int[]> mergeOverlap(int[][] arr) {
         Arrays.sort(arr, (a, b) -> Integer.compare(a[0], b[0]));

        List<int[]> res = new ArrayList<>();
        res.add(new int[]{arr[0][0], arr[0][1]});

        for (int i = 1; i < arr.length; i++) {
            int[] last = res.get(res.size() - 1);
            int[] curr = arr[i];

            // If current interval overlaps with the last merged 
            // interval, merge them 
            if (curr[0] <= last[1]) 
                last[1] = Math.max(last[1], curr[1]);
            else 
                res.add(new int[]{curr[0], curr[1]});
        }

        return res;
        // Code here // Code here
    }
    }
