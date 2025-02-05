Day 71 of GFG 160 Challenge: Detect Cycle in a Linked List
Problem Statement
Given a singly linked list, determine whether it contains a cycle (loop).


🔹 Efficient Approach: Floyd’s Cycle Detection (Tortoise & Hare) 🐢🐇
✔ Idea: Use two pointers:

Slow Pointer (slow) moves one step at a time.
Fast Pointer (fast) moves two steps at a time.
If there is a cycle, they will meet at some point.
If fast reaches NULL, the list has no cycle.

**code**

    class Solution {
    // Function to check if the linked list has a loop.
    public static boolean detectLoop(Node head) {
        // Add code here
        Node slow =head,fast=head;
        while(slow != null && fast!= null && fast.next != null){
            slow =slow.next;
            fast=fast.next.next;
            if(slow == fast){
                return true;
            }
        }
        return false;
    }
      }
