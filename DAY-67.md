**Day 67 of GFG 160 Challenge: Merge Two Sorted Linked Lists**



🔹 Approach
1️⃣ Use a Dummy Node:

Create a dummy node to store the merged list.
Maintain a tail pointer to track the last node.
2️⃣ Two-Pointer Traversal:

Compare the heads of both lists and attach the smaller one to tail.
Move the pointer forward in the list where the node was picked.
3️⃣ Attach Remaining Nodes:

If any list is not fully traversed, attach its remaining nodes to tail.

**code**

      class Solution {
    Node sortedMerge(Node head1, Node head2) {
        // code here
        if(head1 == null)
            return head2;
        if(head2 == null)
            return head1;
        if(head1.data <= head2.data){
            head1.next = sortedMerge(head1.next,head2);
            return head1;
            
        }
        else{
            head2.next = sortedMerge(head1,head2.next);
            return head2;
        }
    }
    static void printList(Node curr){
        while(curr != null){
            System.out.print(curr.data);
            if(curr.next != null)
                System.out.print("  ");
            curr=curr.next;
        }
        System.out.println();
    }
    }
