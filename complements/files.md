## Files

The ANSI C file handling system consists of a series of interconnected functions, whose prototypes are gathered in stdio.h. All of these functions work with the concept of a "file pointer." A file pointer points to a structure that contains information about the file, such as the location of a buffer, the current character position in the buffer, whether the file is being read or written, and whether errors or the end of the file have been encountered. However, the programmer does not need to know the details of this structure, as its declaration is already defined in the stdio.h header file and is called FILE. Therefore, to create a file pointer, you just need to declare it using the syntax:

```julia
FILE *fp; // FILE is the special data type, defined as a typedef within the stdio.h file.
          // fp is the name of the file pointer.
```


## Predefined Files

In the C language, a file is a set of data that can be stored and/or retrieved from a file on disk or a peripheral device (e.g., keyboard or printer).

When a program begins execution, the system automatically opens some predefined files:

- **stdin:** Standard input device (typically the keyboard).
- **stdout:** Standard output device (typically the screen).
- **stderr:** Standard error output device (typically the screen).
- **stdaux:** Auxiliary output device (on many systems, associated with the serial port).
- **stdprn:** Standard printing device (on many systems, associated with the parallel port).

Each of these constants can be used as a FILE pointer to access the respective associated peripherals.

## File Opening

Opening or creating a file in C is done using the fopen() function. It returns a file pointer associated with the file. The general syntax is:

#### Syntax
```c
FILE *fp;
fp = fopen("file_name", "open_mode");
```

- **fp** is the file pointer that will be associated with the opened file.
- "**file_name"** is the name of the file you want to open or create, including the path if necessary.
- **"open_mode"** is the mode in which the file is to be opened or created, and it can be one of the following:

> *The fopen() function returns a pointer to the opened file, or it returns NULL if an error occurs while opening the file. It's essential to check for the NULL return value to handle potential errors when opening files.*


## Valid Values For File Opening Mode

| Opening Mode   | Description                                        |
| :--------------: | -------------------------------------------------- |
| "r"            | Opens a text file for reading.                     |
| "w"            | Opens a text file for writing.                     |
| "a"            | Opens a text file for writing (append).            |
| "r+"           | Opens a text file for reading and writing.         |
| "w+"           | Opens a text file for reading and writing.         |
| "a+"           | Opens a text file for writing and reading.         |
| "rb"           | Opens a binary file for reading.                   |
| "wb"           | Creates a binary file for writing.                 |
| "ab"           | Opens a binary file for writing (append).          |
| "r+b"          | Opens a binary file for reading and writing.       |
| "w+b"          | Creates a binary file for reading and writing.     |
| "a+b"          | Opens or creates a binary file for reading and writing (append). |


In the example below, a binary file is opened for writing:

```c
#include <stdio.h>

int main() {
  FILE *file_ptr;
  
  // Opening a binary file for writing
  file_ptr = fopen("binary_data.dat", "wb");
  if (file_ptr == NULL) {
    perror("Error opening binary file for writing");
    return 1;
  }
  printf("Binary file opened in write mode successfully.\n");
  fclose(file_ptr);
  
  return 0;
}
```

> *In this example, a binary file is opened for writing using the "wb" (write binary) mode. It ensures that the "binary_data.dat" file will be created or replaced if it already exists. Handling potential errors during file opening, as demonstrated in the example, is essential for robust file operations in your code.*


## Files Closing


File closing is a fundamental part of file manipulation in the C language. After you finish reading or writing to a file, you should close it using the fclose() function. This is important to release operating system resources and ensure that all changes are saved to the file.

#### Syntax
```julia
FILE *fp;
(...)
fclose(fp);
```

> *Where fp is the name of the file pointer (of type FILE) opened by the fopen() function.*

Not closing a file can lead to various types of problems, including data loss, file corruption, and potential intermittent errors in the program. Closing a file with fclose() also releases the file control block, making it available for reuse.

Closing a file causes any characters that have remained in the output stream's "buffer" to be written. ***But what is this "buffer"?***

When you send characters to be written to a file, these characters are temporarily stored in a memory area (the "buffer") instead of being written to the disk immediately. When the buffer is full, its contents are written to the disk all at once. The reason for doing this is related to efficiency in reading and writing files. If, for each character we wanted to write, we had to position the write head to a specific point on the disk, writing would be very slow. With the "buffer," writes only occur when there is a reasonable amount of information to be written or when the file is closed.

The *fclose()* function returns an integer value equal to zero when the operation was successful. Any value different from zero indicates an error.

Here's a simple example of how to close a file after opening it:

```c
#include <stdio.h>

int main() {
  FILE *file_ptr;
  
  // Open a file for writing
  file_ptr = fopen("example.txt", "w");
  if (file_ptr == NULL) {
    perror("Error opening the file");
    return 1;
  }
  
  // Write data to the file
  fprintf(file_ptr, "This is an example of file writing.\n");
  
  // Close the file when done
  fclose(file_ptr);
  
  return 0;
}
```

> *In this example, after writing data to the file, we close it using fclose() to ensure proper resource management and data persistence.*


## Reading and Writing Files

Reading and writing files in C is primarily done using the fread() and fwrite() functions for binary operations, and fgets() and fputs() for text operations. 

### Reading Strings From Files

Reading files in C allows you to access and process data stored in external files, such as text documents or binary files. It's a crucial operation for tasks like data analysis, configuration file parsing, and more.

#### Syntax
```julia
FILE *fp;

fgets (str, size, fp); 
```

- **str:** This is a character array (string) where the line of text read from the file will be stored.
- **size:** It represents the maximum number of characters to be read from the file, including the newline character and the null-terminating character. It's essentially the size of the buffer (str).
* **fp:** This is the file pointer associated with the file you want to read from.

This function reads the string until a newline character is encountered or until size - 1 characters have been read, whichever occurs first. If the newline character ('\n') is encountered, it becomes part of the string, unlike the gets() function. The resulting string always ends with '\0' (hence, at most size-1 characters are read).

```c
#include <stdio.h>
  
  int main() {
  FILE *file_ptr;
  char line[100];
  
  file_ptr = fopen("example.txt", "r");
  if (file_ptr == NULL) {
    perror("Error opening the file");
    return 1;
  }
  
  while (fgets(line, sizeof(line), file_ptr) != NULL) {
    printf("%s", line); // Print each line to the console
  }
  
  fclose(file_ptr);
  return 0;
  }
```

#

### Writings Strings To Files

Writing files in C allows you to create, modify, and store data in external files. It's essential for tasks like logging, data export, and configuration file creation.

### Syntax
```julia
FILE *fp;

fputs (str, fp);
```

- **str:** This is a character array (string) where the line of text read from the file will be stored.
* **fp:** This is the file pointer associated with the file you want to read from.


The fputs() function accesses the characters of the string str (excluding the special null-terminating character - '\0') and writes them to the output file pointed to by the fp pointer. It returns a negative value if an error occurs and no error pointer is defined; otherwise, it returns EOF (End of File).

Using fputs() to Write Strings to Files:

```c
#include <stdio.h>

int main() {
  FILE *file_ptr;
  char data[] = "This is an example of writing a string to a file.\n";
  
  file_ptr = fopen("output.txt", "w");
  if (file_ptr == NULL) {
    perror("Error opening the file");
    return 1;
  }
  
  fputs(data, file_ptr); // Write the string to the file
  
  fclose(file_ptr);
  return 0;
}
```

> *This code opens a text file for writing, checks for successful file opening, writes a string to the file using fputs(), and closes the file. It showcases a fundamental example of writing strings to a text file in C while handling potential errors.*

#

### Reading and Writing Blocks of Data

Reading and writing blocks of data in files is a common task in C, especially for binary file operations.

#### FREAD 

You can use the fread() function to read blocks of binary data from a file. This is particularly useful when working with structured data like records or binary formats.

```c
fread (buffer, bytes_size, cont, fp);
```

Where:
- **buffer:** It's a pointer to the buffer where the data will be stored.
- **bytes_size:** It specifies the size of each data element to be read, in bytes.
- **cont:** It represents the number of data elements to read.
- **fp:** This is the file pointer associated with the file from which you want to read data.

> *The *fread()* function reads a total of bytes_size * cont bytes from the file and stores them in the memory pointed to by buffer. It's commonly used for reading binary data from files.*

Here's an example of how to use fread()

```c
#include <stdio.h>

int main() {
FILE *file_ptr;
int data[5]; // Array to store data

file_ptr = fopen("data.bin", "rb");
if (file_ptr == NULL) {
  perror("Error opening the file");
  return 1;
}

// Read 5 integers (20 bytes) from the file into the 'data' array
size_t elements_read = fread(data, sizeof(int), 5, file_ptr);

fclose(file_ptr);

if (elements_read == 5) {
  // Successfully read 5 integers from the file
  for (int i = 0; i < 5; i++) {
      printf("Data[%d]: %d\n", i, data[i]);
  }
} else {
  printf("Error reading data from the file\n");
}

return 0;
}
```

> *In this example, fread() reads an array of 5 integers (20 bytes) from a binary file, and the data is stored in the data array. It's important to check the return value of fread() to ensure that the expected number of elements was read successfully.*

#

#### FWRITE 

To write blocks of data to a file, you can use the fwrite() function. It allows you to write structured data to binary files efficiently.

```c
fwrite (buffer, bytes_size, cont, fp); 
```

Where:
- **buffer:** It's a pointer to the buffer where the data will be stored.
- **bytes_size:** It specifies the size of each data element to be read, in bytes.
- **cont:** It represents the number of data elements to read.
- **fp:** This is the file pointer associated with the file from which you want to read data.

The *fwrite()* function returns the number of elements actually written. This value will be equal to cont, unless an error occurs during the process.

When the file is opened for binary data operations, such as with the "rb" mode for reading and "wb" mode for binary writing, the *fread()* and *fwrite()* functions can read and write any type of data.

Here's an example that uses the fwrite() function to write data to a binary file in C:

```c
#include <stdio.h>

struct Student {
    char name[50];
    int roll_number;
    float marks;
};

int main() {
  FILE *file_ptr;
  struct Student student_data;
  
  // Prepare some data
  strcpy(student_data.name, "John Doe");
  student_data.roll_number = 101;
  student_data.marks = 85.5;
  
  file_ptr = fopen("student_data.bin", "wb");
  if (file_ptr == NULL) {
    perror("Error opening the file");
    return 1;
  }
  
  // Write the student_data structure to the binary file
  size_t elements_written = fwrite(&student_data, sizeof(struct Student), 1, file_ptr);
  
  fclose(file_ptr);
  
  if (elements_written == 1) {
    printf("Data was successfully written to the file.\n");
  } else {
    printf("Error writing data to the file.\n");
  }
  
  return 0;
}
```

> *This code demonstrates how to use fwrite() to write structured data to a binary file.*

#

#### STANDARD STREAMS

Standard file streams allow the programmer to read and write to files in a manner similar to how they read and write to the screen. For this purpose, the functions fscanf() and fprintf() are used, respectively.

#### FPRINTF

fprintf is a C library function used for formatted output to a file. It allows you to write data to a specified file, formatting it according to a specified format string, similar to how printf is used for output to the console.

```c
int fprintf(FILE *stream, const char *format, ...);
```

Where:
- **stream:** A pointer to the FILE structure that represents the file to which you want to write data.
- **format:** A format string that specifies how the data should be formatted and written to the file. It may contain format specifiers like %d for integers, %f for floats, %s for strings, etc.
- **...:** Additional arguments corresponding to the format specifiers in the format string. These are the values you want to write to the file.

The fprintf function returns the number of characters successfully written to the file. If an error occurs, it will return a negative value.

Here's a basic example of using fprintf to write to a file:

```c
#include <stdio.h>

int main() {
  FILE *file_ptr;
  file_ptr = fopen("output.txt", "w"); // Open a file for writing
  
  if (file_ptr == NULL) {
    perror("Error opening the file");
    return 1;
  }
  
  fprintf(file_ptr, "This is a line written to the file.\n");
  fprintf(file_ptr, "You can write more lines as well.\n");
  
  fclose(file_ptr); // Close the file
  
  return 0;
}
```

> *In this example, fprintf is used to write formatted data to the "output.txt" file. You can use format specifiers, similar to those used in printf, to control the format of the data being written to the file.*

#### FSCANF

fscanf is a C library function used for formatted input from a file. It allows you to read data from a specified file, interpreting it according to a specified format string, similar to how scanf is used for input from the console.

```c
int fscanf(FILE *stream, const char *format, ...);
```

Where:
- **stream:** A pointer to the FILE structure that represents the file from which you want to read data.
- ***format:*** A format string that specifies how the data in the file should be interpreted and extracted. It may contain format specifiers like %d for integers, %f for floats, %s for strings, etc.
- **...:** Additional arguments corresponding to the format specifiers in the format string. These are pointers to variables where the extracted data should be stored.

The fscanf function returns the number of items successfully read and assigned. If it encounters an error or reaches the end of the file before reading the expected number of items, it will return a value less than the number of items requested or EOF (End of File) if there's a reading error.

Here's a basic example of using fscanf to read from a file:

```c
#include <stdio.h>

int main() {
  FILE *file_ptr;
  char name[50];
  int age;
  
  file_ptr = fopen("input.txt", "r"); // Open a file for reading
  
  if (file_ptr == NULL) {
    perror("Error opening the file");
    return 1;
  }
  
  fscanf(file_ptr, "%s %d", name, &age); // Read data from the file
  
  fclose(file_ptr); // Close the file
  
  printf("Name: %s\nAge: %d\n", name, age);
  
  return 0;
}
```

> *In this example, fscanf is used to read formatted data from the "input.txt" file. It interprets the data based on the format specifiers in the format string provided.*

#

### File Remove

File removal in C is done using the remove() function. This function allows you to delete a file from the file system. Here is the syntax of the remove() function:

```c
int remove(const char *filename);
```

- **filename:** A string containing the name of the file you want to remove.

The *remove()* function returns zero if the removal is successful and a non-zero value if an error occurs during the removal operation.

Here's a simple example of how to use the remove() function to delete a file:

```c
#include <stdio.h>

int main() {
  const char *filename = "file_to_delete.txt";
  
  if (remove(filename) == 0) {
    printf("The file %s has been successfully removed.\n", filename);
  } else {
    perror("Error removing the file");
  }
  
  return 0;
}
```

> *In this example, we attempt to remove a file named "file_to_delete.txt." If the removal is successful, a success message is displayed. Otherwise, an error message is displayed using the perror() function. Be sure to handle possible errors when using the remove() function.*

#

### Buffer Clearing

The fflush function in C is used to flush (empty) the output buffer associated with a file or stream. Flushing the buffer means that any data stored in the buffer is written to the corresponding output destination (e.g., a file or the screen) immediately. This ensures that the data is visible or saved as expected.

```c
int fflush(FILE *stream);
```

Where:
- **stream:** A pointer to the FILE structure representing the file or stream for which you want to flush the output buffer.

> *If successful, fflush returns zero. If an error occurs, it returns EOF (End of File), and you can use ferror to check for the error condition.*

Example of using fflush:

```c
#include <stdio.h>

int main() {
  FILE *file_ptr;
  file_ptr = fopen("output.txt", "w");
  
  if (file_ptr == NULL) {
    perror("Error opening the file");
    return 1;
  }
  
  fprintf(file_ptr, "This is some text in the file buffer.\n");
  fflush(file_ptr); // Flush the output buffer to ensure data is written immediately
  
  fclose(file_ptr);
  
  return 0;
}
```

Flushing the output buffer is important to make sure that data is written promptly, especially when it's critical that the data appears in the file or is sent over a network connection without delays.

## Repositioning Functions

Every time we work with files, there is a current position within the file. This is the position from which the next character will be read or written. Typically, in sequential access, we don't need to manipulate this position because when we read data, the position in the file is automatically incremented. However, in random access, it's often necessary to reposition the file position indicator to obtain the desired data.

#

### REWIND

The rewind() function repositions the file position indicator (pointer) to the beginning of the file specified by the pointer passed as an argument. Its syntax is:

```c
rewind(fp);
```

Using this function has the same effect as closing and reopening the file. However, using this function is more efficient in terms of performance. It allows you to quickly reset the file pointer to the beginning of the file without the overhead of closing and reopening the file. This can be especially useful when you want to start reading or writing from the beginning of the file again without the need to open and close it multiple times.

#

### FSEEK

The fseek function is used to move the read/write position pointer within a file. It allows you to specify an offset in relation to a reference position and move from that position.

Syntax:
```c
int fseek(FILE *stream, long int offset, int origin);
```

Where:
- **stream:** A pointer to the FILE structure representing the file.
- **offset:** The offset you want to apply to the position pointer. It can be positive or negative, depending on the direction you want to move.
- **origin:** The reference position from which the offset is applied. It can take one of the following values:
  - **SEEK_SET (or 0):** From the beginning of the file.
  - **SEEK_CUR (or 1):** From the current position of the pointer.
  - **SEEK_END (or 2):** From the end of the file.

Example:

```c
#include <stdio.h>

int main() {
  FILE *file_ptr;
  file_ptr = fopen("sample.txt", "r");
  
  if (file_ptr == NULL) {
    perror("Error opening the file");
    return 1;
  }
  
  fseek(file_ptr, 10, SEEK_SET); // Move the pointer to position 10 from the beginning
  
  int c;
  while ((c = fgetc(file_ptr)) != EOF) {
    putchar(c);
  }
  
  fclose(file_ptr);
  
  return 0;
}
```

> *In this example, we use fseek to move the pointer to position 10 from the beginning of the "sample.txt" file and then read and display the file's content from that point*

#

## Other Functions

### Macro FEOF


EOF, which stands for "End Of File," indicates the end of a file. Therefore, it's possible to determine whether a program has reached the end of a file by comparing the character read with the EOF identifier, which is defined in the stdio.h header file.

When reading data from a file using functions like fgetc, the value EOF is returned when the end of the file is reached. You can use this value to check if you have reached the end of the file in your program's file processing logic. For example:

```c
#include <stdio.h>

int main() {
  FILE *file_ptr;
  file_ptr = fopen("sample.txt", "r");
  
  if (file_ptr == NULL) {
    perror("Error opening the file");
    return 1;
  }
  
  int c;
  while ((c = fgetc(file_ptr)) != EOF) {
    putchar(c);
  }
  
  fclose(file_ptr);
  
  return 0;
}
```

> *In this example, the program reads characters from the "sample.txt" file in a loop, and the loop continues until EOF is encountered, indicating the end of the file*

Another way to determine if the end of a file has been reached is by using the feof() macro. It returns a non-zero value when the end of the file associated with the specified file pointer has been encountered. Otherwise, it returns zero. Its syntax is:

```c
feof(fp);
```

You can use feof() to check for the end of a file in your program's file processing logic. Here's an example:

```c
#include <stdio.h>

int main() {
  FILE *file_ptr;
  file_ptr = fopen("sample.txt", "r");
  
  if (file_ptr == NULL) {
    perror("Error opening the file");
    return 1;
  }
  
  int c;
  while (!feof(file_ptr)) {
    c = fgetc(file_ptr);
    if (c != EOF) {
        putchar(c);
    }
  }
  
  fclose(file_ptr);
  
  return 0;
}
```

> *In this example, we use feof() within a loop to check if the end of the file has been reached before attempting to read characters. This helps ensure that we don't read beyond the end of the file.*

#

### CLEARERR

The clearerr() function is used to clear the error or end-of-file (EOF) indicator associated with a file pointer. It has the following syntax:

```c
clearerr(fp);
```

In this syntax:

- **fp** is a file pointer associated with the file where EOF or an error was encountered.

The clearerr() function is helpful when you want to reset the error or EOF state of a file pointer so that you can continue working with the file without being affected by previous error conditions.

Here's a simple example:

```c
#include <stdio.h>

int main() {
  FILE *file_ptr;
  file_ptr = fopen("sample.txt", "r");
  
  if (file_ptr == NULL) {
    perror("Error opening the file");
    return 1;
  }
  
  // Perform file operations that may set an error or EOF condition
  // ...
  
  if (feof(file_ptr)) {
    printf("End of file encountered.\n");
  }
  
  clearerr(file_ptr); // Clear the EOF or error condition
  
  // Now you can continue working with the file without considering previous errors
  // ...
  
  fclose(file_ptr);
  
  return 0;
}
```

> *In this example, we first check for the EOF condition using feof(). If EOF is encountered, we print a message. Afterward, we use clearerr() to clear any error or EOF condition, allowing us to continue working with the file without considering previous errors.*

#

### Macro FERROR

A macro FERROR (or ferror()) is a predefined macro in the C programming language that is used to check whether an error has occurred on a stream or file associated with a FILE pointer. It returns a non-zero value if an error condition is set on the file stream, indicating that an error has occurred. If no error is set, it returns zero.

Here's the basic syntax of using ferror():

```c
if (ferror(fp)) {
    // Handle the error
}
```

- **fp** is a pointer to a FILE structure representing the file stream you want to check for errors.

You can use ferror() to detect and handle errors that may occur during file I/O operations. For example, if you are reading from a file and an error occurs, you can use ferror() to identify the error and take appropriate action, such as reporting the error or attempting to recover from it.

Here's a simple example:

```c
#include <stdio.h>

int main() {
  FILE *file_ptr;
  file_ptr = fopen("non_existent_file.txt", "r");
  
  if (file_ptr == NULL) {
    perror("Error opening the file");
    return 1;
  }
  
  int c = fgetc(file_ptr);
  if (ferror(file_ptr)) {
    printf("An error occurred while reading the file.\n");
  } else {
    printf("Read character: %c\n", (char)c);
  }
  
  fclose(file_ptr);
  
  return 0;
}
```

> *In this example, we open a file that does not exist, and then we use ferror() to check if an error occurred while trying to read from the file. If an error is detected, we print an error message; otherwise, we display the character read from the file.*

#

### PERROR

perror() is a C library function used to print an error message to the standard error stream (usually the console) based on the value of the global variable errno. It is a convenient way to display a descriptive error message when a system call or library function fails.

Here's the basic syntax of perror():

```c
#include <stdio.h>
#include <errno.h>

void perror(const char *s);
```

- **s:** A string that is typically used as a prefix for the error message. It can be NULL if no prefix is needed.

The perror() function looks up the error code stored in errno, fetches the corresponding error message from the system, and then prints the error message to the standard error stream along with the provided prefix (if any). The output typically includes both the prefix and the system-specific error message.

Here's an example of using perror():

```c
#include <stdio.h>
#include <errno.h>

int main() {
  FILE *file_ptr;
  file_ptr = fopen("non_existent_file.txt", "r");
  
  if (file_ptr == NULL) {
    perror("Error opening the file");
    return 1;
  }
  
  // Perform file operations
  
  fclose(file_ptr);
  
  return 0;
}
```

> *In this example, we attempt to open a file that doesn't exist. If the fopen() function fails (returns NULL), perror("Error opening the file") is called to print an error message like "Error opening the file: No such file or directory" to the standard error stream, providing context about the error.*


perror() is particularly useful when dealing with system calls and library functions that may fail, as it helps developers diagnose and troubleshoot errors more effectively.

