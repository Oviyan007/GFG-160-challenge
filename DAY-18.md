
**💡 Day 18 Problem: Check if Two Strings are Rotations of Each Other**

**🧠 Approach:**

1️⃣ Understand the Problem:

Two strings are rotations of each other if you can form one string by rotating the other.
2️⃣ Steps to Solve:

Step 1: Check if the lengths of the two strings are equal. If not, they cannot be rotations.
Step 2: Concatenate the first string with itself.
Step 3: Check if the second string is a substring of this concatenated result.
Step 4: If it is, the strings are rotations of each other; otherwise, they are not.



**code**

      class Solution {
    // Function to check if two strings are rotations of each other or not.
    static int[] computeLPSArray(String pat) {
        int n = pat.length();
        int[] lps = new int[n];
      
        int len = 0;

        
        lps[0] = 0;

       
        int i = 1;
        while (i < n) {
          
           
            if (pat.charAt(i) == pat.charAt(len)) {
                len++;
                lps[i] = len;
                i++;
            }
          
            
            else {
              
                
                if (len != 0) {
                    len = lps[len - 1];
                }
              
                
                else {
                    lps[i] = 0;
                    i++;
                }
            }
        }
        return lps;
    }
    
    public static boolean areRotations(String s1, String s2) {
        // Your code here
        String txt = s1 + s1;
        String pat = s2;
        
        
        int n = txt.length();
        int m = pat.length();

        
        int[] lps = computeLPSArray(pat);
      
        int i = 0; 
        int j = 0;
        while (i < n) {
            if (pat.charAt(j) == txt.charAt(i)) {
                j++;
                i++;
            }

            if (j == m) {
                return true;
            }

            
            else if (i < n && pat.charAt(j) != txt.charAt(i)) {

                
                if (j != 0)
                    j = lps[j - 1];
                else
                    i = i + 1;
            }
        }
        return false;
    }
    }
