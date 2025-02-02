 **Day 69 of GFG 160 Challenge: Add Two Numbers Represented as Linked Lists**
**Problem Statement**
Given two singly linked lists, where each node represents a digit of a number (in reverse order), add the two numbers and return the sum as a linked list.

**🔹 Approach**

1️⃣ Initialize Pointers: Use p1 and p2 to traverse both linked lists.
2️⃣ Maintain a Carry: Keep track of the carry from the previous sum.
3️⃣ Iterate Over Lists: Add corresponding digits, store the last digit, and carry over the rest.
4️⃣ Handle Unequal Lengths: If one list is longer, continue adding with the carry.
5️⃣ Handle Extra Carry: If there's a leftover carry, create a new node.



**code**

    class Solution {
    static Node reverse(Node head) {
        // code here
        Node prev=null;
        Node curr=head;
        Node next;
        while(curr!=null){
            next=curr.next;
            curr.next=prev;
            prev=curr;
            curr=next;
        }
        return prev;
    }
    static int countNodes(Node head){
        int len=0;
        Node curr=head;
        while(curr != null){
            len+=1;
            curr=curr.next;
        }
        return len;
    }
    static Node trimLeadingZeros(Node head){
        while(head != null && head.data ==0){
            head=head.next;
        }
        return head;
    }
    static Node addTwoLists(Node num1,Node num2){
        num1=trimLeadingZeros(num1);
        num2=trimLeadingZeros(num2);
        int len1=countNodes(num1);
        int len2=countNodes(num2);
        if(len1 < len2){
            return addTwoLists(num2,num1);
        }
        int carry =0;
        num1=reverse(num1);
        num2=reverse(num2);
        Node res=num1;
        while(num2 != null || carry !=0){
            num1.data+=carry;
            
            if(num2!=null){
                num1.data+=num2.data;
                num2=num2.next;
            }
            carry=num1.data/10;
            num1.data=num1.data%10;
            if(num1.next == null&&carry!=0){
                num1.next=new Node(0);
            }
            num1=num1.next;
        }
        return reverse(res);
    }
    static void printList(Node head){
        Node curr=head;
        while(curr!=null){
            System.out.print(curr.data+" ");
            curr=curr.next;
        }
        System.out.println();
    }
    }
