Exercise 1: Break Statement
Create a program that uses a for loop to find the sum of numbers entered by the user until the user enters a negative number. Use the break statement to exit the loop.

```c
#include <stdio.h>

int main() {
    int num, sum = 0;

    for (;;) {
        printf("Enter a number (or a negative number to exit): ");
        scanf("%d", &num);

        if (num < 0) {
            break;
        }

        sum += num;
    }

    printf("Sum of numbers = %d\n", sum);

    return 0;
}
```

Exercise 2: Continue Statement
Create a program that uses a for loop to print even numbers between 1 and 10, skipping odd numbers using the continue statement.

```c
#include <stdio.h>

int main() {
    printf("Even numbers between 1 and 10:\n");

    for (int i = 1; i <= 10; i++) {
        if (i % 2 != 0) {
            continue;
        }
        printf("%d ", i);
    }

    printf("\n");

    return 0;
}
```

Exercise 3: Goto Statement
Create a program that uses the goto statement to jump to a specific label when an error condition is encountered.

```c
#include <stdio.h>

int main() {
    int number;

    printf("Enter a positive integer: ");
    scanf("%d", &number);

    if (number <= 0) {
        printf("Invalid input. Please enter a positive integer.\n");
        goto end;
    }

    printf("You entered: %d\n", number);

end:
    return 0;
}
```