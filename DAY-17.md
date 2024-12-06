**💡 Day 17 Problem: First Non-Repeating Character in a String**

**🧠 Approach:**

1️⃣ Understand the Problem:

Find the first character in the string that does not repeat. If no such character exists, return a placeholder (e.g., -1).
2️⃣ Steps to Solve:

Step 1: Use a hash map (or dictionary) to store the frequency of each character in the string.
Step 2: Traverse the string and populate the frequency map.
Step 3: Iterate through the string again. For each character, check its frequency in the map. Return the first character with a frequency of 1.
Step 4: If no non-repeating character is found, return -1.

**code**

      class Solution {
    // Function to find the first non-repeating character in a string.
    static char nonRepeatingChar(String s) {
        for(int i=0;i<s.length();i++){
        boolean found=false;
            for(int j=0;j<s.length();j++){
                if(i!=j && s.charAt(i) == s.charAt(j)){
                    found=true;
                    break;
                }
            }
        if(!found){
            return s.charAt(i);
        }
        }
        return '$';
    }
    }
