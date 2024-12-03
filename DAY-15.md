💡 Day 15 Problem: Check if Two Strings are Anagrams

🧠 Approach:
1️⃣ Understand the Problem:

Two strings are anagrams if they contain the same characters in the same frequency, irrespective of order.
2️⃣ Steps to Solve:

Step 1: Check if the lengths of the two strings are equal. If not, they can’t be anagrams.
Step 2: Use a frequency counter (e.g., a hash map or an array for English lowercase letters) to track the character counts of the first string.
Step 3: Traverse the second string and decrement the frequency for each character.
Step 4: After traversal, verify that all frequencies are zero. If so, the strings are anagrams; otherwise, they aren’t.

**Code**

      class Solution {
    // Function is to check whether two strings are anagram of each other or not.
    public static boolean areAnagrams(String s1, String s2) {

        HashMap<Character, Integer> map = new HashMap<>();
        // Your code here
        if(s1.length() != s2.length()){
            return false;
        }
        for(int i=0;i<s1.length();i++){
          if (map.containsKey(s1.charAt(i))) {
               
                map.put(s1.charAt(i),
                        map.get(s1.charAt(i)) + 1);
            }
            else {
               
                map.put(s1.charAt(i), 1);
            }
        }
         for (int i = 0; i < s2.length(); i++) {
 
           
            if (map.containsKey(s2.charAt(i))) {
 
                map.put(s2.charAt(i),
                        map.get(s2.charAt(i)) - 1);
            }
        }
         Set<Character> keys = map.keySet();
        for (Character key : keys) {
            if (map.get(key) != 0) {
                return false;
            }
        }
       
        return true;
    }
    }
