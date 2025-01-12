**Day 48 of GFG 160 Challenge 🚀**

💡 Day 48 Problem: Print Anagrams Together

🧠 Approach:
1️⃣ Using Hashing:

Use a dictionary to group words by their sorted characters.
For each word in the list, sort its characters alphabetically to create a key.
Append the word to the list corresponding to this key in the dictionary.
Finally, extract all the grouped anagrams from the dictionary values.

**code**

    class Solution {
    
    static final int MAX_CHAR=26;
    static String getHash(String s){
        StringBuilder hash=new StringBuilder();
        int [] freq=new int[MAX_CHAR];
        
        for(char ch:s.toCharArray()){
            freq[ch-'a']++;
        }
        for(int i=0;i<MAX_CHAR;i++){
            hash.append(freq[i]);
            hash.append("$");
        }
        return hash.toString();
    }
    
    public ArrayList<ArrayList<String>> anagrams(String[] arr) {
        ArrayList<ArrayList<String>> res= new ArrayList<>();
        Map<String, Integer> mp=new HashMap<>();
        for(int i=0;i<arr.length;i++){
            String key=getHash(arr[i]);
            if(!mp.containsKey(key)){
                mp.put(key, res.size());
                res.add(new ArrayList<>());
            }
            res.get(mp.get(key)).add(arr[i]);
        }
        return res;
    }
    }
