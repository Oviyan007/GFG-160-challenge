**Day 85: Inorder Traversal of a Binary Tree**

In inorder traversal, we visit nodes in the following order:
Left → Root → Right

🔹 Approach 1: Recursive Traversal
Recursively visit the left subtree.
Process the root node.
Recursively visit the right subtree.

**code**

    class Solution {
    // Function to return a list containing the inorder traversal of the tree.
    ArrayList<Integer> inOrder(Node root) {
        // Code
        ArrayList<Integer> res=new ArrayList<>();
        Node curr=root;
        while(curr != null){
            if(curr.left == null){
                res.add(curr.data);
                curr=curr.right;
            }
            else{
                Node prev=curr.left;
                while(prev.right != null && prev.right!= curr){
                    prev=prev.right;
                }
                if(prev.right == null){
                    prev.right=curr;
                    curr=curr.left;
                }
                else{
                    prev.right=null;
                    res.add(curr.data);
                    curr=curr.right;
                }
            }
        }
        return res;
    }
    
    }
