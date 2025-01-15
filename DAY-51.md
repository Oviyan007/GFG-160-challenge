
💡 Day 51 Problem: Count All Triplets with Given Sum Using Two-Pointer Approach

🧠 Approach:
1️⃣ Sorting the Array:

First, sort the array to leverage the two-pointer technique.
2️⃣ Iterating for the First Element:

Use a loop to fix the first element of the triplet.
3️⃣ Two-Pointer Technique:

For the remaining part of the array, set two pointers: one at the start (left) and the other at the end (right).
Calculate the sum of the three elements (arr[i] + arr[left] + arr[right]).
If the sum matches the target, increment the count and adjust both pointers (left++, right--).
If the sum is less than the target, increment left.
If the sum is greater than the target, decrement right.


**code**


    class Solution {
    public int countTriplets(int[] arr, int target) {
        // Code Here
        Arrays.sort(arr);
        int n=arr.length;
        int res=0;
        for(int i=0;i<n-2;i++){
            int left=i+1;
            int right=n-1;
            while(left < right){
                int sum=arr[i]+arr[left]+arr[right];
                if(sum == target){
                    int ele1=arr[left],ele2=arr[right];
                    int cnt1=0,cnt2=0;
                    while(left <= right && arr[left] == ele1){
                        cnt1++;
                        left++;
                    }
                    while(left <= right && arr[right] == ele2){
                        cnt2++;
                        right--;
                    }
                    if(ele1 == ele2){
                        res+=(cnt1*(cnt1-1))/2;
                    }
                    else{
                        res+=cnt1*cnt2;
                    }
                }else if(sum < target){
                    left++;
                }else{
                    right--;
                }
            }
        }
        return res;
    }
    }
