Day 66 of GFG 160 Challenge: Rotate a Linked List
Problem Statement
Given a singly linked list and an integer k, rotate the list k places to the right. That means the last k nodes move to the front while maintaining the relative order.

🔹 Approach
1️⃣ Find Length:

Traverse the list to count the total number of nodes (let’s call it n).
2️⃣ Optimize Rotation:

Since rotating n times results in the same list, we only need to rotate k % n times.
3️⃣ Find the Breakpoint:

Locate the (n - k)th node.
Update its next pointer to None.
4️⃣ Move Last Part to Front:

Set the (n-k+1)th node as the new head.
Connect the old tail to the old head.

**code**

      class Solution {
    public Node rotate(Node head, int k) {
        // add code here
        if(k == 0 || head == null)
            return head;
        Node curr = head;
        int len =1;
    
        while(curr.next != null){
            curr=curr.next;
            len +=1;
        }
        k %= len;
        if(k == 0)
            return head;
        curr.next = head;
        
        curr=head;
        for(int i=1;i<k;i++)
            curr = curr.next;
        head = curr.next;
        curr.next=null;
        return head;
    }
    static void printList(Node node){
        while(node != null){
            System.out.print(node.data + " ");
            node =node.next;
        }
        System.out.println();
    }
    }
