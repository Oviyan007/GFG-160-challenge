

💡 Day 58 Problem: Longest Substring with Distinct Characters

🧠 Approach:
1️⃣ Sliding Window + Hash Map:

Use a two-pointer technique (left and right pointers) to maintain the current substring window.
Utilize a hash map to store the last occurrence of each character.
2️⃣ Iterate Through the String:

For each character, check if it exists in the hash map:
If it exists and its last occurrence is within the current window, move the left pointer to the right of this occurrence.
Update the hash map with the current character's index.
3️⃣ Update the Maximum Length:

At each step, calculate the length of the current window (right - left + 1) and update the maximum length if needed.

**code**

    class Solution {
    static final int MAX_CHAR=26;
    public int longestUniqueSubstr(String s) {
        // code here
       int n=s.length();
       int res=0;
       int[] lastindex=new int[MAX_CHAR];
       for(int i=0;i<MAX_CHAR;i++){
           lastindex[i]=-1;
           
       }
       int start=0;
       for(int end=0;end<n;end++){
           start=Math.max(start,lastindex[s.charAt(end)-'a']+ 1);
           res=Math.max(res, end-start + 1);
           lastindex[s.charAt(end)-'a']=end;
       }
       return res;
        
    }
    }
