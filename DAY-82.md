Day 82: Diameter of a Binary Tree
The diameter (or width) of a binary tree is the longest path between any two nodes in the tree. This path may or may not pass through the root.

🔹 Approach 1: Brute Force (Recursive)
Compute the height of the left and right subtrees.
Compute the diameter of the left and right subtrees.
The diameter is the maximum of:
leftHeight + rightHeight + 1 (path passing through the root)
diameter of left subtree
diameter of right subtree


**code**

    class Solution {
    static int diameterRecur(Node root,int[] res){
        if(root == null)
            return 0;
        int lHeight=diameterRecur(root.left,res);
        int rHeight=diameterRecur(root.right,res);
        res[0]=Math.max(res[0],lHeight + rHeight);
        
        return 1 + Math.max(lHeight,rHeight);
        
    }
    static int diameter(Node root) {
        // Your code here
        int [] res=new int[1];
        diameterRecur(root,res);
        return res[0];
    }
    }
