Day 72 of GFG 160 Challenge: Find First Node of Loop in Linked List
Problem Statement
Given a singly linked list with a cycle, find the first node of the cycle. If no cycle exists, return NULL.


🔹 Efficient Approach: Floyd’s Cycle Detection + Finding the Loop Start
✔ Step 1: Use the Floyd’s Cycle Detection Algorithm (Tortoise & Hare 🐢🐇)
✔ Step 2: After detecting the cycle, place one pointer at the head and another at the meeting point.
✔ Step 3: Move both one step at a time until they meet. The meeting point is the first node of the loop.



**code**

    class Solution {
    public static Node findFirstNode(Node head) {
        // code here
        Node slow =head;
        Node fast =head;
        while(fast != null && fast.next != null){
            slow =slow.next;
            fast=fast.next.next;
            if(slow == fast){
                slow=head;
                while(slow != fast){
                    slow =slow.next;
                    fast =fast.next;
                }
                return slow;
            }
        }
        return null;
        
    }
    }
