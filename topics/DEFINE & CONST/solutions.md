Exercise 1: Using #define for Constants

In C, you can define constants using the #define preprocessor directive. These constants are replaced with their values during preprocessing. Create a program that calculates the area of a circle using a #define constant for π (pi).

```c
#include <stdio.h>

#define PI 3.14159265

int main() {
    double radius = 5.0;
    double area = PI * radius * radius;
    printf("Area of the circle: %lf\n", area);
    return 0;
}
```

Exercise 2: Using const for Constants

In C, you can declare constants using the const keyword. Unlike #define, const variables are stored in memory, and their values cannot be changed. Write a program that calculates the area of a circle using a const variable for π (pi).

```c
#include <stdio.h>

const double PI = 3.14159265;

int main() {
    double radius = 5.0;
    double area = PI * radius * radius;
    printf("Area of the circle: %lf\n", area);
    // PI = 3.14; // This line would result in a compilation error
    return 0;
}
```

Exercise 3: Using #define for Macros

#define can be used to create macros in C, which are code substitutions. Macros are processed during preprocessing and can take arguments. Create a program that defines and uses a macro to calculate the square of a number.

```c
#include <stdio.h>

#define SQUARE(x) (x * x)

int main() {
    int num = 5;
    int square = SQUARE(num);
    printf("Square of %d: %d\n", num, square);
    return 0;
}
```