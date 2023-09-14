Exercise 1: Arithmetic Operators

Create a program that demonstrates the use of arithmetic operators (+, -, *, /, %) with two integer operands.

```c
#include <stdio.h>

int main() {
    int a = 10;
    int b = 3;

    printf("a + b = %d\n", a + b);
    printf("a - b = %d\n", a - b);
    printf("a * b = %d\n", a * b);
    printf("a / b = %d\n", a / b);
    printf("a %% b = %d\n", a % b);

    return 0;
}
```


Exercise 2: Assignment Operators

Create a program that demonstrates the use of various assignment operators (=, +=, -=) to modify variable values.

```c
#include <stdio.h>

int main() {
	int a = 10;
	int b = 5;

	a += 3;
	b -= 2;

	printf("a = %d\n", a);
	printf("b = %d\n", b);

	return 0;
}
```

Exercise 3: Increment and Decrement Operators

Increment (++) and decrement (--) operators are used to increase or decrease the value of a variable by 1. Create a program that demonstrates the use of both pre-increment and post-increment operators.

```c
#include <stdio.h>

int main() {
    int x = 5;
    int y;

    y = ++x; // Pre-increment: Increment x first, then assign to y
    printf("x = %d, y = %d\n", x, y);

    x = 5; // Reset x
    y = x++; // Post-increment: Assign x to y first, then increment x
    printf("x = %d, y = %d\n", x, y);

    return 0;
}
```

Exercise 4: Ternary Operator

The ternary operator (condition ? expr1 : expr2) allows you to conditionally choose between two expressions. Create a program that uses the ternary operator to determine whether a number is even or odd.

```c
#include <stdio.h>

int main() {
    int num = 7;
    printf("The number %d is %s.\n", num, (num % 2 == 0) ? "even" : "odd");

    return 0;
}
```

Exercise 5: Casting

Casting allows you to convert one data type to another explicitly. Create a program that demonstrates the use of casting to convert a floating-point number to an integer.

```c
#include <stdio.h>

int main() {
    double pi = 3.14159265359;
    int piInt = (int)pi; // Casting from double to int

    printf("pi as double: %lf\n", pi);
    printf("pi as int (after casting): %d\n", piInt);

    return 0;
}
```