**💡 Day 20 Problem: Minimum Characters to Add for a Palindrome**

**🧠 Approach:**

1️⃣ Understand the Problem:

Determine the minimum number of characters that need to be added at the beginning of a string to make it a palindrome.
2️⃣ Steps to Solve:

Step 1: Reverse the string and concatenate it with the original string using a special delimiter to avoid overlaps.
Step 2: Compute the Longest Prefix Suffix (LPS) array for this concatenated string.
Step 3: The length of the longest prefix that is also a suffix gives the count of characters already forming a palindrome. Subtract this length from the string length to find the minimum characters needed to add.

**code**

    class Solution {
    public static int minChar(String s) {
        
        int n = s.length();
        String rev = new StringBuilder(s).reverse().toString();

        
        String combined = s + "$" + rev;

        
        int[] lps = computeLPSArray(combined);

        
        return n - lps[lps.length - 1];
    }

    private static int[] computeLPSArray(String s) {
        int n = s.length();
        int[] lps = new int[n];
        int len = 0; 
        int i = 1;

        lps[0] = 0; 

        while (i < n) {
            if (s.charAt(i) == s.charAt(len)) {
                len++;
                lps[i] = len;
                i++;
            } else {
                if (len != 0) {
                    len = lps[len - 1];
                } else {
                    lps[i] = 0;
                    i++;
                }
            }
        }

        return lps;
    }
    }
