
## Functions

Functions are the constructs that allow the user to break down their programs into building blocks. The main characteristic of functions is the fact that, once written and debugged, they can be reused as many times as needed, including by other programs.

```c
return_type function_name(parameters) {
    // Function body
    return value; // This is only required for functions that have a non-void return type.
}
```

> ***return_type:** It specifies the data type of the value that the function will return. If the function doesn't return a value, you should use `void`.*      
> ***parameters:** You can have zero or more parameters. Each parameter consists of a data type and a name.*  
> ***Function body:** This is where you write the actual code that the function will execute when called.*  
> ***return value (optional):** If the function is expected to return a value, you use the `return` statement to specify the value to be returned. *

Note that the type must be specified for each of the N input variables. It's in the parameter declaration that we inform the compiler about the inputs to the function (just as we specify the output in the return type). Each variable described in the parameter declaration will be treated as a local variable of the function. When a function has no input arguments, the parameter list will be empty. However, the parentheses in the function declaration are mandatory.

When a *return* statement is encountered, the function is immediately terminated, and if any data is provided after *return*, its value is returned by the function. It's important to remember that the return value provided must be compatible with the return type declared for the function. A function can have more than one *return* statement; however, only one will be executed per function call. This becomes clear when we consider that the function is terminated when the program reaches the first *return* statement.

Here are two examples of functions in C, one of which uses multiple return statements:

#### Example: A Simple Function
```c
#include <stdio.h>

// Function to calculate the square of a number
int square(int num) {
  int result = num * num;
  return result;
}

int main() {
  int number = 5;
  int squared = square(number);
  printf("The square of %d is %d\n", number, squared);
  return 0;
  }
```

> *In this example, the square function takes an integer as input, calculates its square, and returns the result.*

#### Example: Function with Multiple Return Statements
```c
#include <stdio.h>

// Function to check if a number is positive, negative, or zero
char* checkNumber(int num) {
  if (num > 0) {
      return "Positive";
  } else if (num < 0) {
      return "Negative";
  } else {
      return "Zero";
  }
}

int main() {
  int number = -7;
  char* result = checkNumber(number);
  printf("%d is %s\n", number, result);
  return 0;
}
```

> *In this example, the checkNumber function takes an integer as input, checks whether it's positive, negative, or zero, and returns a corresponding string. This function uses multiple return statements based on different conditions.*

Since functions return values, we can utilize them for assignments and conditional comparisons (as part of an expression) or even in outputting data. However, it's important to emphasize that in an assignment, function calls can only appear on the right-hand side of assignment statements.

#

### VOID TYPE

Instead of returning data, functions with a void return type are often used to perform actions or tasks, such as printing output, modifying variables, or interacting with external devices. To declare a function with a void return type, you simply specify void as the return type in the function signature:

```c
void functionName(parameters) {
    // Function body
    // Code to perform some task
}

```

> ***void:** This indicates that the function doesn't return a value.*  
> ***functionName:** This is the name you give to your function.*  
> ***parameters:** These are the input values that the function can accept. You can have zero or more parameters.*

Here's an example of a simple C function with a void return type that prints a message:

```c
#include <stdio.h>

void printWelcome() {
  printf("Welcome to our program!\n");
}

int main() {
  // Calling the function to print the welcome message
  printWelcome();
  return 0;
}
```

> *In a void function, the use of the return statement is optional and can be omitted.*

### FUNCTION CALL

Once functions are defined, they can be used without worrying about how they were written. This is what we refer to as a function call. A function call is the act of invoking the function in a program. When you call a function, you are requesting it to execute the code contained within its body. Functions are called by their name followed by parentheses, which can contain arguments if the function expects them.

For example, if you have a function called calculateSum that adds two numbers, you can call it like this:

```c
int result = calculateSum(5, 3); 
```

> *The function call above executes the code inside the calculateSum function with the arguments 5 and 3, and the result is assigned to the result variable.*

In general, arguments can be passed to functions in two ways, as follows:

#### Passing Parameters by Value

Passing parameters by value is a method of passing arguments to functions in which a copy of the actual parameter values is passed. This means that the function works with a copy of the original values, and any modifications to the parameters within the function do not affect the original variables outside of the function. This method is commonly used to avoid unintended side effects on the original variables.

Here's an example in C that demonstrates passing parameters by value:

```c
#include <stdio.h>

void swap(int a, int b) {
  int temp = a;
  a = b;
  b = temp;
}

int main() {
  int x = 5;
  int y = 10;
  
  printf("Before swap: x = %d, y = %d\n", x, y);
  
  // Calling the function to swap the values of x and y
  swap(x, y);
  
  printf("After swap: x = %d, y = %d\n", x, y);
  
  return 0;
}
```

> *In this example, even after calling the swap function, the values of x and y in the main function remain the same because the swap function received copies of the values and did not affect the original variables. This illustrates passing parameters by value.*

#

#### Passing Parameters by Reference

This type of function call is called "call by reference." This name comes from the fact that, in this type of call, the values of the variables are not passed to the function but rather their references (memory addresses of the variables). The function uses these references to modify the values of the variables used in the function call.

In this type of call, the formal parameters of a function must be declared as pointers (using the * operator). Pointers are the "references" we need to be able to change the variable outside the function. Additionally, to make these pointers receive the memory address of the variables used in the function call, it is necessary to place the & operator in front of each of the variables, as shown in the example:

> *In C, this is a common way to achieve call by reference, but it's worth noting that some other programming languages may have different mechanisms for call by reference*

Here's an example in C that demonstrates passing parameters by reference using pointers:

```c
#include <stdio.h>

void swap(int *a, int *b) {
  int temp = *a;
  *a = *b;
  *b = temp;
}

int main() {
  int x = 5;
  int y = 10;
  
  printf("Before swap: x = %d, y = %d\n", x, y);
  
  // Calling the function to swap the values of x and y by reference
  swap(&x, &y);
  
  printf("After swap: x = %d, y = %d\n", x, y);
  
  return 0;
}
```

> *In this example, the swap function receives pointers to x and y as arguments, allowing it to directly access and modify the variables x and y in the main function. This demonstrates passing parameters by reference using pointers.*

Note that once the value of the function has been stored in the memory address of nro, no return is necessary. This type of call is the same as used by the scanf() function. This is because this function needs to change the value of the variable passed as a parameter by assigning the new value entered by the user.

#

### RECURSION

Functions in C can call each other to perform a specific task. A special case of function calling occurs when a function calls itself. This process is called "recursion," and the function is referred to as a recursive function.

In a recursive function, the problem is divided into smaller, similar subproblems, and each subproblem is solved by applying the same function recursively. This process continues until a base case is reached, which is a condition that indicates when the recursion should stop. 

**Syntax of Recursive Function:**

```c
return_type recursiveFunction(parameters) {
  // Base case
  if (base_case_condition) {
    // Return a value or perform some action
  } else {
    // Recursive case
    // Call the function with modified arguments
    return recursiveFunction(modified_parameters);
  }
}
```

> ***Base Case:** This is the termination condition that specifies when the recursion should stop. It prevents the function from calling itself infinitely. When the base case is met, the recursion unwinds.*    
> ***Recursive Case:** In this part, the function calls itself with modified arguments, typically smaller or simpler than the original problem.*

Here's a classic example of recursion in C: calculating the factorial of a number.

```c
#include <stdio.h>

int factorial(int n) {
  // Base case: factorial of 0 or 1 is 1
  if (n == 0 || n == 1) {
    return 1;
  } else {
    // Recursive case: n! = n * (n-1)!
    return n * factorial(n - 1);
  }
}

int main() {
  int num = 5;
  int result = factorial(num);
  printf("Factorial of %d is %d\n", num, result);
  return 0;
}
```

> *The base case is when n is 0 or 1, where the factorial is 1. In the recursive case, the function calls itself with n-1 to calculate (n-1)! and multiplies it by n to get n!. The recursion continues until the base case is reached.*

A recursive function almost always consumes more memory and has slower processing than its non-recursive counterpart. This occurs because the memory used in a function call is only released upon its completion, so the computer allocates much more memory when the function is recursive. 

However, recursive code is more compact and sometimes easier to understand. Additionally, there are certain algorithms that are more efficient when implemented recursively. For example, the construction of some types of abstract data structures, such as trees, is inherently recursive in nature, even in their definition.

#

### PARAMETERS TO THE MAIN FUNCTION

In C, the main() function can receive arguments directly from the command line when you run the program from the terminal. These arguments are passed as parameters to the main() function. These parameters allow you to provide information or options to the program when it is started. The parameters *argc* and *argv* provide the programmer with access to the command line of the operating system through which the program was invoked. The declaration of a main() function with these parameters is:

```c
int main(int argc, char *argv[])
```

**argc:** (argument count): It's an integer that represents the total number of arguments passed to the program, including the program's own name.

**argv:** (argument vector): It's an array of strings, where each element is a sequence of characters representing an argument passed to the program. argv[0] contains the name of the program itself, and additional arguments are stored in argv[1], argv[2], and so on.

Here's an example of how these parameters can be used:

```c
#include <stdio.h>

int main(int argc, char *argv[]) {
  printf("Total number of arguments: %d\n", argc);
  
  printf("Program name: %s\n", argv[0]);
  
  for (int i = 1; i < argc; i++) {
    printf("Argument %d: %s\n", i, argv[i]);
  }
  return 0;
}
```

When you run this program from the terminal and provide arguments, it will print them to the screen. For example:

```julia
$ ./my_program arg1 arg2 arg3
Total number of arguments: 4
Program name: ./my_program
Argument 1: arg1
Argument 2: arg2
Argument 3: arg3
```

This is useful for creating programs that can be configured or customized with different options and input data from the command line.