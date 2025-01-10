
💡 Day 46 Problem: Union of Arrays with Duplicates

🧠 Approach:
1️⃣ Using a Set:

Combine both arrays into one.
Convert the combined array into a set to eliminate duplicates.
Count the number of elements in the set to get the union size.

**code**

      class Solution {
    public static int findUnion(int a[], int b[]) {
        // code here
        Set<Integer> st=new HashSet<>();
        for(int num:a){
            st.add(num);
        }
        for(int num:b){
            st.add(num);
        }
       
        
        return st.size();
    }
    }
