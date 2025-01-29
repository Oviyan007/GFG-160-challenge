Day 65 of GFG 160 Challenge 🚀
💡 Day 65 Problem: Reverse a Linked List

🧠 Approach:
The task is to reverse a singly linked list, meaning the last node should become the first, and the first should become the last.

🔹 Iterative Approach (Efficient)
1️⃣ Initialize Three Pointers:

prev → Initially None
curr → Points to the head
next → Helps track the next node
2️⃣ Reverse Pointers:

Iterate through the list and adjust next pointers.
Move prev and curr forward.
3️⃣ Update the Head:

After traversal, prev points to the new head.

**code**

    class Solution {
    Node reverseList(Node head) {
        // code here
        Stack<Node> stack=new Stack<>();
        Node temp=head;
        while(temp != null){
            stack.push(temp);
            temp=temp.next;
        }
        if(!stack.isEmpty()){
            head=stack.pop();
            temp=head;
            while(!stack.isEmpty()){
                temp.next=stack.pop();
                temp=temp.next;
            }
            temp.next=null;
        }
        return head;
    }
    
    static void printList(Node node){
        while(node != null){
            System.out.print(" "+node.data);
            node=node.next;
        }
        System.out.println();
    }
    }
