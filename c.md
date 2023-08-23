## Introduction

To master C is not just about learning a language; it's about gaining a profound understanding of programming principles. C strikes a balance between abstraction and hardware control, enabling you to craft effective programs and transfer knowledge to other languages.

In this guide, we will delve deep into the key topics encompassing the C language, starting with the most basic concepts and progressing to more advanced subjects. You will learn to write functional code, grasp memory management, and explore the construction of efficient data structures and algorithms.

---

## Variables

Variables hold and point to a value. They act as a *reference* or *abstraction* to literal data. That data is stored in the computer's memory, and takes up an certain amount of space, so we can retrieve it later and use when we need to.

In the simplest terms, you can think of variables as a **named box**. A box that acts as a *storage place* and *location* for holding different information. 

Each box has a **unique name** which acts like a label put on the outside that is a unique identifier, and the information/content lives on the inside. The content is the variable's value.

#### Adding Two Numbers

```c
#include <stdio.h>

int main(int argv, char *argc[])
{
  int a, b, sum;           // Declaring three scope interger variables

  a = 10;                  // Assignment inline of variable a
  b = 5;                   // Assignment inline of variable b

  sum = a + b;             // Assignment to sum variable the result between the sum of a and b
  return 0;
}
```
> ***In this example was declared three integer data type variables which were used to store three values: a, b and sum.***

#

### Declaration and Initialization of Variables

When using c variables, it's always necessary declare their data type before using them in our program.

