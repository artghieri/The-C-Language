## Variables

Variables hold and point to a value. They act as a *reference* or *abstraction* to literal data. That data is stored in the computer's memory, and takes up an certain amount of space, so we can retrieve it later and use when we need to.

In the simplest terms, you can think of variables as a **named box**. A box that acts as a *storage place* and *location* for holding different information. 

Each box has a **unique name** which acts like a label put on the outside that is a unique identifier, and the information/content lives on the inside. The content is the variable's value.

#### Example: Adding Two Numbers

```c
#include <stdio.h>

int main(int argc, char *argv[])
{
  int a, b, sum;           // Declaring three scope interger variables

  a = 10;                  // Assignment inline of variable a
  b = 5;                   // Assignment inline of variable b

  sum = a + b;             // Assignment to sum variable the result between the sum of a and b
  return 0;
}
```
> *In this example was declared three integer data type variables - a, b and sum - which were used to store three values*

#

### Declaration and Initialization of Variables

The C programming language is a ***strongly statically typed*** language, unlike many other modern programming languages. In ***statically typed*** languages, you need to explicitly declare your variables to be of a certain *data type*. That way the compiler knows during compilation time if the variable is able to perform the actions it was set out and requested to do.

The purpose of specifying the variable type to our compiler (virtual machine) for code interpretation is due to the fact that in C, we are working directly with the allocation of a physical memory space present in the machine in question.

Thus, by indicating the variable *data type* we will work with, our machine will allocate a space of a specific size so that this variable - *access key* - can have a value *assigned* to it.

> [!NOTE]
> *Use the `=` or assignment operator to assign a value to a variable.*

#

### Declaring a Variable

When declaring a new variable in the C language, it's necessary to specify to the compiler what type of data will be assigned to that variable - access key. This way, when compiled in the future (program), the compiler will know what type of information is stored in that particular variable.

```c
#include <stdio.h>

int main(int argc, char *argv[])
{
  int age;     // int is the data type and age is the unique acess key to this variable

  int n1, n2   // We can also declare multiple variables at once.
  return 0;
}
```

> *To declare a variable, you specify the **data type**, and give a **name** - **acess key** - to the variable.*

#### So, what is the difference between initialising and declaring a variable?

#

### Initializing a Variable

When we declare a variable, we are simply defining its *data type* and a *unique access key* for that variable, as shown in the previous example.

We don't need to specify or assign a value immediately to all the variables we declare in our program. By merely declaring a variable, a memory space on our machine has already been reserved for that *access key*.

#### If we declare a variable and assign it a value at once, this is called initialising the variable.

```c
#include<stdio.h>

int main(int argc, char *argv[])
{
  int age = 30; // int n = 30; is initializing the variable. It refers to assigning an initial value.
  return 0;
}
```

```c
int age = 30;   // initializing the variable with the value of 30

age = 34;      //  the new value of age is 34
```

> [!IMPORTANT]
> **If the new value is the same data type, we don't need to include the data type, just the new value. If the data type is different, we will get an error.**

#

<br>

| BEST PRACTICES FOR NAMING VARIABLES IN C. | 
| --- | 
| Names with leading and trailing underscores are reserved for system purposes and should not be used for any user-created names. If you must have your own private identifiers, begin them with a letter or two identifying the package to which they belong. |
| #define constants should be in all CAPS. |
| Enum constants are Capitalized or in all CAPS |
| Function, typedef, and variable names, as well as struct, union, and enum tag names should be in lower case. |
| Many macro "functions" are in all CAPS. Some macros (such as getchar and putchar) are in lower case since they may also exist as functions. |
| Avoid names that differ only in case, like foo and Foo. Similarly, avoid foobar and foo_bar. The potential for confusion is considerable. |
| Similarly, avoid names that look like each other. On many terminals and printers, 'l', '1' and 'I' look quite similar. A variable named 'l' is particularly bad because it looks so much like the constant '1'. |
| In general, global names (including enums) should have a common prefix identifying the module that they belong with. Globals may alternatively be grouped in a global structure. Typedeffed names often have "_t" appended to their name. |
| Avoid names that might conflict with various standard library names. Some systems will include more library code than you want. Also, your program may be extended someday. |