## Data Types

During the compilation of the source code, the C compiler seeks to allocate the necessary *memory space* for program execution. While the compiler can determine the *data types* and *memory space* required for constants found in the code, for variables, this is only possible if there is a prior declaration of the *data type* used.

Each *data type* has a predetermined ***memory size requirement*** and an ***associated range of permissible values***. For example, a *character* typically occupies **1 byte**, while an *integer* usually takes up **2 bytes**. However, to ensure the portability of C code, this assumption cannot be taken as true. This is because the size and range of these *data types* vary according to the type of processor and the implementation of the C compiler. 

The ANSI standard stipulates only the minimum range for each data type, not its size in bytes.

| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Types**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Description**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Approximate Size**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Minimum Range**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;     |
| :---:       | :---:             | :---:                  | :---:                   |
| char      | Character       | 8 bits = 1 byte      | -127 to 127            |
| int       | Integer         | 16 bits = 2 bytes    | -32.767 to 32.767      |
| float     | Floating-Point  | 32 bits = 4 bytes    | 7 digits of precision|
| double    | Double precision Floating-Point  | 64 bits = 8 bytes | 10 digits of precision |
| void     | No Value | |

Elements of the *char type* are typically used to hold values defined by the **ASCII** character set. Elements of the *int* type* generally correspond to the natural size of a word on the host computer. Thus, on a *16-bit machine*, int will likely be **16 bits**, and on a *32-bit machine*, int should be **32 bits**. The exact format of *floating-point* elements depends on how they are implemented.

The range of *float* and *double* types is given in digits of precision. Their magnitudes, however, depend on the method used to represent *floating-point* numbers. Regardless of the method, the number can be very large (the ANSI standard specifies the minimum range as 1x10^-37 to 1x10^37). The *void type* explicitly declares a function that does not return any value or creates generic pointers.

#

### Data Type Modifiers

With the exception of the void and *float types*, the other basic types can be adapted more precisely to the needs of the studied problem. To achieve this, it is necessary to prefix the basic *data type* with one of the ***type modifiers*** (signed, unsigned, long, and short) to alter the meaning of the type.

Usually, only the *long* modifier can be applied to the *double type*. This modification generates a *floating-point type with greater precision*. All four modifiers can be applied to *integers*. The ***short*** and ***long*** modifiers aim to provide different sizes of *integers* (smaller integers - short int or larger integers - long int).

The *unsigned* modifier is used to specify variables without sign. An *unsigned int* will be an integer that takes only positive values.

Below are the permitted data types and their maximum and minimum values in a typical compiler for 16-bit hardware. Also specified in this table is the format that should be used to read the data types using the ***scanf()*** function.

|  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Type**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;       | **Number of Bits** |  &nbsp;&nbsp;&nbsp;&nbsp;**scanf Read Format**&nbsp;&nbsp;&nbsp;&nbsp;|   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Start**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;   |   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**End**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;   |
|:---:|:---:|:---:|:---:|:---:|
|   char          |        **8**       |           *%c*             |    **-128**   |    **127**  |
|   unsigned char |        **8**       |           *%c*             |      **0**    |    **255**  |
|   int          |       **16**       |       *%i or %d*           |  **-32,768**  |  **32,767** |
|   unsigned int  |       **16**       |           *%u*             |      **0**    |  **65,535** |
|   short int     |       **16**       |     *%hi or %hd*           |  **-32,768**  |  **32,767** |
|   unsigned short int|   **16**       |           *%hu*            |      **0**    |  **65,535** |
|   long int     |       **32**       |     *%li or %ld*           |**-2,147,483,648**|**2,147,483,647**|
|   unsigned long int|   **32**       |           *%lu*            |      **0**    |**4,294,967,295**|
|   float         |       **32**       | *%f, %e, or %g*            |  **3.4E-38**  |  **3.4E+38**|
|   double        |       **64**       |*%lf, %le, or %lg*          |**1.7E-308**   |**1.7E+308**|
|   long double   |       **80**       |           *%Lf*            |**3.4E-4932** |**3.4E+4932**|

> *Certainly, it's important to note that the floating-point ranges in the table above are indicated in terms of exponent range, but the numbers can take both positive and negative values.*