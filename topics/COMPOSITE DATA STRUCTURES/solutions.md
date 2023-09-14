Exercise 1: Creating and Using Structs
Create a program that defines a struct representing a Student with name and age fields and demonstrates how to use it.

```c
#include <stdio.h>

// Define a struct
struct Student {
    char name[50];
    int age;
};

int main() {
    // Declare and initialize a struct variable
    struct Student student1;
    strcpy(student1.name, "Alice");
    student1.age = 20;

    // Display the student's information
    printf("Student Name: %s\n", student1.name);
    printf("Student Age: %d\n", student1.age);

    return 0;
}
```

Exercise 2: Typedef for Struct
Create a program that uses typedef to define a new type Student for the struct defined earlier and demonstrates how to use it.

```c
#include <stdio.h>

// Define a struct
struct Student {
    char name[50];
    int age;
};

// Create a typedef for the struct
typedef struct Student Student;

int main() {
    // Declare and initialize a struct variable
    Student student1;
    strcpy(student1.name, "Bob");
    student1.age = 22;

    // Display the student's information
    printf("Student Name: %s\n", student1.name);
    printf("Student Age: %d\n", student1.age);

    return 0;
}
```