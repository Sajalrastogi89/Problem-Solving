# Recursive Print Function

## Intuition
The goal of this code is to create a simple recursive function that prints numbers from 1 to `n`.

## Approach
1. Define a method called `recursivePrint` that takes two parameters: `n` (the upper limit) and `m` (the current number).
2. Base case: If `m` exceeds `n`, return.
3. Print the current number `m`.
4. Recursively call `recursivePrint` with `n` and `m + 1`.

## Example
Suppose we run the program with `n = 5`. The output will be:
1 2 3 4 5

## Complexity
- **Time complexity**: O(n), where `n` is the upper limit.
- **Space complexity**: O(1) (since we use only function call stack space).

```java
package Striver.Recursion.Lecture1;

import java.util.Scanner;

public class Recursion1 {
    public static void main(String[] args) {
        int n;
        Scanner sc = new Scanner(System.in);
        n = sc.nextInt();
        Recursion1 obj = new Recursion1();
        obj.recursivePrint(n, 1);
    }

    void recursivePrint(int n, int m) {
        if (m > n)
            return;
        System.out.println(m);
        recursivePrint(n, m + 1);
    }
}

