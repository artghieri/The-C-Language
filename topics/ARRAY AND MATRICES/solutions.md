Exercise 1: Simple Array
Create a program that defines an integer array and prints its elements.

```c
#include <stdio.h>

int main() {
    int numbers[] = {1, 2, 3, 4, 5};

    printf("Array elements: ");
    for (int i = 0; i < 5; i++) {
        printf("%d ", numbers[i]);
    }

    printf("\n");

    return 0;
}
```

Exercise 2: Matrix Multiplication
Create a program that performs matrix multiplication. Given two matrices, matrix1 and matrix2, the program should multiply them and store the result in the result matrix.

```c
#include <stdio.h>

int main() {
    int matrix1[2][2] = {{1, 2}, {3, 4}};
    int matrix2[2][2] = {{5, 6}, {7, 8}};
    int result[2][2] = {{0, 0}, {0, 0}};

    for (int i = 0; i < 2; i++) {
        for (int j = 0; j < 2; j++) {
            for (int k = 0; k < 2; k++) {
                result[i][j] += matrix1[i][k] * matrix2[k][j];
            }
        }
    }

    printf("Resulting Matrix:\n");
    for (int i = 0; i < 2; i++) {
        for (int j = 0; j < 2; j++) {
            printf("%d ", result[i][j]);
        }
        printf("\n");
    }

    return 0;
}
```

Exercise 3: Finding Maximum Element in an Array
Create a program that finds and prints the maximum element in an integer array.

```c
#include <stdio.h>

int main() {
    int numbers[] = {15, 7, 38, 41, 19, 84, 26};
    int n = sizeof(numbers) / sizeof(numbers[0]);
    int max = numbers[0];

    for (int i = 1; i < n; i++) {
        if (numbers[i] > max) {
            max = numbers[i];
        }
    }

    printf("Maximum element in the array: %d\n", max);

    return 0;
}
```