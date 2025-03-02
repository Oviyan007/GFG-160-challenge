🔹 Day 89: K-Sum Paths in a Binary Tree
The K-Sum Path problem requires finding all paths in a binary tree where the sum of nodes in the path equals K. The path does not need to start from the root or end at a leaf, but it must follow the parent-child direction.

🔹 Approach
1️⃣ Prefix Sum + DFS (Backtracking)
Use DFS to traverse the tree.
Maintain a prefix sum map to track the sum of paths ending at the current node.
Check if (current sum - K) exists in the map → If yes, it means a valid subpath exists.
Backtrack after processing each node to restore the prefix sum state.


**code**

      class Solution {
    static int countPathUtil(Node node,int k,int currSum, HashMap<Integer,Integer> prefSums){
        if(node == null)
            return 0;
        int pathCount = 0;
        currSum += node.data;
        
        if(currSum == k)
            pathCount++;
        pathCount+=prefSums.getOrDefault(currSum - k,0);
        prefSums.put(currSum,prefSums.getOrDefault(currSum,0)+1);
        pathCount+=countPathUtil(node.left,k,currSum,prefSums);
        pathCount+=countPathUtil(node.right,k,currSum,prefSums);
        prefSums.put(currSum,prefSums.get(currSum)-1);
        return pathCount;
    }
    static int sumK(Node root,int k){
        HashMap<Integer, Integer> preSums=new HashMap<>();
        return countPathUtil(root,k,0,preSums);
    }
    
    }
