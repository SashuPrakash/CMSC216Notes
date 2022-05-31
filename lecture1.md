# Lecture 1 - 5/31/2022

## Using grace
 
 * "Eclipse died" - Nelson
 * Command Line Interfaces (CLIs), are used everywhere in development, so it is good to know.

## Folders
* In the host `grace.umd.edu`, there are several folders, one of which is your account which was set up using the link in Nelson's email.
* In your account folder, there is a `216` folder in which you can put your projects for this class.

## Linux Commands
* Create directory by using [`mkdir <example>`] where `<example>` is the name of the folder you want to make.
    * `mkdir` stands for  "make directory" 
* Go into a folder by using [`cd <folder>`] where `<folder>` is the name of the folder you want to go into
* Go back to the home folder by using [`cd`]
* List everything in a folder using [`ls`]
    * `ls -F` puts a `/` next to everything that is a folder
* copy: `cp -r <directory/of/file/or/folder/fileOrFolderName> <newDirectory>`
    * `-r` means recursive, so it will copy everything

## Nano
* `nano` is a file editor in Grace.
* open `nano` using [`nano <filename>`], where `<filename>` is the name of the file you wish to edit. If the file doesn't exist, nano will create the file in the current directory.
* all commands in `nano` is shown at the bottom of the window.
    * the symbol `^` represents `ctrl`. For example, the command "`^X`" means "`ctrl+X`" to exit nano.

## Multiple Windows
* you can connect to Grace multiple times

## Compiling code
* the tool `gcc` compiles the code. Use it by using [`gcc <codeName>`] where `<codeName>` is the name of the file which contains your code.
* `gcc` will output to a file called `a.out`. This file is the exacutable that `gcc` compiled. You can run this executable by typing `a.out`.

## `C`

This example `C` program called `p2.c` shows some basic commands of a `C` program.

``` C
# include <stdio.h> 

int main (void) {
    int x, y;
    float m = 3.75;
    char letter = 'a';

    x = 10;
    printf("The value to print is %d and %f and %c\n", x, m, letter);

    i = 1;
    while ( i <= 5) {
        printf("Johnny and Amber\n")

        i++;
    }

    if (i == 6) {
        done = 1;
    } else {
        done = 0;
    }

    if (done) {
        printf("yes, we are done\n");
    } else {
        printf("NOOOOOOOOOOOOO we are done\n");
    }

    return 0;
}

```
* `if` statements are like Java
* `while` loops are like in Java
* `do-while` loops are like in Java
* there is no `boolean` type. In `C,` `0` is false, anything else is true.
* different compilers initialize uninitialilzed variables to different random variables. 