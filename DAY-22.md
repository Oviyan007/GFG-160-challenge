Day 22 of GFG 160 Challenge 🚀
💡 Day 22 Problem: H-Index

🧠 Approach:
1️⃣ Understand the Problem:

Given an array of integers representing the citation count for each paper, calculate the H-Index.
H-Index is defined as the maximum value h such that there are at least h papers with h or more citations.
2️⃣ Steps to Solve:

Step 1: Sort the array in ascending order.
Step 2: Iterate through the sorted array and calculate the number of papers with citations greater than or equal to the current citation count.
Step 3: Find the maximum value of h that satisfies the H-Index condition.

**code**

      class Solution {
    // Function to find hIndex
    public int hIndex(int[] citations) {
        // code here
        int n=citations.length;
        int[] freq=new int[n+1];
        for(int i=0;i<n;i++){
            if(citations[i]>=n){
                freq[n]+=1;
            }
            else{
                freq[citations[i]]+=1;
            }
        }
        int idx=n;
        int s=freq[n];
        while(s<idx){
            idx--;
            s+=freq[idx];
        }
        
        return idx;
    }
    }
