![image](https://github.com/user-attachments/assets/69bc00bd-4342-4310-a118-ded57fef2311)



**code**





    class Solution {
    static boolean isLeaf(Node node){
        return node.left == null && node.right == null;
    }
    static void collectBoundaryLeft(Node root, ArrayList<Integer> res){
        if(root == null)
            return;
        Node curr=root;
        while(curr != null){
            if(!isLeaf(curr)) res.add(curr.data);
            if(curr.left != null)
                curr=curr.left;
            else
                curr=curr.right;
        }
    }
    static void collectLeaves(Node root,ArrayList<Integer> res){
        if(root == null) return;
        if(isLeaf(root)){
            res.add(root.data);
            return;
        }
        collectLeaves(root.left,res);
        collectLeaves(root.right,res);
    }
    static void collectBoundaryRight(Node root,ArrayList<Integer> res){
        if(root == null)
            return;
        ArrayList<Integer> temp=new ArrayList<>();
        Node curr=root;
       while(curr != null){
           if(!isLeaf(curr)) temp.add(curr.data);
           if(curr.right != null) curr = curr.right;
           else curr = curr.left;
       }
       for(int i=temp.size()-1;i>=0;i--){
           res.add(temp.get(i));
       }
    }
    ArrayList<Integer> boundaryTraversal(Node root) {
        // code here
        ArrayList<Integer> res=new ArrayList<>();
        if(root == null)
            return res;
        if(!isLeaf(root))
            res.add(root.data);
        collectBoundaryLeft(root.left,res);
        collectLeaves(root,res);
        collectBoundaryRight(root.right,res);
        return res;
    }
    }
