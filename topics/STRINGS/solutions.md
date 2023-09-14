Exercise 1: String Input and Output
Create a program that reads a string from the user and displays it.

```c
#include <stdio.h>

int main() {
    char str[100];

    printf("Enter a string: ");
    fgets(str, sizeof(str), stdin);

    printf("You entered: %s", str);

    return 0;
}
```


Exercise 2: String Length
You can find the length of a C string using the strlen function from the <string.h> library. Create a program that calculates and prints the length of a string entered by the user.


```c
#include <stdio.h>
#include <string.h>

int main() {
    char str[100];

    printf("Enter a string: ");
    fgets(str, sizeof(str), stdin);

    str[strlen(str) - 1] = '\0'; // Remove the newline character

    int length = strlen(str);

    printf("Length of the string: %d\n", length);

    return 0;
}
```

Exercise 3: String Concatenation
You can concatenate two strings in C using the strcat function from the <string.h> library. Create a program that takes two strings as input and concatenates them.

```c
#include <stdio.h>
#include <string.h>

int main() {
    char str1[100], str2[100];

    printf("Enter the first string: ");
    fgets(str1, sizeof(str1), stdin);

    printf("Enter the second string: ");
    fgets(str2, sizeof(str2), stdin);

    str1[strlen(str1) - 1] = '\0'; // Remove the newline character
    str2[strlen(str2) - 1] = '\0'; // Remove the newline character

    strcat(str1, str2);

    printf("Concatenated string: %s\n", str1);

    return 0;
}
```