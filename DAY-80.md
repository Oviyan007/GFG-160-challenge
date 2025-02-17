Day 80: Level Order Traversal
Given a binary tree, perform a level order traversal, meaning we traverse nodes level by level from left to right.

🔹 Approach: Using Queue (BFS)
Use a Queue → Start with the root node and push it into the queue.
Process Level by Level → Dequeue a node, print/store its value, and enqueue its left and right children (if present).
Continue Until the Queue is Empty → This ensures all levels are traversed in order.

**code**

    class Solution {
    public ArrayList<ArrayList<Integer>> levelOrder(Node root) {
        // Your code here
        if(root == null)
            return new ArrayList<>();
        Queue<Node> q=new LinkedList<>();
        ArrayList<ArrayList<Integer>> res=new ArrayList<>();
        q.add(root);
        int currLevel=0;
        while(!q.isEmpty()){
            int len=q.size();
            res.add(new ArrayList<>());
            for(int i=0;i<len;i++){
                Node node=q.poll();
                res.get(currLevel).add(node.data);
                if(node.left != null)
                    q.add(node.left);
                if(node.right != null)
                    q.add(node.right);
                    
            }
            currLevel++;
        }
        return res;
    }
    }
