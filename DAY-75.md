Day 75 of GFG 160 Challenge: Permutations of a String


🔹 Approach 1: Backtracking (Recursion)
🔹 Idea:

Swap each character with every other character.
Recurse to generate further permutations.
Restore (backtrack) and repeat for the next character.

**code**

    class Solution {
    static void genPermutation(int n,StringBuilder curr,Map<Character,Integer>cnt,List< String>res){
        if(curr.length()==n){
            res.add(curr.toString());
            return;
        }
        for(Map.Entry<Character,Integer> entry:cnt.entrySet()){
            char c=entry.getKey();
            int count =entry.getValue();
            if(count == 0)
                continue;
            curr.append(c);
            cnt.put(c,count-1);
            genPermutation(n,curr,cnt,res);
            curr.deleteCharAt(curr.length()-1);
            cnt.put(c,count);
        }
    }
    public ArrayList<String> findPermutation(String s) {
        // Code here
        ArrayList<String> res=new ArrayList<>();
        Map<Character,Integer>cnt=new HashMap<>();
        for(char c : s.toCharArray())
            cnt.put(c,cnt.getOrDefault(c,0) + 1);
        StringBuilder curr=new StringBuilder();
        genPermutation(s.length(),curr,cnt,res);
        return res;
    }
    }
