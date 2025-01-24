Day 60 of GFG 160 Challenge 🚀
💡 Day 60 Problem: Container with Most Water

🧠 Approach:
1️⃣ Two Pointer Technique:

Place one pointer at the start (left) and another at the end (right) of the array.
Calculate the area formed between the two lines using the formula:

Area=(right−left)×min(height[left],height[right])

2️⃣ Optimize Area:

Keep track of the maximum area encountered so far.
Move the pointer pointing to the shorter height inward:
If height[left] < height[right], move left forward.
Otherwise, move right backward.

**code**

    class Solution {

    public int maxWater(int arr[]) {
        // Code Here
        int left=0,right=arr.length-1;
        int res=0;
        while(left<right){
            int water=Math.min(arr[left],arr[right])*(right-left);
            res=Math.max(res,water);
            if(arr[left] < arr[right])
                left +=1;
            else
                right-=1;
        }
        return res;
    }
    }
