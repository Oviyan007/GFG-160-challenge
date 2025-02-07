Day 73 of GFG 160 Challenge: Remove Loop in Linked List
Problem Statement
Given a singly linked list with a loop, your task is to remove the loop without losing any nodes.


🔹 Efficient Approach: Floyd’s Cycle Detection + Fix the Last Node
✔ Step 1: Use Floyd’s Cycle Detection Algorithm (Tortoise & Hare 🐢🐇) to detect the loop.
✔ Step 2: If a cycle exists, find the first node of the loop using the meeting point technique.
✔ Step 3: Traverse the loop until the last node of the cycle (node pointing back to the first loop node).
✔ Step 4: Set lastNode.next = NULL to break the loop.

✔ Time Complexity: O(N)
✔ Space Complexity: O(1)

**code**

      class Solution {
    // Function to remove a loop in the linked list.
    public static void removeLoop(Node head) {
        if(head == null || head.next == null)
            return ;
        
        Node slow =head, fast=head;
        slow =slow.next;
        fast=fast.next.next;
        
        while(fast != null && fast.next != null){
            if(slow == fast)
                break;
            slow=slow.next;
            fast=fast.next.next;
        }
        if(slow == fast){
            slow=head;
            if(slow != fast){
                while(slow.next != fast.next){
                    slow=slow.next;
                    fast=fast.next;
                }
                fast.next=null;
            }
            else{
                while(fast.next!=slow){
                    fast=fast.next;
                }
                fast.next=null;
            }
        }
        // code here
    }
    static void printList(Node curr){
        while(curr != null){
            System.out.print(curr.data+" ");
            curr=curr.next;
        }
    }
      }
