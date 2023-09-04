
## Arrays and Matrices

Arrays and matrices are fundamental concepts in C programming, providing a structured approach to store and manipulate multiple elements of the *same data type*. An *array* is a collection of elements, such as integers or characters, arranged sequentially in memory. Matrices, a n-dimensional extension of arrays, organize data in n-axis, creating a grid-like structure. These constructs empower programmers to efficiently manage large datasets, streamline operations, and enable versatile data handling. 

#

### Arrays

Arrays stand as foundational elements in C programming, embodying organized collections capable of containing multiple data items of a consistent data type. With a contiguous memory arrangement, arrays offer swift access and manipulation of elements. This construct simplifies the management of large datasets, streamlining operations and augmenting code structure. 

```julia
data_type array_name[array_size];
```

> *data_type: Specifies the type of data that the array will hold.*  
> *array_name: The name given to the array, used to reference its elements.*  
> *array_size: The number of elements the array can hold, which should be a positive integer.*

For example, to declare an *array of integers* named numbers with a size of 5:

```julia
int numbers[5];
```

> *The array elements are not initialized automatically. Ensure to explicitly assign values to the elements using assignments or loops before accessing them to avoid unexpected behavior due to uninitialized data.*

When declaring arrays in C, the compiler allocates memory space based on the specified dimensions. For instance, with a declaration like `int numbers[5];`, the compiler reserves contiguous memory for efficient data storage. This results in *10 bytes* - ***2 bytes per integer times 5***. This allocation approach optimizes memory utilization, streamlining access and manipulation of array elements.

The assignment or utilization of the value of one of the cells in arrays can be done using the syntax:

```julia
array[position] = 1;

variable = array[position];
```

In the C language, indexing always starts at *zero*. This implies that, in the previous example, the data in the *array* ***numbers*** will be indexed from 0 to 4. However, the C compiler does not verify whether the index used in the program is within valid bounds (this responsibility falls on the programmer).

Just like other variables, these types of structures can also be initialized during declaration, as follows:

```julia
int numbers[3] = {10, 20, 30};
```

> *Ensure the number of provided values matches the array size to prevent overstepping boundaries or leaving uninitialized elements. This concise initialization method enhances code readability and efficiency, especially for smaller arrays.*

When the structure is initialized during declaration, the size of one of the dimensions can be omitted, as it will be inferred from the number of values listed within curly braces. Thus, the above declaration could be rewritten as follows:

```julia
int numbers [] = {10, 20, 30};
```

Here is an example program that utilizes arrays:

```c
#include <stdio.h>

int main(int argc, char *argv[])
{
  int scores[5];     // Declare an array to store 5 integer scores
  
  printf("Enter 5 student scores:\n");
  // Use a loop to store array values using scanf()
  for (int i = 0; i < 5; i++)   
  {  
    printf("Enter score for student %d: ", i + 1);
    scanf("%d", &scores[i]);
  }
  
  // Calculate the average score
  int total = 0;
  for (int i = 0; i < 5; i++)
  {
    total += scores[i];
  }
  double average = (double)total / 5.0;
  
  // Display the array elements and the average
  printf("Scores: ");
  for (int i = 0; i < 5; i++) {
    printf("%d ", scores[i]);
  }
  printf("\nAverage score: %.2f\n", average);
  return 0;
}
```

> *In this example, the program uses a loop structure to prompt the user to enter 5 student scores using the scanf function within the loop. The scores are stored in the scores array. After storing the scores, the program calculates the average score using a loop, and finally, it displays the entered scores and the average using printf.*

#

### Matrices

Matrices, find profound significance in programming, where they extend the array concept to a n-dimensional grid. This grid-like structure, empowers programmers to handle complex datasets methodically. In the C language, matrices emerge as a robust tool for diverse tasks, from mathematical operations to image processing and simulations. Acquiring a grasp of matrices allows to navigate multidimensional data seamlessly, amplifying code efficiency and structured problem-solving.

```julia
data_type matrix_name[size1][size2]...[sizeN];
```

> *data_type: Specifies the type of data that the array will hold, such as int, float, char, etc.*  
> *array_name: The name given to the array, used to reference its elements.*  
> *size1, size2, ..., sizeN: The sizes of each dimension in the array.*

For example, to declare a 3-dimensional array of integers named matrix with sizes 2x3x4:

```c
int matrix[2][3][4];
```

> *Ensure that the provided sizes align with the intended data structure, and remember that multidimensional arrays (matrices) can quickly become complex to manage.*

As the same case for array type, with a declaration like `int matrix[2][3][4];`, the compiler reserves contiguous memory for efficient data storage. This results in *96 bytes* - (2 x 2 x 3 x 4).

The assignment or utilization of the value of one of the cells in arrays can be done using the syntax:

```julia
matrix[size1][size2]...[sizeN] = 1;

variable = matrix[size1][size2]...[sizeN];
```

In the C language, indexing always starts at zero. This signifies that, in the previous example, the data in the the matrix will hold 24 values, respectively indexed by the ordered pairs (0,0,0), (0,0,1), (0,0,2), (0,0,3), (0,1,0), (0,1,1), (0,1,2), (0,1,3), (0,2,0), (0,2,1), (0,2,2), (0,2,3), (1,0,0), (1,0,1), (1,0,2), (1,0,3), (1,1,0), (1,1,1), (1,1,2), (1,1,3), (1,2,0), (1,2,1), (1,2,2), (1,2,3). This indexing convention is essential to remember when working with matrices in C, as it ensures proper access to elements based on their positions.

Just like other variables, these types of structures can also be initialized during declaration, as follows:

```julia
int matrix[2][2][2] = {
    {{1, 2}, {3, 4}},
    {{5, 6}, {7, 8}}
};
```

> *In this example, the array has 2x2x2 dimensions, and each element is initialized accordingly. The concept extends similarly for arrays with more than three dimensions.*

Here is an example program that utilizes matrices:


```c
#include <stdio.h>

int main(int argc, char *argv[])
{
  int matrix[3][3]; // Declare a 3x3 matrix
  float total = 0;
  
  // Input values into the matrix using a for loop and scanf
  for (int row = 0; row < 3; row++)
  {
    for (int column = 0; column < 3; column++)
    {
      printf("Enter value for matrix[%d][%d]: ", row, column);
      scanf("%d", &matrix[row][column]);
      total += matrix[row][column]; // Calculate total for average
    }
  }
  
  // Calculate the average of all matrix elements
  float average = total / (3 * 3);
  
  // Display the matrix and its average
  printf("Matrix values:\n");
  for (int row = 0; row < 3; row++)
  {
    for (int column = 0; column < 3; column++)
      printf("%d ", matrix[row][column]);
    printf("\n");
  }
  printf("Average of matrix elements: %.2f\n", average);
  return 0;
}
```

> *In this example, the program uses nested for loops to input values into a 3x3 matrix using scanf. It then calculates the average of all matrix elements and displays the matrix along with the calculated average.*
