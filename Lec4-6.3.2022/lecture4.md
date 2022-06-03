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

