## Aim:

You are required to implement a queue data structure using an array with support for the following operations:

    Enqueue (1 x) – Add the integer x to the rear of the queue.

        If the queue is full, print:

        Queue is full! Cannot enqueue x

    Dequeue (2) – Remove the element from the front of the queue.

        If the queue is empty, print:

        Queue is empty! Cannot dequeue.

    Peek (3) – Print the element at the front of the queue without removing it.

        If the queue is empty, print:

        Queue is empty!

    Display (4) – Print all elements of the queue from front to rear, separated by spaces.

        If the queue is empty, print:

        Queue is empty!

Constraints

    1 ≤ capacity ≤ 1000

    1 ≤ number of operations ≤ 10^5

    -10^9 ≤ x ≤ 10^9

    Operations are processed in the order given until EOF.

    The queue must be implemented using arrays only (no LinkedList or Java built-in Queue class).

## Program:

```

import java.util.*;

public class ArrayQueue {
    private int[] queue;
    private int front, rear, size, capacity;

    public ArrayQueue(int capacity) {
        this.capacity = capacity;
        queue = new int[capacity];
        front = 0;
        rear = 0;
        size = 0;
    }

    public void enqueue(int data) {
        if (isFull()) {
            System.out.println("Queue is full! Cannot enqueue " + data);
            return;
        }

        queue[rear] = data;
        rear = (rear + 1) % capacity; // circular increment
        size++;
        System.out.println(data + " enqueued");
    }

    public void dequeue() {
        if (isEmpty()) {
            System.out.println("Queue is empty! Cannot dequeue.");
            return;
        }

        int removed = queue[front];
        front = (front + 1) % capacity; // circular increment
        size--;
        System.out.println(removed + " dequeued");
    }

    public void peek() {
        if (isEmpty()) {
            System.out.println("Queue is empty!");
            return;
        }
        System.out.println("Front element: " + queue[front]);
    }

    public void display() {
        if (isEmpty()) {
            System.out.println("Queue is empty!");
            return;
        }

        for (int i = 0; i < size; i++) {
            int index = (front + i) % capacity;
            System.out.print(queue[index] + " ");
        }
        System.out.println();
    }

    public boolean isFull() {
        return size == capacity;
    }

    public boolean isEmpty() {
        return size == 0;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int cap = sc.nextInt();
        ArrayQueue q = new ArrayQueue(cap);

        while (sc.hasNext()) {
            int command = sc.nextInt();
            switch (command) {
                case 1:
                    int val = sc.nextInt();
                    q.enqueue(val);
                    break;
                case 2:
                    q.dequeue();
                    break;
                case 3:
                    q.peek();
                    break;
                case 4:
                    q.display();
                    break;
                default:
                    System.out.println("Invalid command: " + command);
            }
        }

        sc.close();
    }
}
```
