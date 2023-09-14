## Input and Output Commands

Data input and output are essential pillars in programming, enabling interaction between programs and users, as well as communication with the external environment. This dynamic allows for acquiring crucial information and presenting processed results.

### Output of Data

The `printf()` function enables the *output* of values (constants, variables, or expression results). This function converts and prints its *arguments* to the standard output following the format specified in the *control string*.

```c
printf("control string", arguments);
```

The *control string*, describes everything that the function will display on the screen. This string not only shows the characters that will be presented but also the respective formats and positions of constants, variables, and expressions listed in the argument list.

```c
int a, b, sum;

a = 2;
b = 3;

sum = a + b;
printf("%s %d %s %d %s %d", "The sum between the numbers:", a, "and", b, "is equals to", sum);
```

In summary, the control string consists of three types of characters:

- **Miscellaneous characters** that will be displayed on the screen (corresponding to the text to be shown).
- **Escape characters "\\"** used to assist in cursor movement on the screen or carriage movement.
- **Format specifier characters "%"** that define the position and manner in which each of the variables in the argument list will be displayed.


|    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Specifier** &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;   |     &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Type**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;     |         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Example**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;              |       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Output**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;       |
|:-----------------:|:-------------------:|:---------------------------------:|:----------------------:|
|       **`%c`**      |    ***Character***       |       **`printf("%c", 'A');`**          |           **A**            |
|       **`%d`**     |      ***Integer***        |       **`printf("%d", 42);`**           |           **42**           |
|       **`%f`**      |  ***Floating Point***     |      **`printf("%f", 3.14);`**          |        **3.140000**       |
|      **`%lf`**      |       ***Double***        |   **`printf("%lf", 1.618);`**           |        **1.618000**       |
|       **`%o`**      |       ***Octal***         |        **`printf("%o", 8);`**           |           **10**           |
|       **`%p`**      |      ***Pointer***        | **`int var = 5; printf("%p", &var);`**  |    **Memory address**     |
|       **`%s`**      |       ***String***        | **`printf("%s", "Hello");`**            |         **Hello**         |
|       **`%u`**      | ***Unsigned Integer***    |     **`printf("%u", -42);`**            | **Unpredictable value**   |
|   **`%x or %X`**    |   ***Hexadecimal***       |     **`printf("%x", 255);`**            |           **ff**           |
|       **`%%`**      | ***Percent Symbol***      |         **`printf("%%");`**             |           **%**            |

> *In the table above, there are Some Format Specifiers for the printf() Function, followed by practical examples.*

#

### Input of Data

The `scanf()` function reads characters from the *standard input*, interprets them according to the format specification, and stores the results in variables declared in the program.

```c
scanf("control string", &variable);
```

The *memory address* representation of the variables that will *receive the input data is provided* using the `&` operator *followed by the variable name*. Additionally, this function also uses escape control characters via backslash codesand formatting characters `%`.

```c
int number;

scanf("%d", &number);   // The scanf() function reads the typed number and stores it in the number variable as an integer.
```

| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Specifier**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Description**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;                          |  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Example**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |
|:-----------------:|:-------------------:|:---------------------------------:|
| **`%d`**        | ***Read an integer***                        | **`scanf("%d", &num);`**            |
| **`%f`**        | ***Read a floating-point number***            | **`scanf("%f", &floatValue);`**     |
| **`%c`**        | ***Read a character***                       | **`scanf("%c", &letter);`**         |
| **`%s`**        | ***Read a string***                          | **`scanf("%s", stringVar);`**       |
| **`%lf`**       | ***Read a double (long float)***             | **`scanf("%lf", &doubleValue);`**   |
| **`%x`**        | ***Read a hexadecimal integer***            | **`scanf("%x", &hexValue);`**       |
| **`%o`**        | ***Read an octal integer***                  | **`scanf("%o", &octValue);`**       |
| **`%u`**        | ***Read an unsigned integer***               | **`scanf("%u", &unsignedValue);`**  |

> *These format specifiers are used with the scanf() function to read data from the standard input.*