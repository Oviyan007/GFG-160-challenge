Day 90: Kth Smallest Element in a BST
The Kth Smallest Element in a BST problem requires finding the k-th smallest node value in a Binary Search Tree (BST). Given the properties of a BST (left subtree < root < right subtree), an inorder traversal gives the elements in sorted order.

🔹 Approach
1️⃣ Inorder Traversal (Recursive & Iterative)
Perform an inorder traversal (Left → Root → Right).
Keep a counter to track how many elements have been visited.
Return the k-th element when the counter reaches k.

**code **

    class Solution {
    // Return the Kth smallest element in the given BST
    static void inorderTraversal(Node root,int [] k,int [] result){
        if(root == null || k[0] <= 0) return ;
        inorderTraversal(root.left,k,result);
        k[0]--;
        if(k[0]== 0){
            result[0]=root.data;
            return;
        }
        inorderTraversal(root.right,k,result);
    }
    public int kthSmallest(Node root, int k) {
        // Write your code here
        int [] result={-1};
        int [] kRef={k};
        inorderTraversal(root,kRef,result);
        return result[0];
    }
    }
