## Strings 

In C, you don't have a dedicated string data type like in some higher-level languages. Instead, strings are represented using arrays of characters. The last character of a string is always the null character, which indicates the end of the string.

Here's a simple example of how strings are used in C:

```c
#include <stdio.h>

int main(int argc, char *argv[])
{
  // Declaring and initializing a string
  char greeting[] = "Hello, world!";
  
  // Printing the string
  printf("%s\n", greeting);
  
  return 0;
}
```

> *In this example, the string "Hello, world!" is stored in the greeting array. The %s format specifier in the printf function is used to print the string.*

### Strings Manipulation

Strings (sequences of characters) are the most common use case for arrays (a string is an array of chars) in programming. It's important to remember that strings have their last element as a '\0' (null terminator). As a result, the size of a string is the count of the characters entered plus the null terminator '\0'.

```c
char string_name[size];
```

> *The C standard library provides various functions for string manipulation. These functions are valuable because you can't, for instance, directly assign one string to another (string1 = string2;). Strings must be compared and manipulated element by element.*

For example, to compare two strings, you would use functions like strcmp(), and to copy strings, you would use functions like strcpy(). These functions are designed to handle the intricacies of C strings, including the null terminator, which is crucial for proper string manipulation and comparison.

# 

### Basic String Manipulation Functions 

Below, we will present some basic functions for string manipulation. With the exception of the ***fgets()*** function, the other functions are contained in the ***string.h*** header file.

#### FGETS
In C programming, fgets is a fundamental function for reading strings from an input stream, typically used for reading text from files or the standard input (keyboard). 

```c
char *fgets(char *str, int n, FILE *stream);
```

> ***str**: A pointer to a character array (string) where the read line of text will be stored.*   
> ***n**: An integer specifying the maximum number of characters to read, including the null terminator. This helps prevent buffer overflows.*  
> ***stream**: A pointer to the input stream from which to read the line of text. This can be a file pointer, such as stdin for standard input (keyboard), or a file opened using fopen for reading.*

The key advantage of fgets is that it allows you to specify the maximum number of characters to read, preventing buffer overflow issues. It also automatically appends a null terminator ('\0') to the end of the string, making it suitable for working with C strings.

```c
#include <stdio.h>

int main() {
  char input[100]; // Maximum size of the string to be read
  
  printf("Enter a line of text: ");
  
  // Use fgets to read a line of text from standard input
  fgets(input, sizeof(input), stdin);
  
  printf("You entered: %s", input);
  
  return 0;
}
```

> *In this example, fgets reads a line of text from stdin (standard input) and stores it in the input character array with a maximum size of 100 characters.*

#

#### STRCPY

The *strcpy* function in C is used for string manipulation and is short for **"string copy."** It allows you to copy the characters from one string to another, including the null terminator. This function is commonly used to duplicate strings or to initialize character arrays with a specific string value.

```c
char *strcpy(char *destination, const char *source);
```

> ***destination**: A pointer to the destination character array (string) where the copy will be stored. Ensure that the destination array has enough space to hold the source string.*  
> ***source**: A pointer to the source string that you want to copy.*

Here's an example of using strcpy to copy a string from one array to another:

```c
#include <stdio.h>
#include <string.h>

int main() {
  char source[] = "Hello, World!";
  char destination[20]; // Make sure it's large enough to hold the source
  
  // Use strcpy to copy the source string to the destination
  strcpy(destination, source);
  
  printf("Source: %s\n", source);
  printf("Destination: %s\n", destination);
  
  return 0;
}
```

> *The strcpy function copies the content of the source string to the destination string, including the null terminator. It's important to ensure that the destination array has sufficient space to accommodate the source string to avoid buffer overflows.*

#

#### STRCAT

The strcat function in C is used for string manipulation and stands for "string concatenation." It allows you to concatenate (append) one string to the end of another string. This function is particularly useful when you need to combine two strings into a single string.

```c
char *strcat(char *destination, const char *source);
```

> ***destination**: A pointer to the destination character array (string) where the copy will be stored. Ensure that the destination array has enough space to hold the source string.*  
> ***source**: A pointer to the source string that you want to copy.*

Here's an example of using strcpy to copy a string from one array to another:

```c
#include <stdio.h>
#include <string.h>

int main() {
  char destination[50] = "Hello, ";
  char source[] = "World!";
  
  // Use strcat to append the source string to the destination
  strcat(destination, source);
  
  printf("Concatenated String: %s\n", destination);
  
  return 0;
}
```

> *The strcat function appends the content of the source string to the end of the destination string. Ensure that the destination array has sufficient space to accommodate both strings to avoid buffer overflows.*

#

#### STRLEN

The strlen function in C is used to determine the length of a string, which means it calculates the number of characters in a string. This function is particularly helpful when you need to know the size of a string for various operations like memory allocation or string manipulation.

```c
size_t strlen(const char *str);
```

> ***str**: A pointer to the null-terminated string for which you want to find the length.*  
> ***size_t**: strlen returns a value of type size_t, which is an unsigned integer type that can hold the length of the string.*

Here's an example of using strcpy to copy a string from one array to another:

```c
#include <stdio.h>
#include <string.h>

int main() {
  char text[] = "Hello, World!"; // Null-terminated string
  
  // Use strlen to find the length of the string
  size_t length = strlen(text);
  
  printf("Length of the string: %zu\n", length);
  
  return 0;
}
```

> *The strlen function calculates the length of the null-terminated text string and returns it as a size_t value, which is then printed to the console.*

#

#### ATOI AND ATOF

The *atoi* and *atof* functions are used for converting strings to numeric values. These functions are valuable when you need to extract numerical data from strings, which is a common task when processing input data or configuration files.

**Syntax of atoi Function:**

> *str: A pointer to the null-terminated string containing the integer representation.*

```c
int atoi(const char *str);
```

**atoi Function:**
- atoi stands for "ASCII to Integer."
- It is used to convert a string containing an integer representation into an actual integer value.
- The function stops conversion when it encounters a character that is not a digit.
- It returns an integer.

#

**Syntax of atof Function:**

```c
double atof(const char *str);
```

> *str: A pointer to the null-terminated string containing the floating-point representation.*

**atof Function:**
- atof stands for "ASCII to Float."
- It is used to convert a string containing a floating-point representation into a floating-point (double) value.
- The function stops conversion when it encounters a character that is not a digit or a decimal point.
- It returns a double.

#

Example of Using atoi and atof:

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
  char intStr[] = "12345";
  char floatStr[] = "3.14159";
  
  // Using atoi to convert a string to an integer
  int intValue = atoi(intStr);
  
  // Using atof to convert a string to a floating-point number
  double floatValue = atof(floatStr);
  
  printf("Integer value: %d\n", intValue);
  printf("Floating-point value: %f\n", floatValue);
  
  return 0;
}
```

> *The atoi function converts the intStr string to an integer, and the atof function converts the floatStr string to a floating-point number, which are then printed to the console.*