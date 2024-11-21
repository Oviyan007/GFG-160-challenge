**Rotate Array**


Given an unsorted array arr[]. Rotate the array to the left (counter-clockwise direction) by d steps, where d is a positive integer. Do the mentioned change in the array in place.

Note: Consider the array as circular.

Examples :

Input: arr[] = [1, 2, 3, 4, 5], d = 2
Output: [3, 4, 5, 1, 2]
Explanation: when rotated by 2 elements, it becomes 3 4 5 1 2.
Input: arr[] = [2, 4, 6, 8, 10, 12, 14, 16, 18, 20], d = 3
Output: [8, 10, 12, 14, 16, 18, 20, 2, 4, 6]
Explanation: when rotated by 3 elements, it becomes 8 10 12 14 16 18 20 2 4 6.


**Approach**
The idea is to use a temporary array of size n, where n is the length of the original array. If we left rotate the array by d positions, the last n – d elements will be at the front and the first d elements will be at the end.


Copy the last (n – d) elements of original array into the first n – d positions of temporary array.
Then copy the first d elements of the original array to the end of temporary array. 
Finally, copy all the elements of temporary array back into the original array.
**Code**
     
    class Solution {
  
      static void rotateArr(int arr[], int d) {
         int n = arr.length;
     
        d %= n;
       
        reverse(arr, 0, d - 1);

        // Reverse the remaining n-d elements
        reverse(arr, d, n - 1);

        // Reverse the entire array
        reverse(arr, 0, n - 1);
    }

    // Function to reverse a portion of the array
    static void reverse(int[] arr, int start, int end) {
        while (start < end) {
            int temp = arr[start];
            arr[start] = arr[end];
            arr[end] = temp;
            start++;
            end--;
        }
    }
    }
