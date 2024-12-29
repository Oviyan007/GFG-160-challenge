**💡 Day 34 Problem: Allocate Minimum Pages**

**🧠 Approach:**

1️⃣ Understand the Problem:

You are given n books with pages[] representing the number of pages in each book.
You need to allocate these books to m students such that:
Each student gets a contiguous set of books.
The maximum number of pages assigned to a student is minimized.

2️⃣ Steps to Solve:

Binary Search on Answer:
The minimum possible value of the maximum pages is the largest single book (lower bound).
The maximum possible value is the sum of all pages (upper bound).
Perform binary search within this range.

**code**

      class Solution {
     static boolean check(int[] arr, int k, int pageLimit) {
        
       
        int cnt = 1;
        int pageSum = 0;
        for(int i = 0; i < arr.length; i++) {
            
           
            if(pageSum + arr[i] > pageLimit) {
                cnt++;
                pageSum = arr[i];
            }
            else {
                pageSum += arr[i];
            }
        }
        
       
        return (cnt <= k);
    }
    public static int findPages(int[] arr, int k) {
           
        if(k > arr.length)
            return -1;
        
     
        int lo = Arrays.stream(arr).max().getAsInt();
        int hi = Arrays.stream(arr).sum();
        int res = -1;
        
        while(lo <= hi) {
            int mid = lo + (hi - lo) / 2;
            
            if(check(arr, k, mid)){
                res = mid;
                hi = mid - 1;
            }
            else {
                lo = mid + 1;
            }
        }
        
        return res;
    }
    }
