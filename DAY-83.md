**Day 83: Mirror of a Binary Tree**

A mirror tree is a tree where the left and right subtrees of every node are swapped. It’s essentially the reflection of the original tree.

🔹 Approach: Recursive Swap
Base Case: If the node is None, return.
Swap left and right subtrees for the current node.
Recursively call the function for left and right subtrees.

**code**

    class Solution {
    // Function to convert a binary tree into its mirror tree.
    void mirror(Node root) {
        // Your code here
        if(root == null)
            return;
        Queue<Node> queue=new LinkedList<>();
        queue.add(root);
        while(!queue.isEmpty()){
            Node curr=queue.poll();
            Node temp=curr.left;
            curr.left=curr.right;
            curr.right=temp;
            if(curr.left != null)
                queue.add(curr.left);
            if(curr.right != null)
                queue.add(curr.right);
        }
    }
    static void levelOrder(Node root){
        if(root == null){
            System.out.print("N ");
            return;
        }
        Queue<Node>queue=new LinkedList<>();
        queue.add(root);
        while(!queue.isEmpty()){
            Node curr =queue.poll();
            if(curr == null){
                System.out.print("N ");
                continue;
            }
            System.out.print(curr.data+" ");
            queue.add(curr.left);
            queue.add(curr.right);
        }
    }
    }
