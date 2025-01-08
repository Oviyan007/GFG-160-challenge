
**💡 Day 43 Problem: Count Pairs with a Given Sum**

🧠 Approach:
To count the pairs of elements in an array that sum up to a given value 
target
target:

1️⃣ Hash Map Technique:

Use a hash map to store the frequency of each number in the array.
For each number, calculate the complement: 
complement
=
target
−
current_number
complement=target−current_number.
Check if the complement exists in the hash map. If it does, add its frequency to the count.
Update the hash map to include the current number.

**code**

      class Solution {
    public List<List<Integer>> findTriplets(int[] arr) {
        // Your code here
        Set<ArrayList<Integer>> resSet=new HashSet<>();
        int n=arr.length;
        Map<Integer,List<int[]>> mp=new HashMap<>();
        for(int i=0;i<n;i++){
            for(int j=i+1;j<n;j++){
                mp.computeIfAbsent(arr[i]+arr[j],k->new ArrayList<>()).add(new int []{i,j});
            }
        }
        for(int i=0;i<n;i++){
            int rem=-arr[i];
            if(mp.containsKey(rem)){
                List<int[]> pairs=mp.get(rem);
                for(int [] p:pairs){
                    if(p[0]!=i&&p[1]!=i){
                        ArrayList<Integer> curr=new ArrayList<>(Arrays.asList(i,p[0],p[1]));
                        Collections.sort(curr);
                        resSet.add(curr);
                    }
                }
            }
        }
    
        
    return new ArrayList<>(resSet);
    }   
    }
