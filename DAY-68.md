Day 68 of GFG 160 Challenge: Reverse a Linked List in Groups of Given Size
Problem Statement
Given a singly linked list and an integer k, reverse the linked list in groups of size k.
If there are fewer than k nodes left, reverse them as well.

**🔹 Approach**

**Iterative Approach**

Use three pointers (prev, current, next) to reverse k nodes.
Keep track of the previous group's tail to connect it to the newly reversed section.
Continue until all nodes are processed.

**code**

    class Solution {
    public static Node reverseKGroup(Node head, int k) {
        // code here
        if(head == null){
            return head;
        }
        Node curr=head;
        Node newHead=null;
        Node tail=null;
        while(curr != null ){
            Node groupHead=curr;
            Node prev=null;
            Node nextNode=null;
            int count=0;
            while(curr != null && count <k){
                nextNode = curr.next;
                curr.next=prev;
                prev=curr;
                curr=nextNode;
                count++;
            }
            if(newHead == null){
                newHead = prev;
            }
            if(tail != null){
                tail.next=prev;
            }
            tail=groupHead;
        }
        return newHead;
        
    }
    static void printList(Node head){
        Node curr=head;
        while(curr != null){
            System.out.print(curr.data+" ");
            curr=curr.next;
        }
        System.out.println();
    }
    }
