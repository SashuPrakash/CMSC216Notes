# Lecture 4 - 6/3/2022

## Shooting an `xterm`

By running the command:

``` bash
xterm &
```

You will see that a new window shoots so you can have another window to work with grace.

## Types in C

There are differnt types in C, each with different numbers of bytes. The number of bytes can be different depending on the environment that the program is compiled and run on.
* The only type with a consisted number of bytes is `char`.

Warning from Nelson: "Do not randomly cast types unless you know what you're doing"

### Example: `mixed_types_1.c`

Take a look at this code:

``` c
#include <stdio.h>

int main() {
   int x = 2000000000; /* value fits in x */
   long result_long;

   printf("Value of x: %d\n", x);
   printf("Multiplying by 3 (with %%d format): %d\n", 2000000000 * 3);
   printf("Multiplying by 3 (with %%ld format): %ld\n", 2000000000 * 3);
   printf("Multiplying by 3L (with %%d format): %d\n", 2000000000 * 3L);
   printf("Multiplying by 3L (with %%ld format): %ld\n", 2000000000 * 3L);

   result_long = 2000000000 * 3;  /* Does it solve the problem? */
   printf("Storing result in long type variable: %ld\n", result_long);

   return 0;
}
```

``` js
// revisit 2:12 PM
```

### Example: `mixed_types_1.c`

Take a look at this code:

``` c
#include <stdio.h>

int main() {
   unsigned int value = 250;  /* try with 250 and 4000000000 */

   printf("\nType sizes\n");
   printf("sizeof(unsigned int): %ld\n", sizeof(unsigned int));
   printf("sizeof(int): %ld\n", sizeof(int));
   printf("sizeof(long): %ld\n\n", sizeof(long));

   printf("value: %u\n", value);
   printf("(int)value: %d\n", (int)value);
   printf("(long)value: %ld\n", (long)value);

   printf("(int)value / 4: %d\n", (int)value / 4);
   printf("value / 4: %d\n", value / 4);

   return 0;
}
```

``` js
// revisit
```

### Example: `mixed_types_3.c`

Take a look at this example code:

```c
#include <stdio.h>
#include <string.h>

static void process(const char *str) {
   size_t k, value = 2;
   size_t delta = strlen(str) - value; /* problem: possible negative */
   int answer_is_yes;                  /* value assigned to delta (unsigned) */
   char c;

   printf("Delta value: %ld\n", delta);
   printf("Enter \"yes\" to continue: ");
   answer_is_yes = scanf("ye%c", &c);
   if (answer_is_yes == 1) {
      for (k = 0; k < delta; k++) {
         printf("In loop %ld\n", k);
      }
   }
}

int main() {
  process("house");   /* problem when using "a" */

  return 0;
}
```

## Switching Between Clusters

You can switch from one cluster by `ssh`ing to another node within the Grace cluster. This may help if there are many people on one node

## The `sizeof` operator
* Unary **operator**, evaluates to the number of bytes necessary to hold its operand
* Operand can be an expression or a type name
    * It does NOT evaluate the expression
* Examples:
  ```
  int i = 5;
  printf("%ld\n", sizeof(i));
  printf("%ld\n", sizeof(unsigned char));
  printf("%ld\n", sizeof(++i));
  printf("%d\n", i);
  ```

## Pointers

* Pointer -> memory address, address, reference are equivalent terms
* **Pointer variable** -> Variable whose value is an address
    * Informally we call a pointer variable a pointer, but that can be misleading (similar to calling an integer variable an integer)
* A **pointer variable** has a fixed number of bytes as an address in a system has a fixed number of bytes
* A **pointer variable stores** the address of the first byte of an int, float, double, etc. Not the whole address; just the address of the first bye
* **Let’s see a diagram**
* A pointer variable is defined as follows:
  ```js
  <TYPE><ZERO_OR_MORE_SPACES>*<ZERO_OR_MORE_SPACES><VARIABLE_NAME>;
  ```
* Example: `int*ip;`
    * Creates a variable called ip whose type is "pointer to int“
* All the following are equivalent:
  ```c
  int*p; /* no spaces */
  int* p; /* helps emphasize p is a “variable that stores address of int */
  int * p;
  int *p; /* the one we prefer */ /* see man 3 scanf in linux */
  ```
* Obtaining the address of an lvalue (&)
    * Placed before a variable (or an lvalue)
    * **Returns the address of the first byte**
* Accessing the entity at an address (*)
    * Placed before an expression which is either a pointer variable or otherwise evaluates to a pointer
    * **Returns the entity that lives at the specified address**
    * Confusing as same symbol (*) used to define a variable as a pointer variable and to dereference

### Example: `reading.c`

Take a look at this code that shows the usage of pointers

```c
#include <stdio.h>

int main() {
   int age, values_read;
   int* age_ptr = &age;
   float salary;

   printf("Enter your age and salary (using <age>-<salary> format): ");

   /* This example shows we don't always use & in variables of a scanf */
   values_read = scanf("%d-%f", age_ptr, &salary);
   if (values_read != 2) {
      printf("Invalid data provided\n");
   } else {
      printf("Provided values Age: %d, Salary: $%.2f\n", age, salary);
   }

   return 0;
}
```