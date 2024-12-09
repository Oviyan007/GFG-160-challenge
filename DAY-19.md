**Day 19 of GFG 160 Challenge 🚀**

💡 Day 19 Problem: Search Pattern Using KMP Algorithm

**🧠 Approach:**
1️⃣ Understand the Problem:

The task is to efficiently find all occurrences of a pattern string in a given text using the Knuth-Morris-Pratt (KMP) algorithm.
2️⃣ Steps to Solve:

Step 1: Preprocess the Pattern (Build the LPS Array)
Create a Longest Prefix Suffix (LPS) array to store the length of the longest proper prefix that is also a suffix for each substring of the pattern.
Step 2: Search the Pattern in the Text
Use the LPS array to skip unnecessary comparisons while matching the pattern with the text.
Step 3: Traverse the text and the pattern, adjusting indices based on matches and mismatches, using the LPS values for efficient skipping.

**code**

    class Solution {
     static void constructLps(String pat, int[] lps) {
        
       
        int len = 0;

        lps[0] = 0;

        int i = 1;
        while (i < pat.length()) {
            
          
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
    }

    ArrayList<Integer> search(String pat, String txt) {
        // your code here
      int n = txt.length();
        int m = pat.length();

        int[] lps = new int[m];
        ArrayList<Integer> res = new ArrayList<>();

        constructLps(pat, lps);

        
        int i = 0;
        int j = 0;

        while (i < n) {
            
            if (txt.charAt(i) == pat.charAt(j)) {
                i++;
                j++;

                if (j == m) {
                    res.add(i - j);
                    
                    
                    j = lps[j - 1];
                }
            }
            
            
            else {
                
                
                if (j != 0)
                    j = lps[j - 1];
                else
                    i++;
            }
        }
        return res; 
       
    }
    }
