**Day 92: Lowest Common Ancestor (LCA) in a Binary Tree**
The Lowest Common Ancestor (LCA) of two nodes in a Binary Tree is the lowest node in the tree that has both given nodes as descendants.

🔹 Approaches
1️⃣ Recursive DFS Approach (General Binary Tree)
Traverse the tree from the root.
If the current node is either of the two nodes, return it.
If both left and right calls return non-null values, the current node is the LCA.
If only one side returns a non-null value, propagate that value up.


**code**

    class Solution {
    Node LCA(Node root, Node n1, Node n2) {
        // your code here.
        while(root != null){
            if(root.data > n1.data && root.data > n2.data)
                root=root.left;
            else if(root.data < n1.data && root.data < n2.data)
                root=root.right;
            else
                break;
        }
        return root;
    }
    }
