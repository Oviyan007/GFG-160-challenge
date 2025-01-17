
💡 Day 53 Problem: Find the Pair with Sum Closest to Target

🧠 Approach:
1️⃣ Sort the Array:

Sort the array to simplify the problem and use the two-pointer technique efficiently.
2️⃣ Two-Pointer Technique:

Initialize two pointers, left at the start and right at the end of the array.
Track the minimum difference (minDiff) and the pair with the closest sum.
While left < right:
Compute the sum of elements at left and right.
If the absolute difference between the sum and target is less than minDiff, update minDiff and store the pair.
Move pointers:
If the sum is less than the target, increment left (to increase the sum).
Otherwise, decrement right (to decrease the sum).

**code **

    class Solution {
    public List<Integer> sumClosest(int[] arr, int target) {
        // code here
        int n=arr.length;
        Arrays.sort(arr);
        List<Integer> res=new ArrayList<>();
        int minDiff=Integer.MAX_VALUE;
        int left=0,right=n-1;
        while(left<right){
            int currSum=arr[left]+arr[right];
            if(Math.abs(target-currSum)<minDiff){
                minDiff=Math.abs(target-currSum);
                res=Arrays.asList(arr[left],arr[right]);
            }
            if(currSum < target)
                left++;
            else if (currSum > target)
                right--;
            else
                return res;
        }
        return res;
    }
    }
