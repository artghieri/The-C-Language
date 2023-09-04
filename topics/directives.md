
## Directives

During the creation of the *source code*, in addition to regular commands, programmers can use compilation directives. Directives are readily recognized as they often appear at the beginning of source files, starting with the *prefix* `#` followed by the *directive name and its arguments*.

An important example is the `include` directive, which allows you to include the content of another file in the source code. This directive enables the use of inclusion files created by the user or provided with the compiler - typically header files with the ".h" extension.

```c
#include <stdio.h>     // searches for the "stdio.h" file primarily in the include directory (default: C:\TC\INCLUDE).

```

```c
#include "stdio.h"     // searches for the "stdio.h" file primarily in the working directory.
```

> *Regardless of the form used, this command instructs the preprocessor to include the content of the "stdio.h" file as an integral part of the source code file, exactly at that point. This action doesn't physically affect the source code file.*

The table below presents some of the most commonly used header files that can be utilized in program development.

| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**File Inclusion**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Description**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|
|:---:| :---: |
| *#include <stdio.h>* | Provides input and output functions |
| *#include <stdlib.h>* | Provides memory allocation and conversion functions |
| *#include <math.h>* | Provides mathematical functions |
| *#include <string.h>* | Provides string manipulation functions |
| *#include <time.h>* | Provides functions to work with time and dates |
| *#include <stdbool.h>* | Provides the bool type and true/false constants |
