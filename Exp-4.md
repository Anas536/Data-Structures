## Aim:

Sort the elements of a stack in ascending order.

Write a Java program to sort the elements of a given stack in ascending order.

## Program:

```
import java.util.Scanner;
import java.util.Arrays;


public class Stack {
  private int[] arr;
  private int top;

  // Constructor
  public Stack(int size) {
    arr = new int[size];
    top = -1;
  }

  // Push element to stack
  public void push(int num) {
    if (top == arr.length - 1) {
      System.out.println("Stack is full");
    } else {
      arr[++top] = num;
    }
  }

  // Pop element from stack
  public int pop() {
    if (top == -1) {
      System.out.println("Stack Underflow");
      return -1;
    } else {
      return arr[top--];
    }
  }

  // Peek top element
  public int peek() {
    if (top == -1) {
      System.out.println("Stack is empty");
      return -1;
    } else {
      return arr[top];
    }
  }

  // Check if stack is empty
  public boolean isEmpty() {
    return top == -1;
  }

  // Sort so smallest is on top
  public void sort() {
    Arrays.sort(arr, 0, top+1);
  }
  
  public void display(){
      if(isEmpty()){
          System.out.println("Stack is empty");
          return;
      }
      
      for(int i=0;i<=top;i++){
          System.out.print(arr[i] + " ");
      }
  }

  // Main method
  public static void main(String[] args) {
    Scanner scanner = new Scanner(System.in);

    String[] input = scanner.nextLine().trim().split("\\s+");
    int size = input.length;

    Stack stack = new Stack(size);

    for (String s : input) {
      stack.push(Integer.parseInt(s));
    }


    stack.sort();

    stack.display();

    scanner.close();
  }
}

```
