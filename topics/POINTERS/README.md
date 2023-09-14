## Pointers

Whenever we use the `scanf()` function to read an element of an array, we pass the memory address of that element. To do this, as previously discussed, we use the & operator, which returns the memory address allocated for a variable. Therefore, if ***v[i]*** represents the i-th element of the array, ***&v[i]*** represents the memory address where that element is stored.

```c
int v[10];
```

The variable ***v***, which represents the array, is a constant that represents its initial address. In other words, ***v*** without indexing points to the first element of the array. Therefore, the C language supports pointer arithmetic, which means you can add and subtract pointers as long as the resulting value points to the area reserved for the array.

If ***p*** represents a pointer to an integer, ***p+1*** represents a pointer to the next integer stored in memory. This increment is equivalent to adding **2 bytes** - *the size of an int* - to the memory address stored in the pointer ***p***. With this, in an array, we have the following equivalences:

```julia
v+0 points to the 1st element of the array.
v+1 points to the 2nd element of the array.
v+2 points to the 3rd element of the array.
...
v+N points to the (N+1)-th element of the array.
```

Therefore, writing ***&v[i]*** is equivalent to writing ***(v + i)***. Similarly, writing ***v[i]*** is equivalent to writing ***\*(v + i)***. This is because the `*` operator returns the value stored at the memory location indicated by ***(v + i)***.

In C, the declaration of a pointer is done using the following syntax:

```c
data_type *variable_name[size]...[sizeN]
```

Here's an example that demonstrates the use of arrays and pointers in C:

```c
#include <stdio.h>

int main() {
int numbers[] = {1, 2, 3, 4, 5};
int *ptr = numbers; // Assign the address of the first element to ptr
int sum = 0;

for (int i = 0; i < 5; i++) {
  sum += *ptr; // Access the value using the pointer
  ptr++;       // Move the pointer to the next element
}

printf("Sum of elements: %d\n", sum);

return 0;
}
```

> *We assign the address of the first element of the numbers array to ptr. Then, we use a loop to iterate through the array using the pointer ptr to access each element's value. The pointer is incremented to move to the next element in each iteration.*

#

### How Pointers Actually Work

The `int` type stores integers. The `float` type stores floating-point numbers. The `char` type stores characters. On the other hand, pointers store memory addresses. Think of a pointer as a note where you've written down a friend's address. The pointer is like that piece of paper where you've recorded an address. **What's the purpose of this? It's simple: when you write down a friend's address, you do it so that you can find them later. C works in a similar way. You record the address of something in a pointer variable so that you can use it later.**

Just like an address book where you store the addresses of several friends can be seen as an array of pointers in C.

**It's important to mention that pointers also have a type. For example, when you note down a friend's address, you treat that address differently from how you would when noting down the address of a company. Although both addresses have the same format (street, number, neighborhood, city, etc.), they refer to places with different contents. Therefore, these two addresses are pointers of different types.**

**In C, when we declare pointers, we're informing the compiler about the type of variable we are pointing to. An `int` pointer points to an integer, meaning it stores the address of a variable of type integer.**

#

#### Declaring and Using Pointers

To declare a pointer, we have the following general form:

```julia
pointer_type *variable_name;
```

It's the asterisk (*) operator that tells the compiler that the variable will not store a value but rather an address for that specified type. Let's see examples of declarations:

```c
int *pt;
```

> *This example declares a pointer to an integer. It hasn't been initialized yet (as is the case with any C variable that is only declared).*

When a pointer is not initialized at the moment it is declared, it means that it points to an undefined location. This location could be, for example, in the portion of memory reserved for the computer's operating system. Using the pointer in these circumstances can lead to a system crash or even worse consequences.

> *The pointer must be initialized (pointed to a known location) before use! This is of utmost importance!*

To assign a value to a newly created pointer, we could set it equal to a memory address. But how do we know the memory location of a variable in our program? It would be very difficult to determine the address of every variable we use, especially since these addresses are determined by the compiler at compile-time and may be relocated at runtime. We can let the compiler do this work for us. To find the address of a variable, simply use the `&` operator. See the example:

```c
int count, int *pointer;

count = 10;
pointer = &count;
```

> *We create an integer count with the value 10 and a pointer to an integer pointer. The expression &count gives us the memory address of count, which is stored in pointer. Note that we haven't changed the value of count, which still remains 10.*

Now that we have placed an address in pointer, it is now "ready" to be used. For example, we can change the value of count using pointer. To do this, we use the "inverse" operator of the & operator, which is the * operator. In the example above, since we set pointer to &count, the expression *pointer is equivalent to count itself. This means that if we want to change the value of count to 12, we simply do `*pointer = 12`.

Here are two examples of pointers in C:

#### Example: Pointer to an Integer
```c
#include <stdio.h>

int main() {
int num = 10;       // Declare an integer variable
int *ptr = &num;    // Declare a pointer to an integer and assign the address of num to it

printf("Value of num: %d\n", num);      // Print the value of num
printf("Address of num: %p\n", &num);   // Print the address of num
printf("Value using pointer: %d\n", *ptr); // Access the value of num using the pointer

return 0;
}
```

> *In the first example, we declare an integer variable num, initialize it with the value 10, create a pointer ptr that stores the address of num, and demonstrate how to access and print the value of num using the pointer. In*

#

#### Example: Pointer to an Integer
```c
#include <stdio.h>

int main() {
char letter = 'A';    // Declare a character variable
char *ptr = &letter;  // Declare a pointer to a character and assign the address of letter to it

printf("Value of letter: %c\n", letter);       // Print the value of letter
printf("Address of letter: %p\n", &letter);    // Print the address of letter
printf("Value using pointer: %c\n", *ptr);     // Access the value of letter using the pointer

return 0;
}
```

> *In the second example, we declare a character variable letter, assign it the character 'A', create a pointer ptr that points to the address of letter, and show how to access and print the value of letter using the pointer. *

We can do some arithmetic operations with pointers. The first and simplest one is to assign two pointers. If we have two pointers *p1* and *p2*, we can make them equal by doing `p1 = p2`. 

```c
int *p1, *p2;

p1 = p2;
```

Notice that we are making *p1* point to the same location as *p2*. If we want the variable pointed to by *p1* to have the same content as the variable pointed to by *p2*, we should do `*p1 = *p2`.

```c
int *p1, *p2;

*p2 = 10;
*p1 = *p2;
```

The next operations, also commonly used, are increment and decrement. When we increment a pointer, it starts pointing to the next value of the same type to which the pointer points. That is, if we have a pointer to an integer and increment it, it will point to the next integer.

```c
p++;
p--;
```

Reminder. We are discussing operations with pointers and not operations with the contents of the variables they point to. For example, to increment the content of the variable pointed to by the pointer p, you do:

```c
(*p)++; 
```

Other useful arithmetic operations involve adding and subtracting integers with pointers. Suppose you want to increment a pointer by 15. You can simply do:

```c
p = p + 15; // or p += 15;
```

And if you want to access the content of the pointer 15 positions ahead:

```c
*(p + 15);

*(p - 15);
```

These operations allow for easy navigation through memory locations when working with pointers.

#

### Initializing of Pointers

In C programming, initializing pointers is a fundamental concept that involves assigning a memory address to a pointer variable. Proper initialization ensures that the pointer points to a valid location in memory. Pointers can be initialized in various ways, depending on the specific use case.

#### Syntax:

```c
data_type *pointer_name = &variable_name;
```

- **data_type** is the type of data that the pointer will point to (e.g., int, float, char).
- **pointer_name** is the name of the pointer variable.
- **&variable_name** is the address of the variable that the pointer will point to.

Here's an example of how to initialize a pointer in C:

```c
#include <stdio.h>

int main() {
  int num = 42; // Declare an integer variable and initialize it to 42
  int *ptr;     // Declare an integer pointer
  
  ptr = &num;   // Initialize the pointer to the address of 'num'
  
  printf("Value of num: %d\n", num);
  printf("Address of num: %p\n", &num);
  printf("Value pointed to by ptr: %d\n", *ptr);
  printf("Address stored in ptr: %p\n", ptr);
  
  return 0;
}
```

> *In this example, we declare an integer variable num, an integer pointer ptr, and initialize ptr with the address of num. We then print the value of num, the address of num, the value pointed to by ptr, and the address stored in ptr.*

#

### Pointer to a Pointer

A pointer to a pointer, often referred to as a double pointer, is a variable that stores the address of another pointer. This concept is commonly used in scenarios where you need to manipulate or pass pointers to functions by reference. Initializing a pointer to a pointer involves assigning the address of a pointer variable to another pointer variable.

#### Syntax:

```c
data_type **pointer_to_pointer = &pointer_variable;
```

- **data_type** is the type of data that the pointer to a pointer will point to (e.g., int, float, char).
- **pointer_to_pointer** is the name of the pointer to a pointer variable.
- **pointer_variable** is the pointer whose address you want to store in the pointer to a pointer.

Here's an example of how to initialize a pointer to a pointer in C:

```c
#include <stdio.h>

int main() {
  int num = 42;      // Declare an integer variable and initialize it to 42
  int *ptr = &num;   // Declare an integer pointer and initialize it with the address of 'num'
  int **ptr_to_ptr;  // Declare a pointer to a pointer
  
  ptr_to_ptr = &ptr; // Initialize the pointer to a pointer with the address of 'ptr'
  
  printf("Value of num: %d\n", num);
  printf("Value pointed to by ptr: %d\n", *ptr);
  printf("Value pointed to by ptr_to_ptr: %d\n", **ptr_to_ptr);
  
  return 0;
}
```

> *In this example, we have an integer variable num, an integer pointer ptr, and a pointer to a pointer ptr_to_ptr. We initialize ptr with the address of num, and then ptr_to_ptr is initialized with the address of ptr. We demonstrate accessing the value of num through all three levels: directly, through ptr, and through ptr_to_ptr.*

#

### Dinamic Allocation

Dynamic allocation allows the programmer to allocate memory for variables while the program is running. This enables defining, for example, an array or a matrix whose size is determined at runtime.

There are many other functions that are widely used but dependent on the environment and compiler. However, the ANSI C standard defines only four functions for dynamic memory allocation, available in the stdlib.h header file, and they are described as follows.

#### MALLOC 

Malloc stands for "memory allocation." It's a crucial function used for dynamic memory allocation, allowing you to request a specific amount of memory during program execution. This memory is allocated on the heap, which is a region of a computer's memory used for dynamic memory storage. malloc is particularly useful when you need to create data structures like arrays or linked lists of varying sizes.

```c
void* malloc(size_t size);
```

> *The function returns a pointer to the first byte of the allocated memory block if successful, or NULL if it fails to allocate the requested memory.*

Here's an example of how to use malloc to allocate memory for an integer array dynamically:

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
  int *arr; // Declare a pointer to int
  int size = 5; // Size of the array
  
  // Dynamically allocate memory for the array
  arr = (int*)malloc(size * sizeof(int));
  
  // Check if memory allocation was successful
  if (arr == NULL) {
    printf("Memory allocation failed!\n");
    return 1; // Exit with an error code
  }
  
  // Initialize the array
  for (int i = 0; i < size; i++) {
    arr[i] = i * 2;
  }
  
  // Print the values in the array
  for (int i = 0; i < size; i++) {
    printf("arr[%d] = %d\n", i, arr[i]);
  }
  
  // Don't forget to free the allocated memory when done
  free(arr);
  
  return 0;
}
```

> *In this example, we allocate memory for an integer array of size 5 using malloc. We then populate and print the array before releasing the allocated memory with free.*

#

#### CALLOC

Calloc stands for "contiguous allocation." It's another function used for dynamic memory allocation, similar to malloc. However, calloc not only allocates memory but also initializes it to zero, making it suitable for creating arrays and structures where you want all elements to start with a known value, such as zero.

```c
void* calloc(size_t num_elements, size_t element_size);
```

- **num_elements** specifies the number of elements to allocate memory for.  
- **element_size** specifies the size (in bytes) of each element.

> *The function returns a pointer to the first byte of the allocated memory block if successful, or NULL if it fails to allocate the requested memory.*

Here's an example of how to use *calloc* to allocate memory for an integer array and initialize it with zeros:

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
  int *arr; // Declare a pointer to int
  int size = 5; // Size of the array
  
  // Dynamically allocate memory for the array and initialize with zeros
  arr = (int*)calloc(size, sizeof(int));
  
  // Check if memory allocation was successful
  if (arr == NULL) {
    printf("Memory allocation failed!\n");
    return 1; // Exit with an error code
  }
  
  // Print the values in the array (should all be 0)
  for (int i = 0; i < size; i++) {
    printf("arr[%d] = %d\n", i, arr[i]);
  }
  
  // Don't forget to free the allocated memory when done
  free(arr);
  
  return 0;
}
```

> *In this example, we allocate memory for an integer array of size 5 using calloc. Since calloc initializes the memory to zero, all elements of the array will initially contain zeros. Finally, we release the allocated memory with free.*

#

#### REALLOC

Realloc stands for "reallocate." It is used for dynamic memory reallocation, which means changing the size of a previously allocated memory block. This is particularly useful when you have dynamically allocated memory, and you need to adjust its size based on changing requirements.

```c
void* realloc(void* ptr, size_t size);
```

- **ptr** is a pointer to a previously allocated memory block (e.g., the result of a previous malloc, calloc, or realloc call).  
- **size** is the new size (in bytes) you want to allocate for the memory block.

> *The function returns a pointer to the first byte of the newly allocated memory block if successful. If reallocation fails, it returns NULL, and the original block remains unchanged.*

This happens because `realloc()` may need to move the originally allocated block to *increase its size*, which means changing the ***memory address of the allocated bytes***. If this happens, the content of the old block is copied to the new block, and no information is lost. If *ptr* is **NULL**, it allocates num bytes and returns a *pointer*. If *size* is zero, the memory pointed to by ptr is freed. If there is not enough memory for reallocation, a *null pointer* is returned, and the original block remains unchanged.

Here's an example of how to use realloc to resize a dynamically allocated integer array:

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
  int *arr; // Declare a pointer to int
  int size = 5; // Initial size of the array
  
  // Dynamically allocate memory for the initial array
  arr = (int*)malloc(size * sizeof(int));
  
  // Check if memory allocation was successful
  if (arr == NULL) {
      printf("Memory allocation failed!\n");
      return 1; // Exit with an error code
  }
  
  // Initialize the array
  for (int i = 0; i < size; i++) {
      arr[i] = i * 2;
  }
  
  // Print the values in the initial array
  printf("Initial array:\n");
  for (int i = 0; i < size; i++) {
      printf("arr[%d] = %d\n", i, arr[i]);
  }
  
  // Resize the array to a new size
  int new_size = 8;
  arr = (int*)realloc(arr, new_size * sizeof(int));
  
  // Check if reallocation was successful
  if (arr == NULL) {
      printf("Memory reallocation failed!\n");
      return 1; // Exit with an error code
  }
  
  // Initialize the additional elements
  for (int i = size; i < new_size; i++) {
      arr[i] = i * 3;
  }
  
  // Print the values in the resized array
  printf("\nResized array:\n");
  for (int i = 0; i < new_size; i++) {
      printf("arr[%d] = %d\n", i, arr[i]);
  }
  
  // Don't forget to free the allocated memory when done
  free(arr);
  
  return 0;
}
```

> *In this example, we start by allocating memory for an integer array of size 5 using malloc. Later, we use realloc to resize the array to a new size of 8. The additional elements are initialized, and the values are printed. Finally, we free the dynamically allocated memory.*

#

### FREE

The *free* function is used to deallocate memory that was previously allocated using functions like *malloc, calloc, or realloc*. It is an essential step in managing dynamic memory allocation and preventing memory leaks.

```c
void free(void* ptr);
```

- **ptr** is a pointer to the memory block that you want to deallocate.

> *The function doesn't return any value; it simply releases the memory.*

Through this pointer, the program searches an "internal allocation table" for the number of bytes that need to be released.

Here's an example of how to use free to deallocate dynamically allocated memory:

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
  int *arr; // Declare a pointer to int
  int size = 5; // Size of the array
  
  // Dynamically allocate memory for the array
  arr = (int*)malloc(size * sizeof(int));
  
  // Check if memory allocation was successful
  if (arr == NULL) {
    printf("Memory allocation failed!\n");
    return 1; // Exit with an error code
  }
  
  // Initialize the array
  for (int i = 0; i < size; i++) {
    arr[i] = i * 2;
  }
  
  // Print the values in the array
  printf("Array contents:\n");
  for (int i = 0; i < size; i++) {
    printf("arr[%d] = %d\n", i, arr[i]);
  }
  
  // Deallocate the dynamically allocated memory
  free(arr);
  
  return 0;
}
```

> *In this example, we allocate memory for an integer array using malloc, initialize the array, print its values, and then deallocate the memory using free. This step is crucial to prevent memory leaks and efficiently manage memory resources.*


> [!IMPORTANT]
> **Please note that you should always free dynamically allocated memory when you are done using it to avoid memory leaks.**
