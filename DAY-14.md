💡 Day 14 Problem: Implement Atoi

🧠 Approach:
1️⃣ Understand the Problem:

Convert a string representation of an integer into the actual integer, handling edge cases like invalid characters, leading spaces, and optional signs.
2️⃣ Steps to Solve:

Step 1: Trim leading and trailing whitespace from the string.
Step 2: Check for a sign (+ or -) and store it.
Step 3: Initialize a result variable as 0. Traverse the string, converting valid numeric characters into digits. Stop at the first invalid character.
Step 4: Multiply the result by the stored sign before returning.
Step 5: Handle edge cases: empty strings, strings without valid numbers, or numbers exceeding integer limits.

**code**

    class Solution {
    public int myAtoi(String s) {
       int sign = 1, res = 0, idx = 0;

        
        while (idx < s.length() && s.charAt(idx) == ' ') {
            idx++;
        }

        
        if (idx < s.length() && (s.charAt(idx) == '-' 
                                 || s.charAt(idx) == '+')) {
            if (s.charAt(idx++) == '-') {
                sign = -1;
            }
        }

        
        while (idx < s.length() && s.charAt(idx) >= '0' 
                                       && s.charAt(idx) <= '9') {
            
           
            if (res > Integer.MAX_VALUE / 10 || 
                   (res == Integer.MAX_VALUE / 10 && s.charAt(idx) - '0' > 7)) {
                return sign == 1 ? Integer.MAX_VALUE : Integer.MIN_VALUE;
            }
          
            res = 10 * res + (s.charAt(idx++) - '0');
        }
        return res * sign;
    }
    }
