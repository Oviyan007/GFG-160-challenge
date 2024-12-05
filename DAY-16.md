💡 Day 16 Problem: Add Two Binary Strings

🧠 Approach:
1️⃣ Understand the Problem:

Given two binary strings, compute their sum and return the result as a binary string.
2️⃣ Steps to Solve:

Step 1: Start from the rightmost end of both strings. Use two pointers to traverse the strings backward.
Step 2: Initialize a variable carry to store the carry-over from the sum of two binary digits.
Step 3: For each position, calculate the sum of corresponding digits and the carry. Append the result modulo 2 to the result string. Update the carry as sum // 2.
Step 4: After traversing both strings, if a carry remains, append it to the result.
Step 5: Reverse the result string to get the correct binary sum.

**code**
    class Solution {
    static String trimLeadingZeros(String s) {

       
        int firstOne = s.indexOf('1');
        return (firstOne == -1) ? "0"
                                : s.substring(firstOne);
    }
    public String addBinary(String s1, String s2) {
         s1 = trimLeadingZeros(s1);
        s2 = trimLeadingZeros(s2);
        
        int n = s1.length();
        int m = s2.length();

        // Swap the strings if s1 is of smaller length
        if (n < m) {
            return addBinary(s2, s1);
        }

        int j = m - 1;
        int carry = 0;
        StringBuilder result = new StringBuilder();

        // Traverse both strings from the end
        for (int i = n - 1; i >= 0; i--) {

            // Current bit of s1
            int bit1 = s1.charAt(i) - '0';
            int sum = bit1 + carry;

            // If there are remaining bits in s2, add them
            // to the sum
            if (j >= 0) {

                // Current bit of s2
                int bit2 = s2.charAt(j) - '0';
                sum += bit2;
                j--;
            }

            // Calculate the result bit and update carry
            int bit = sum % 2;
            carry = sum / 2;

            // Update the current bit in result
            result.append((char)(bit + '0'));
        }

        // If there's any carry left, update the result
        if (carry > 0)
            result.append('1');

        return result.reverse().toString();
    }
    }
