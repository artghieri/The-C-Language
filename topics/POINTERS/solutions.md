Exercise 1: Pointer Basics
Create a program that demonstrates basic pointer usage by declaring a pointer, assigning it the address of a variable, and using it to access the variable's value.

```c
#include <stdio.h>

int main() {
    int num = 42;
    int *ptr; // Declare a pointer to an integer

    ptr = &num; // Assign the address of 'num' to 'ptr'

    printf("Value of num: %d\n", num);
    printf("Value of num using pointer: %d\n", *ptr);

    return 0;
}
```


Exercise 2: Pointer Arithmetic
Create a program that demonstrates pointer arithmetic by iterating through an array using pointers.

```c
#include <stdio.h>

int main() {
    int numbers[] = {1, 2, 3, 4, 5};
    int *ptr = numbers; // Initialize pointer with the address of the array

    printf("Array elements using pointer arithmetic: ");
    
    for (int i = 0; i < 5; i++) {
        printf("%d ", *ptr);
        ptr++; // Move the pointer to the next element
    }

    printf("\n");

    return 0;
}
```



Exercise: Swapping Two Numbers Using Pointers
Create a program that swaps the values of two integers using pointers.

```c
#include <stdio.h>

// Function to swap two integers using pointers
void swap(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

int main() {
    int num1 = 10, num2 = 20;

    printf("Before swapping: num1 = %d, num2 = %d\n", num1, num2);

    // Call the swap function to swap the values
    swap(&num1, &num2);

    printf("After swapping: num1 = %d, num2 = %d\n", num1, num2);

    return 0;
}
```


Exercise: Dynamic Array Using malloc and free
In C, you can use malloc to allocate memory dynamically and free to release that memory when it's no longer needed. Your task is to create a program that dynamically allocates an integer array, initializes it, and then frees the memory when done.

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int n;
    int *arr;

    printf("Enter the size of the array: ");
    scanf("%d", &n);

    // Dynamically allocate memory for an integer array of size 'n'
    arr = (int *)malloc(n * sizeof(int));

    if (arr == NULL) {
        printf("Memory allocation failed.\n");
        return 1;
    }

    // Initialize the array with values
    for (int i = 0; i < n; i++) {
        arr[i] = i * 2;
    }

    // Print the array elements
    printf("Array elements: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    // Free the dynamically allocated memory
    free(arr);

    return 0;
}
```