class Tree {
    // Function to serialize a tree and return a list containing nodes of tree.
    public ArrayList<Integer> serialize(Node root) {
        ArrayList<Integer> arr=new ArrayList<>();
        Queue<Node> q=new LinkedList<>();
        q.add(root);
        while(!q.isEmpty()){
            Node curr=q.poll();
            if(curr == null){
                arr.add(-1);
                continue;
            }
            arr.add(curr.data);
            q.add(curr.left);
            q.add(curr.right);
        }
        
        return arr;
        // code here
    }

    // Function to deserialize a list and construct the tree.
    public Node deSerialize(ArrayList<Integer> arr) {
        if(arr.get(0) == -1) return null;
        Node root =new Node(arr.get(0));
        Queue <Node> q=new LinkedList<>();
        q.add(root);
        int i=1;
        while(!q.isEmpty()){
            Node curr=q.poll();
            if(arr.get(i) != -1){
                Node left=new Node(arr.get(i));
                curr.left=left;
                q.add(left);
            }
            i++;
            if(arr.get(i) != -1){
                Node right=new Node(arr.get(i));
                curr.right=right;
                q.add(right);
            }
            i++;
        }
        return root;
        
        // code here
    }
    static void printLevelOrder(Node root){
        if(root == null){
            System.out.print("N ");
            return;
        }
        Queue<Node> queue=new LinkedList<>();
        queue.add(root);
        int nonNull=1;
        while(!queue.isEmpty() && nonNull >0){
            Node curr=queue.poll();
            if(curr == null){
                System.out.print("N ");
                continue;
            }
            nonNull--;
            System.out.print(curr.data + " ");
            queue.add(curr.left);
            queue.add(curr.right);
            if(curr.left != null)
                nonNull++;
            if(curr.right != null)
                nonNull++;
        }
    }
      };
