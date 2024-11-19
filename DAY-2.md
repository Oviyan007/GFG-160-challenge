**Problem Description**


**Reverse an Array**

You are given an array of integers arr[]. Your task is to reverse the given array.

Examples:

Input: arr = [1, 4, 3, 2, 6, 5]
Output: [5, 6, 2, 3, 4, 1]
Explanation: The elements of the array are 1 4 3 2 6 5. After reversing the array, the first element goes to the last position, the second element goes to the second last position and so on. Hence, the answer is 5 6 2 3 4 1.

Input: arr = [4, 5, 2]
Output: [2, 5, 4]
Explanation: The elements of the array are 4 5 2. The reversed array will be 2 5 4.

Input: arr = [1]
Output: [1]
Explanation: The array has only single element, hence the reversed array is same as the original.
---
🧠 Approach:
1️⃣ Use two pointers:

One starting at the beginning of the array (left) and the other at the end (right).
2️⃣ Swap the elements at the left and right pointers.
3️⃣ Increment left and decrement right to move the pointers inward.
4️⃣ Repeat until the pointers meet or cross each other.

---
**code**

    class Solution {
    public void reverseArray(int arr[]) {
        // code here
        int n=arr.length-1;
      int left=0; int right=n;
      while(left < right){
          int temp=arr[right];
          arr[right]=arr[left];
          arr[left]=temp;
           
          left++;
          right--;
      }
    
         
    }
    }
