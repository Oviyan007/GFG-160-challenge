
**💡 Day 32 Problem: K-th Element of Two Sorted Arrays**

**🧠 Approach:**

1️⃣ Understand the Problem:

You are given two sorted arrays, arr1[] and arr2[], and a positive integer k.
Find the k-th smallest element from the merged array formed by both arrays (without explicitly merging them).
2️⃣ Steps to Solve:

Merge-Based Approach (Naive):

Merge the two arrays into a single sorted array.
Return the k-th element from the merged array.
Time Complexity: O(n + m).
Optimized Binary Search Approach:

Treat the arrays as partitions.
Use binary search on the smaller array to find the position of the k-th element by comparing elements from both arrays.
Adjust the search space based on conditions ensuring all elements before the k-th element in both arrays are smaller.
Time Complexity: O(log(min(n, m))).
**code**

    class Solution {
    public int kthElement(int a[], int b[], int k) {
         int n = a.length, m = b.length;

       
        if (n > m)
            return kthElement(b, a, k);

      
        int lo = Math.max(0, k - m), hi = Math.min(k, n);

        while (lo <= hi) {
            int mid1 = (lo + hi) / 2;
            int mid2 = k - mid1;

        
            int l1 = (mid1 == 0 ? Integer.MIN_VALUE : 
                                          a[mid1 - 1]);
            int r1 = (mid1 == n ? Integer.MAX_VALUE : 
                                              a[mid1]);

          
            int l2 = (mid2 == 0 ? Integer.MIN_VALUE : 
                                          b[mid2 - 1]);
            int r2 = (mid2 == m ? Integer.MAX_VALUE :
                                              b[mid2]);

            if (l1 <= r2 && l2 <= r1) {
               
                return Math.max(l1, l2);
            }

        
            if (l1 > r2)
                hi = mid1 - 1;

        
            else
                lo = mid1 + 1;
        }

        return 0;

    }
    }
