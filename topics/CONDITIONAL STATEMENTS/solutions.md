Exercise 1: If-Else Statement
Create a program that checks if a number is positive, negative, or zero using an if-else statement.

```c
#include <stdio.h>

int main() {
    int number;

    printf("Enter an integer: ");
    scanf("%d", &number);

    if (number > 0) {
        printf("The number is positive.\n");
    } else if (number < 0) {
        printf("The number is negative.\n");
    } else {
        printf("The number is zero.\n");
    }

    return 0;
}
```

Exercise 2: Switch Statement
The switch statement in C is used to select one of many code blocks to be executed. Create a program that takes a number representing a day of the week (1-7) and displays the corresponding day name.

```c
#include <stdio.h>

int main() {
    int day;

    printf("Enter a number (1-7) representing a day of the week: ");
    scanf("%d", &day);

    switch (day) {
        case 1:
            printf("Sunday\n");
            break;
        case 2:
            printf("Monday\n");
            break;
        case 3:
            printf("Tuesday\n");
            break;
        case 4:
            printf("Wednesday\n");
            break;
        case 5:
            printf("Thursday\n");
            break;
        case 6:
            printf("Friday\n");
            break;
        case 7:
            printf("Saturday\n");
            break;
        default:
            printf("Invalid input\n");
    }

    return 0;
}
```

Exercise 3: Nested If-Else Statements
Create a program that determines if a given year is a leap year or not. Leap years are divisible by 4 but not by 100 unless they are also divisible by 400.

```c
#include <stdio.h>

int main() {
    int year;

    printf("Enter a year: ");
    scanf("%d", &year);

    if ((year % 4 == 0 && year % 100 != 0) || (year % 400 == 0)) {
        printf("%d is a leap year.\n", year);
    } else {
        printf("%d is not a leap year.\n", year);
    }

    return 0;
}
```