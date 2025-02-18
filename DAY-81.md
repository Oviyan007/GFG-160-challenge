**Day 81: Height of a Binary Tree**

The height of a binary tree is the number of edges in the longest path from the root to a leaf node. (Alternatively, it can be measured in terms of the number of nodes along the path.)

🔹 Approach 1: Recursive (DFS - Postorder Traversal)
Base Case: If the node is NULL, return 0.
Recursive Call: Compute the height of the left and right subtrees.
Return the Maximum Height: Height = 1 + max(leftHeight, rightHeight).

**code**

    class Solution {
    // Function to find the height of a binary tree.
    int height(Node node) {
        // code here
        if( node == null ) return 0;
        Queue<Node> q=new LinkedList<>();
        q.add(node);
        int depth=0;
        while(!q.isEmpty()){
            int levelSize=q.size();
            for(int i=0;i<levelSize;i++){
                Node curr=q.poll();
                if(curr.left != null) q.add(curr.left);
                if(curr.right != null) q.add(curr.right);
            }
            depth++;
        }
        return depth - 1;
    }
    }

  
