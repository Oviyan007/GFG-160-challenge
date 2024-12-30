 Day 35 of GFG 160 Challenge 🚀
💡 Day 35 Problem: Kth Missing Positive Number

🧠 Approach:

1️⃣ Understand the Problem:

Given a sorted array arr[] of positive integers and an integer k, find the kth missing positive number from the sequence of natural numbers not present in the array.

2️⃣ Steps to Solve:

Binary Search Approach:
Compute the number of missing numbers before each element of the array.
If the missing count at an index is less than k, the answer lies to the right.
Otherwise, the answer lies to the left.
Result=arr[left−1]+(k−missing[left−1])

Iterative Approach:

Start from 1 and iterate through natural numbers while skipping the ones present in arr.
Stop when the count of missing numbers equals k.

**code**

      class Solution {
    public int kthMissing(int[] arr, int k) {
        
        // code here
        Set<Integer> set=new HashSet<>();
        for(int num:arr){
            set.add(num);
            }
        int count=0; int curr=0;
        while(count<k){
            curr++;
            if(!set.contains(curr)){
                count++;
            }
        }
        return curr;
    }
    }
