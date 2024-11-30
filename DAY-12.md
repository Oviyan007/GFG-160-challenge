
💡 Day 12 Problem: Smallest Positive Missing Number

🧠 Approach:
1️⃣ Understand the Problem:

Find the smallest positive integer missing from a given array of integers, which may include both positive and negative numbers.
2️⃣ Steps to Solve:

Optimal Approach (O(n)):
Segregate positive numbers from non-positive ones by rearranging the array.
Work only on the positive segment:
Use the index positions of the array as a hash to mark the presence of numbers.
For any number x, if 1 ≤ x ≤ n, mark the position x-1 as visited by making it negative.
Traverse the array: The first index with a positive value indicates the missing number. If all are marked, the missing number is n+1.

**code**

      class Solution {
    // Function to find the smallest positive number missing from the array.
    public int missingNumber(int[] arr) {
        // Your code here
        
        Arrays.sort(arr);
        int res=1;
        int n=arr.length;
        for(int i=0;i<n;i++){
            if(arr[i] == res){
                res+=1;
            }
            else if(arr[i] > res){
                break;
            }
        }
        return res;
    }
    }
