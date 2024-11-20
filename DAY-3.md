**Problem description**
Given an array arr[]. Push all the zeros of the given array to the right end of the array while maintaining the order of non-zero elements. Do the mentioned change in the array in place.

Examples:

Input: arr[] = [1, 2, 0, 4, 3, 0, 5, 0]
Output: [1, 2, 4, 3, 5, 0, 0, 0]
Explanation: There are three 0s that are moved to the end.

Input: arr[] = [10, 20, 30]
Output: [10, 20, 30]
Explanation: No change in array as there are no 0s.

Input: arr[] = [0, 0]
Output: [0, 0]
Explanation: No change in array as there are all 0s.

**🧠 Approach:**

1️⃣ Use two pointers:

One pointer (j) tracks the position to place the next non-zero element.

The other pointer (i) iterates through the array.

2️⃣ For each non-zero element at index i, swap it with the element at index j, then increment j.

3️⃣ All zeros will naturally shift to the right by the end of the loop.

**Code**
        
         
         public static void moveZerosToEnd(int[] arr) {
            int n = arr.length; 
            int i = 0; 
           for (int j = 0; j < n; j++) {
            if (arr[j] != 0) {
                
                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
                i++;
            }
        }
    }
