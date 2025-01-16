
💡 Day 52 Problem: Count Pairs Whose Sum is Less Than Target

🧠 Approach:
1️⃣ Sort the Array:

Start by sorting the array to enable the two-pointer technique efficiently.
2️⃣ Two-Pointer Technique:

Initialize two pointers, left at the beginning of the array and right at the end.
While left < right:
Check the sum of the elements at left and right.
If the sum is less than the target, all pairs between left and right will have a sum less than the target (since the array is sorted). Add (right - left) to the count, then increment left.
Otherwise, decrement right.

**code**

    class Solution {
    int countPairs(int arr[], int target) {
        // Your code here
        Arrays.sort(arr);
        int left=0,right=arr.length-1;
        int cnt=0;
        while(left < right){
            int sum=arr[left]+arr[right];
            if(sum < target){
                cnt+=right-left;
                left++;
            }
            else{
                right--;
            }
        }
        return cnt;
    }
    }
