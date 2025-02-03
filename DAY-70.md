Day 70 of GFG 160 Challenge: Clone a Linked List with Random Pointers
Problem Statement
Given a singly linked list where each node has two pointers:
1️⃣ Next Pointer → Points to the next node.
2️⃣ Random Pointer → Points to any node (or NULL).


🔹 Approach

1️⃣ Step 1: Create Interleaved Nodes

Insert a copy of each node right after the original node.
Example:
matlab
Copy
Edit
Original: 1 → 2 → 3 → 4
Modified: 1 → 1' → 2 → 2' → 3 → 3' → 4 → 4'
2️⃣ Step 2: Copy Random Pointers

copy->random = original->random->next
3️⃣ Step 3: Separate the Cloned List

Extract the copied nodes to form the deep copy list.

**code**

      class Solution {
    public Node cloneLinkedList(Node head) {
        // code here
        if(head == null){
            return null;
        }
        Node curr=head;
        while(curr != null){
            Node newNode=new Node(curr.data);
            newNode.next=curr.next;
            curr.next=newNode;
            curr=newNode.next;
        }
        curr=head;
        while(curr != null){
            if(curr.random != null){
                curr.next.random=curr.random.next;
            }
            curr=curr.next.next;
        }
        curr=head;
        Node cloneHead=head.next;
        Node clone=cloneHead;
        while(clone.next != null){
            curr.next=curr.next.next;
            clone.next=clone.next.next;
            curr=curr.next;
            clone=clone.next;
        }
        curr.next=null;
        clone.next=null;
        return cloneHead;
        
    }
    public static void printList(Node head){
        while(head != null){
            System.out.print(head.data+" ");
            if(head.random != null){
                System.out.print(head.random.data);
            }
            else{
                System.out.print("null");
            }
            System.out.print(")");
            if(head.next != null){
                System.out.print(" ->");
            }
            head=head.next;
        }
        System.out.println();
    }
      }
