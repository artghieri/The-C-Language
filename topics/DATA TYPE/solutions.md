Exercise 1: Integer Data Types

Create a program that demonstrates the use of various integer data types, including int, short, long, and char.

```c
#include <stdio.h>

int main() {
    int integerVar = 42;
    short shortVar = 32767;
    long longVar = 2147483647;
    char charVar = 'A';

    printf("int: %d\n", integerVar);
    printf("short: %d\n", shortVar);
    printf("long: %ld\n", longVar);
    printf("char: %c\n", charVar);

    return 0;
}
```

Exercise 2: Floating-Point Data Types

Create a program that demonstrates the use of float and double data types to store and perform operations on real numbers.

```c
#include <stdio.h>

int main() {
    float floatVar = 3.14159;
    double doubleVar = 3.14159265359;

    printf("float: %.5f\n", floatVar);
    printf("double: %.10lf\n", doubleVar);

    return 0;
}
```
