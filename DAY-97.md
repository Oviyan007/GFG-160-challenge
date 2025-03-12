**Code**


    
    class Solution {
    // Function to merge K sorted linked list.
    static Node mergeTwo(Node head1,Node head2){
        Node dummy = new Node(-1);
        Node curr=dummy;
        while(head1 != null && head2 != null){
            if(head1.data <= head2.data){
                curr.next=head1;
                head1=head1.next;
                
            }
            else{
                curr.next=head2;
                head2=head2.next;
            }
            curr=curr.next;
        }
        if(head1 != null){
            curr.next=head1;
        }else{
            curr.next=head2;
        }
        return dummy.next;
    }
     static Node mergeKLists(List<Node> arr) {
        // Add your code here.
        Node res = null;
        for(Node node:arr)
            res=mergeTwo(res,node);
        return res;
    }
    static void printList(Node node){
        while(node !=null){
            System.out.print(node.data +" ");
            node =node.next;
        }
    }
    }
