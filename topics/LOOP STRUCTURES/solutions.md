Exercise 1: While Loop
Create a program that uses a while loop to count from 1 to 5 and display the numbers.

```c
#include <stdio.h>

int main() {
    int count = 1;

    printf("Counting from 1 to 5 using a while loop:\n");

    while (count <= 5) {
        printf("%d ", count);
        count++;
    }

    printf("\n");

    return 0;
}
```

Exercise 2: For Loop
Create a program that uses a for loop to calculate the factorial of a number entered by the user.

```c
#include <stdio.h>

int main() {
    int n;
    long long factorial = 1;

    printf("Enter a positive integer: ");
    scanf("%d", &n);

    // Calculate factorial using a for loop
    for (int i = 1; i <= n; i++) {
        factorial *= i;
    }

    printf("Factorial of %d = %lld\n", n, factorial);

    return 0;
}
```

Exercise 3: Do-While Loop
Create a program that uses a do-while loop to find the sum of positive numbers entered by the user until a negative number is encountered.

```c
#include <stdio.h>

int main() {
    int num, sum = 0;

    do {
        printf("Enter a positive number (or a negative number to exit): ");
        scanf("%d", &num);

        if (num > 0) {
            sum += num;
        }
    } while (num >= 0);

    printf("Sum of positive numbers = %d\n", sum);

    return 0;
}
```