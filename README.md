package com.journaldev.linkedlist.reverse;

public class MyLinkedList {

public Node head;

public static class Node {

public Node next;

public Object data;

public Node(Object data) {
this.data = data;
next = null;
}
}
}



package com.journaldev.linkedlist.loopDetection;

import com.journaldev.linkedlist.reverse.MyLinkedList;
import com.journaldev.linkedlist.reverse.MyLinkedList.Node;

public class DetectLinkedListLoop {


public static void main(String[] args) {

        MyLinkedList myLinkedList = new MyLinkedList();

        myLinkedList.head = new Node(1);
        myLinkedList.head.next = new Node(2);
        Node node = myLinkedList.head.next.next = new Node(3);
        myLinkedList.head.next.next.next = new Node(4);
        myLinkedList.head.next.next.next.next = new Node(5);
        myLinkedList.head.next.next.next.next.next = node;

        System.out.println("Has Loop? " + hasLoop(myLinkedList));
    }


private static boolean hasLoop(MyLinkedList myLinkedList) {

        Node head = myLinkedList.head;

        Node slow = head;
        Node fast = head;

        boolean loop = false;

        while (slow != null && fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;

            if (slow == fast) {
                loop = true;
                break;
            }
        }

        return loop;
    }

}
