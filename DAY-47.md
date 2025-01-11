
💡 Day 47 Problem: Longest Consecutive Subsequence

🧠 Approach:

1️⃣ Using Hashing:

Insert all elements of the array into a set to allow O(1) lookups.
Iterate through the array and, for each element, check if it's the start of a sequence (i.e., no element - 1 exists in the set).
If it is the start of a sequence, count the consecutive elements until the sequence breaks.
Keep track of the maximum sequence length.

**code**

      class Solution {

    // Function to return length of longest subsequence of consecutive integers.
    public int longestConsecutive(int[] arr) {
        // code here
        Set<Integer> st=new HashSet<>();
        int res=0;
        for(int val:arr){
            st.add(val);
        }
        for(int val:arr){
            if(st.contains(val) && !st.contains(val-1)){
                int cur=val,cnt=0;
                while(st.contains(cur)){
                    st.remove(cur);
                    cur++;
                    cnt++;
                }
                res=Math.max(res, cnt);
            }
        }
        return res;
    }
    }
