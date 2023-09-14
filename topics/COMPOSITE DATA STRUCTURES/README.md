## Composite Data Structures

Composite data structures are data structures that are composed of or built upon simpler data structures or primitive data types. They allow you to organize and store multiple pieces of data in a way that can represent more complex relationships and entities. One common type of composite data structure is the "struct," often accompanied by the "typedef" keyword, which enhances the flexibility and readability of your code.

#

### Structs

A *struct* is a composite data type in programming that groups together variables of different *data types* under a single name. It lets you create a custom data structure to represent a record, object, or entity with various attributes or properties. Each attribute is called a member, and you can define members with different *data types*. Structs are especially useful when you want to model real-world entities in your code.

For instance, you might use a *struct* to define a ***Person*** data type that contains members like *name*, *age*, and *height*, as shown in the previous example. This grouping makes it easier to manage related data and pass it around within your program.

#

#### Struct Statement

In the C language, a record is declared using the reserved keyword "struct." This keyword introduces a list of declarations enclosed in braces. An optional identifier called the "structure tag" can follow the "struct" keyword. This tag provides a name for the record and can be used as a shortcut for declaring the record in other parts of the program.

> *The variables within a record are called the members of the record.*

Here's an example of how you can define and use a struct in C:

```c
#include <stdio.h>
#include <string.h>

// Define a struct called "Person"
struct Person {
  char name[50];
  int age;
  float height;
};

int main(int argc, char *argv[])
{
  // Declare a variable of type "struct Person"
  struct Person person1;
  
  // Assign values to the members of the struct
  strcpy(person1.name, "John");
  person1.age = 30;
  person1.height = 1.75;
  
  // Print the information
  printf("Name: %s\n", person1.name);
  printf("Age: %d\n", person1.age);
  printf("Height: %.2f\n", person1.height);
  
  return 0;
}
```

> *In this example, we define a struct named Person with three members: name (a character array), age (an integer), and height (a float). We then declare a variable person1 of type struct Person and assign values to its members using the dot notation.*

Sometimes, you might need to represent more complex relationships between data elements. This is where nesting one struct inside another comes in handy.

Consider a scenario where you need to work with 2D coordinates and rectangles in a program. You can start by defining a Point struct to represent a point in a 2D space. This struct has two members: x and y, which hold the horizontal and vertical coordinates respectively.

```c
struct Point {
    int x;
    int y;
};
```

Now, let's say you want to define a Rectangle struct that represents a rectangle on a plane. Instead of just storing the width and height, you want to represent the rectangle using its top-left and bottom-right corners, each of which can be represented by a Point. This is achieved by nesting the Point struct within the Rectangle struct.

```c
struct Rectangle {
    struct Point topLeft;    // A Point representing the top-left corner
    struct Point bottomRight; // A Point representing the bottom-right corner
};
```

In the main function, you can create an instance of the Rectangle struct named rect. To assign values to the nested Point structs within rect, you use the dot notation twice: first to access the outer struct member (topLeft or bottomRight), and then to access the inner struct member (x or y).

```c
#include <stdio.h>

int main(int argc, char *argv[])
{
    struct Rectangle rect;

    rect.topLeft.x = 10;
    rect.topLeft.y = 20;
    rect.bottomRight.x = 50;
    rect.bottomRight.y = 30;

    // Printing the information
    printf("Top left point: x = %d, y = %d\n", rect.topLeft.x, rect.topLeft.y);
    printf("Bottom right point: x = %d, y = %d\n", rect.bottomRight.x, rect.bottomRight.y);

    return 0;
}
```

A declaration of a struct without a list of variables only describes the structure's format, but it does not allocate any storage space. If the struct has a name (identifier), this name can be used later in the definition of struct instances, as shown in the example:

```c
struct Person;
```

Normally, the declaration of the structure is done at the beginning of the program (global declaration), while the declaration of variables associated with this type of structure is done within respective functions (local declaration or formal arguments

#

#### Manipulation of Structure Members

A structure member is referenced in an expression using the construct:

```c
struct_variable.member_name
```

The dot operator "." connects the name of the variable of the structure type and the name of the member that will be used in the expression.

```c
rect.topLeft.x = 10;
```

As seen in the last example, referencing members of nested structures is done by sequentially identifying the involved structures from outermost to innermost, all separated by periods. This is followed by the name of the member from the innermost structure that will be used.

#

#### Typedef Command

In programming, the typedef keyword is a powerful tool that allows you to create custom, more descriptive names for existing data types. This serves to enhance code readability, improve maintainability, and provide a level of abstraction when working with complex or lengthy type names.

```c
typedef datatype variable_nickname;
```

> *When you encounter situations where a data type name is long, convoluted, or not intuitive, typedef lets you define an alias for that type.*

Consider this scenario: you're working with a complex data structure, perhaps involving nested structures or function pointers. The names of these types could become quite lengthy and cumbersome. Using typedef, you can assign shorter and more meaningful names to these types, simplifying the code.

Here's a simple example in C:

```c
#include <stdio.h>

// Define a type alias using typedef
typedef int Age;

int main(int argc, char *argv[])
{
    Age personAge = 30;
    printf("The person's age is: %d\n", personAge);
    return 0;
}
```

> *In this example, we've defined a type alias Age using typedef. This alias represents the int data type. By doing this, we can use the name Age instead of int, making our code clearer and more self-explanatory.*

Typedef is especially helpful when working with complex data types, such as function pointers or structures. It allows you to create meaningful names for these types, making your code easier to understand, more maintainable, and less error-prone.