## #DEFINE and CONST Variables

When we use define for a constant, the preprocessor generates a C program where the defined constant is searched, and the corresponding tokens are replaced by the given expression. This can save space and increase compilation time.

```c
#define NUMBER 10
```

Constant variables are regarded as true variables, not macro definitions. Therefore, they allocate a memory space on your machine, just like any other variable.

```c
const int number = 10;
```

The significant advantage of `const` over `#define` is *type checking*. `#define` cannot be *type-checked*, which can cause issues when determining *data types*. If the variable is instead a constant, we can obtain the *data type* stored in that constant variable.

As const variables are considered variables, we can use pointers on them. This means we can perform type casting, manipulate addresses, and everything else you would be able to do with a regular variable, except altering the data itself, as the data assigned to that constant variable remains constant.

In general, `const` is a better option if we have a choice and it can be successfully applied to the code. There are situations where `#define` cannot be replaced by `const`. For example, `#define` can take parameters.

```c
#include <stdio.h>
#define MULTIPLY(a, b) a*b

int main(int argc, char *argv[])
{
  printf("%d", MULTIPLY(2+3, 3+5));
  return 0;
}
```
> *The macro is expanded as 2 + 3 * 3 + 5, not as 5\*8*


```c
#include <stdio.h>
#define LIMIT 100

int main(int argc, char *argv[])
{
  printf("%d", LIMIT);
  #undef LIMIT          // Removing defined macro LIMIT
  
  printf("%d", LIMIT);   // This line causes error as LIMIT is not defined
  return 0;
}
```
> *We can also remove previously defined macros using `#undef MACRO_NAME`*