## Aim:
Write a Java program to calculate the length of a singly linked list.

Input Format

    First line: integer n — number of nodes in the linked list

    Next n integers: values of the linked list nodes

Output Format

    Print the length of the linked list.


## Program:
```
import java.util.Scanner;

public class LinkedListLength {

    public static int getLength(ListNode head) {
        int count = 0;
        ListNode current = head;
        while (current != null) {
            count++;
            current = current.next;
        }
        return count;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        if (!scanner.hasNextInt()) {
            System.out.println(0);
            return;
        }

        int n = scanner.nextInt();
        if (n <= 0) {
            System.out.println(0);
            return;
        }

        ListNode head = new ListNode(scanner.nextInt());
        ListNode current = head;

        for (int i = 1; i < n; i++) {
            if (scanner.hasNextInt()) {
                current.next = new ListNode(scanner.nextInt());
                current = current.next;
            }
        }

        int length = getLength(head);
        System.out.println(length);
    }
}

class ListNode {
    int data;
    ListNode next;

    ListNode(int data) {
        this.data = data;
        this.next = null;
    }
}


```
