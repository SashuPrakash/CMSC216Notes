# Lecture 6 - 6/7/2022

Today, the TA is lecturing

## Pointer Arithmetic 

* Pointer arithmetic only makes sense when the pointers are referring to a countinuous chucnk of memory (eg., array)
* Only valid forms of pointer arithmetic
    * `pointer1 - pointer2` (Subtracting two pointer values)
    * `pointer +- integer` (Adding or subtracting an integer)
* When a pointer is incremented/decremented by an integer we move the pointer to the next/previous element
    * How many bytes are skipped depends on the size of the type to which the pointer points
* Indexing is a pointer operation (`pointer +- integer`)
    * `data[i]` -> `*(data + i)`
* When two pointers are referring to the same array, we cand eterming how far apart ehy are by subtracting the pointers

### Example: `pointer_ops.c`

Take a look at this example code:

``` c
int main() {
   int data[] = {10, 20, 30, 40};
   /* Is there a simpler way to initilize pid0? */
   int *p0 = &data[0], *p3, *p4;
   int age = 78, *age_ptr = &age;

   p3 = data + 3;
   p4 = data + 4;
   printf("*p0: %d, *p3: %d\n", *p0, *p3);
   p0++;
   printf("*p0 after p0++: %d\n", *p0);
   printf("p0[1]: %d\n", p0[1]); /* Indexing is pointer op */
   printf("*(p0 + 1): %d\n", *(p0 + 1)); /* Indexing is pointer op */

   printf("Difference p3 - p0: %ld\n", p3 - p0);
   printf("Difference Two p0 - p3: %ld\n", p0 - p3);
   printf("Negative index p4[-2]: %d\n", p4[-2]); /* BAD */

   /* Shows indexing is a pointer, not an array operation */
   printf("age_ptr[0]: %d\n", age_ptr[0]);  /* How about age_ptr[1]? */

   return 0;
}
```