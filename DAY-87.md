**code**

      class Solution {
    // Function to check whether a Binary Tree is BST or not.
    boolean isBST(Node root) {
        // code here.
         Node curr=root;
         Node pre;
         int prevValue=Integer.MIN_VALUE;
        while(curr != null){
            if(curr.left == null){
                if(curr.data <= prevValue){
                    return false;
                }
                prevValue=curr.data;
                curr=curr.right;
            }else{
                pre=curr.left;
                while(pre.right != null && pre.right != curr){
                    pre=pre.right;
                }
                if(pre.right == null){
                    pre.right=curr;
                    curr=curr.left;
                }else{
                    pre.right=null;
                    if(curr.data <= prevValue){
                        return false;
                    }
                    prevValue=curr.data;
                    curr=curr.right;
                }
            }
        }
    return true;
    }
    }
