
💡 Day 54 Problem: Pair with a Given Sum in a Sorted Array

🧠 Approach:
1️⃣ Two-Pointer Technique:

Since the array is already sorted, initialize two pointers:
left at the start of the array.
right at the end of the array.
2️⃣ Finding the Pair:

While left < right:
Calculate the sum of the elements at left and right.
If the sum equals the target, you've found the pair!
If the sum is smaller than the target, increment left to increase the sum.
If the sum is larger than the target, decrement right to decrease the sum.

**code**
    class Solution {

    int countPairs(int arr[], int target) {
        // Complete the function
        int res=0;
        int n=arr.length;
        int left=0,right=n-1;
        while(left< right){
            if(arr[left] + arr[right]<target)
                left++;
            else if (arr[left]+arr[right]>target)
                right--;
            else{
                int cnt1=0,cnt2=0;
                int ele1=arr[left],ele2=arr[right];
                while(left<=right && arr[left] == ele1){
                    left++;
                    cnt1++;
                }
                while(left<=right && arr[right]==ele2){
                    right--;
                    cnt2++;
                }
                if(ele1==ele2)
                    res+=(cnt1*(cnt1-1))/2;
                else
                    res+=(cnt1*cnt2);
            }
        }
        return res;
        
    }
    
    
      }
