Exercise 1: Basic Input and Output
Create a program that takes user input for their name and age and displays a greeting message.

```c
#include <stdio.h>

int main() {
    char name[50];
    int age;

    printf("Enter your name: ");
    scanf("%s", name);
    
    printf("Enter your age: ");
    scanf("%d", &age);

    printf("Hello, %s! You are %d years old.\n", name, age);

    return 0;
}
```


Exercise 2: Formatted Input and Output
C provides formatting options for input and output. Your task is to Create a program that reads two floating-point numbers from the user and displays their sum and difference with specific formatting.

```c
#include <stdio.h>

int main() {
    double num1, num2;

    printf("Enter two numbers separated by a space: ");
    scanf("%lf %lf", &num1, &num2);

    printf("Sum: %.2lf\n", num1 + num2);
    printf("Difference: %.2lf\n", num1 - num2);

    return 0;
}
```
