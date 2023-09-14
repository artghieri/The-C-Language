Exercise 1: Basic FunctionC
Create a program that defines a simple function to calculate the square of a number and demonstrates how to use it.

```c
#include <stdio.h>

// Function to calculate the square of a number
int square(int num) {
    return num * num;
}

int main() {
    int number;

    printf("Enter an integer: ");
    scanf("%d", &number);

    int result = square(number);

    printf("Square of %d is %d\n", number, result);

    return 0;
}
```

Exercise 2: Function with Parameters and Return Value
Functions can take parameters and return values. Create a program that defines a function to find the maximum of two numbers and demonstrates its use.

```c
#include <stdio.h>

// Function to find the maximum of two numbers
int max(int a, int b) {
    if (a > b) {
        return a;
    } else {
        return b;
    }
}

int main() {
    int num1, num2;

    printf("Enter two integers separated by a space: ");
    scanf("%d %d", &num1, &num2);

    int maximum = max(num1, num2);

    printf("Maximum: %d\n", maximum);

    return 0;
}
```

Exercise: Fibonacci Sequence Using Recursion
The Fibonacci sequence is a series of numbers where each number is the sum of the two preceding ones, usually starting with 0 and 1. Create a program that calculates the nth Fibonacci number using a recursive function.

```c
#include <stdio.h>

// Recursive function to calculate the nth Fibonacci number
int fibonacci(int n) {
    if (n <= 0) {
        return 0;
    } else if (n == 1) {
        return 1;
    } else {
        return fibonacci(n - 1) + fibonacci(n - 2);
    }
}

int main() {
    int n;

    printf("Enter a positive integer n: ");
    scanf("%d", &n);

    if (n < 0) {
        printf("Fibonacci sequence is not defined for negative numbers.\n");
    } else {
        int result = fibonacci(n);
        printf("Fibonacci(%d) = %d\n", n, result);
    }

    return 0;
}
```
