![image](https://github.com/user-attachments/assets/2a2601a9-6845-4c31-ae20-18870558c50f)
💡 Day 44 Problem: Intersection of Two Arrays (with Duplicates)

🧠 Approach:
To find the intersection of two arrays while including duplicates:

1️⃣ Using Hash Maps:

Create a hash map to store the frequency of each element in the first array.
Iterate through the second array:
If an element exists in the hash map with a non-zero frequency, add it to the result and decrement its frequency in the hash map.

**code**

      class Solution {
    public ArrayList<Integer> intersectionWithDuplicates(int[] a, int[] b) {
        // code here
        
        HashSet<Integer> sa=new HashSet<>();
        for(int num : a){
            sa.add(num);
        }
        ArrayList<Integer> res=new ArrayList<Integer>();
        for(int num:b){
            if(sa.contains(num)){
                res.add(num);
                sa.remove(num);
            }
        }
        return res;
    }
    }
