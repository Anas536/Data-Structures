## Aim:


You are tasked with helping a UI design team create symmetric loading patterns for an educational visualization platform. One of the patterns requires generating two mirrored right-angled triangles of asterisks 

Write a recursive Java program that prints the pattern based on the input number n.
Input Format:

    A single integer n (1 ≤ n ≤ 20)

Output Format:

    A pattern of two mirrored decreasing triangles of *, with double spaces between the sets.

    Each * should be followed by a space (i.e., "* "), including the last in a row.

    The gap between the triangles should increase by 2 spaces per line, beginning with 1 space after the first row.


## Program


```
import java.util.Scanner;

public class Main {

    static void printAsterisk(int count) {
        if (count == 0) return;
        System.out.print("* ");
        printAsterisk(count - 1);
    }

    static void printSpaces(int count) {
        if (count == 0) return;
        System.out.print("  "); // double space
        printSpaces(count - 1);
    }

    static void printPattern(int n, int original) {
        if (n == 0) return;

        printAsterisk(n);

        int gap = (original - n) * 2 + 1;
        printSpaces(gap);

        printAsterisk(n);

        System.out.println();

        printPattern(n - 1, original);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        printPattern(n, n);
        sc.close();
    }
}


```
