# Lecture 2 - 6/1/2022

## Introduction

At this point, you should have run the setup command.
* This will give you the `216` and `215public` directories.
    * the `216public` directory is read-only, so students cannot change it.

When you connect to Grace, you will see a number next to `Grace` such as `grace3:`. This number represents the specific host within the cluster to which you have connected.

## Copying Things 

This command copies the `Week01` directory from the `216public` directory to our own `216` directory in our home directory.

``` bash
cp -r ~/216public/lecture_examples/Week01/ ~/216
```

* `cp` is the copy command.
* `~` (tilde) represents the home directory.
* `-r` means recursive
* `~/216public/lecture_examples/Week01/` is what we want to grab.
* `~/216` is where we want to put it.

Note: pressing tab after typing the beginning of a word or command will autocomplete it. It will even autocomplete using the names of the contents which you can access.

## Removing things

This command removes the `Week01` and everything in it.

``` bash
rm -r Week01
```

To bypass all the confirmations, use `-F`.

## Moving things

Suppose we want to move things from a directory `old` to `old2`.

The command `mv` moves things.

``` bash
mv old old2
```

## Typing in files

To type in a file, we can simply use an editor such as vi, vim, or nano. For example, we can type in a file called `p1.c` by using 

``` bash
vi p1.c
```
Then we can simply type code such as this:

``` c
#include <stdio.h>

int main() {

}
```

* Save a file using escape, `shift`+`:`
* Write the file using `w`.
* Quit the editor using `q`.

Often, we will write and quit so we just do `wq` in vim.

## Class Website

On the class website, you can see resources by going to the dropdown menu. Here, you will find all the Linux commands you will need for this class.

## Aliases

When one wants to compile code in this class, we must use `gcc` with many flags like this:

``` bash
gcc -ansi -Wall -g -O0 -Wwrite-strings -Wshadow -pedantic-errors -fstack-protector-all -Wextra p1.c
```

This is a rediculous amount of flags to write, so we can create an alias for `gcc` such that whenever we use `gcc`, all those flags are used. To do this, follow the instructions [here](http://www.cs.umd.edu/~nelson/classes/resources/setting_gcc_alias/).

## C

Let's take a look at `print example` in `C-Language-II-Code` in `216public`.

``` c
#include <stdio.h>

int main(void) {   /* Notice the void to indicate no parameters */
   int age = 18;
   float salary = 100.50;
   char gender = 'F';
   const char *address = "AV Williams Bld";

   printf("Age: %d, Salary: %f, Gender: %c\n", age, salary, gender);
   printf("Address: %s\n", address);

   return 0;
}
```

The line

``` c
printf("Age: %d, Salary: %f, Gender: %c\n", age, salary, gender);
```

is a formatted string. 

Next, let's look at the program `reading.c`.

In this code, there is `%c` and `%d` for input.
* `%d` skips/ignores all spaces and newlines.
* `%c` inludes spaces and newlines

## scanf() conversion specifiers

* `%d`, `%x`, `%o`
    * Reads a decimal, hex, or octal number into an `int`
* %f reads in a `float`
* %lf reads in a `double`
* %ld reads in a `long`
* %c reads in a `char`
* %s reads in a `string` (bounded by whitespace)

## Naming Convention in `C`

In C, we don't use camelCase by convention. Instead, we separate words with underscores. Instead of `letterGrade`, we would use `letter_grade`.