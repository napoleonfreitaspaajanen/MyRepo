---
title: C programming essentials
---
# Basics  
reference page: [Creference](https://en.cppreference.com/w/c)  

- Global variables can be defined by setting them outside of the main function  
- static local variables can be set with the word "static" and they will continue to accumulate during the whole program (i.e, they are not reset when the function is called again)  
- static global variables and functions (also with the word static) are only shown inside the c file they are defined.  
- Autocomplete with Ctrl-N and Ctrl-P

**Compiling**  

command: gcc -g -Wall -Wextra -std=c99 -o compiledName fileName.c  
- g for debugging  
- Wall for all warnings  
- Wextra for more warnings  
- std=c99 for the c standard  
- o compinedName for the name of the output file

**Generalities**  
- Commenting: can be done with `/*` and `*/`, or rest of line with `//`  
- Adding a library: #include <stdio.h>  
- Adding a math library: #include <math.h> and add -lm to compiler gcc

**Creating functions**
```c
int multiply(int first, int second){
  int res = first * second;
  return res;
}
```  
# Built-ins  
Short explanation of things that are built into the language.  
- sizeof: Returns the size of a data structure. Especially, one can write sizeof(short) or any other datatype. Note that the return type is size_t, which is equivalent to unsigned int (in printf, lu).  



# stdio library  

**IO**  

printf command is the basic print function.  
- first argument is a string to be printed.  
- Remember to use `\n` since it is not included in printf
- next arguments are variables to be substituted to locations by marked by %
- [%6.1f] sets 6 spaces for the number and uses one decimal. Brackets not needed.

| sign | variable |
| ---  |:--------:|
|%d| signed 16 bit int |
|%f| float 32 bits |
|%lf| double 64 bit|
|%c| characters|

# Flow control  
- and is &&, or is ||  

**If**  
```c
if (ret > 0) {
  doSomething
} else  if (ret < 0) {
  somethingElse;
} else {
  lastSomething;
}
```   

**switch**  
```c
switch(a) {
  case 'a':
    doSomething;
    break; // remember to break, otherwise it continues directly
  case 'b':
  case 'c': // Note that this takes in consideration both a and b
    doSomethingElse;
    break;
  default:
    doDefault;
    break;
}
```
**while**  
```c
while (a < 10) {
  a++;
}
// OR
do {
  a ++;
} while (a < 10);
```  

**for loop**  
```c
for (int a = 0; a < 10; a++) {
  doSomething;
}
```  
For comparison between the two methods, look at the following:  
```c
alustus;
while (ehto) {
  lause;
  toimenpide;
}

for (alustus; ehto; toimenpide){
  lause;
}
```

# Pointers and arrays  
The two basic operators of pointers are `&` and `*`.  
- `*` is used to create a pointer and as a deferencing or indirection operator  
- `&` is called the address-of operator and it yields the address of a variable  

The story is briefly the following:  
```c
#include <stdio.h>
int main(void){
  int var = 5; // var is a direct reference to 5, i.e., the variable name
  int * p_var = &var; // creates a pointer p_var to the value of var. & yields its address.
  printf("Get the value of var through pointer: %d", * p_var);
  // at this point p_var is a pointer, &p_var yields its address, &var is an address, and var represents a integer
}  
```  

Here are some examples of what is allowed:  
```c
void function(int* argument){} // Takes a pointer argument. If one wants to pass an array, this is also the way.
aPtr = (bPtr + 2) // assign a new pointer to the old
*(aPtr + 2) = * bPtr // Set the value behind 2 slots in front of pointer a to the value of pointer b

```

## Connection with arrays  
The basic syntax for an array:  

- int a[10]  

After this, `a` is a pointer to the first location a[0], so we can write for a integer pointer aPtr = a instead of aPtr = &a.  
Furthermore, * (aPtr + 1) is equal to aPtr[1].  
The difference between the two is that aPtr is a variable, so aPtr = a and aPtr++ are legal, whereas a = aPtr and a++ are not.  

A table can also be initialized as follows:
```c
short slots[5] = {1 ,5, 3, 5, 6};
int numbers[] = {2232, 434, 232}; // Number of elements is interpreted  
int numbers2[10] = {0}; // array of zeros: if less numbers given in curly, rest will be set to zero
int number3[5]; // This will not contain zeros, it will contain random numbers
```  

A table of pointer can be initialized as follows:  
char * array_name[max_elements];

# Memory allocation  
A C-programs memory is roughly divided into two categories: heap and stack. The stack contains the stack-frames for the functions, whereas the heap contains global variables and similar that need to be accessed throughout the program.  

Stack is a faster memory that is easier to use, whereas memory allocated in the heap must be controlled by the programmer, making it more dangerous by allowing things such as memory leaks (variables not deleted).  

There are, however, some valid reasons why to use the heap.  

- The heap allows for dynamic memory (e.g., a array that the programmer does not know the size of at compile time)  
- The heap allows for larger data to be stored.  

Basic functions for memory management are malloc, calloc, realloc, and free from the header <stdlib.h>.  

- void* malloc(size_t size) returns a pointer to a location in the heap of a given size. The pointer is for a void variable, and thus it must be changed. If malloc fails, it will return NULL  
-  void * realloc(void * ptr, size_t size) re-allocates memory for the pointer ptr. It must be thought as doing three things: reserve new space, copy old content or part of it, free old space. Thus the pointer location might change.  
- void * calloc(size_t count, size_t size) initializes count amount of space of size size, and initializes them with zero.

Example  
```c
int * p;
p = (int*)malloc(100 * sizeof(int)); // pointer of size 100 * int to heap. If it fails it returns NULL
if (p == NULL) {
  return -1; // memory allocation failed
}
int * newp = realloc(p, 200 * sizeof(int))
if (!newp) {
  free(p); // old pointer is still valid because reallocation failed
  return -1;
}
free(newp); // remember to free the memory as well! Has to be to the start of the allocation (i.e., the location that malloc gave)
```

**Working with memory**  
After memory has been allocated etc., one wants to work with the memory. These are some commands that can be used. These are included in <string.h>.  
- void * memcpy(void * destination, const void * source, size_t n) does a copy
- memmove is the same as the previous but allows overlapping memory  
- int memcmp(const void * mem1, const void * mem2, size_t n) compares two memory slots, returns 0 if equal and nonzero if not.  
- void * memset(void * mem, int c, size_t len) sets memory to a given value. C is a 8 byte value



# Types  
## Strings  
Strings are character arrays that end with the character `\0`. Thus we have the following:  
```c
char string[] = {'h', 'e', 'l', 'l', 'o'};
// Is the same than
char string[] = "hello"
// Is the same than
const char *string = "hello" // Note that  const is disnescessary but it will be immutable even without it.
// based on stackoverflow, char* is a mutable pointer to a mutable string
```   
The basic idea of const char is the following:  

- char * is mutable pointer to mutable char  
- const char * is a mutable pointer to a immutable char  
- char * const is a immutable pointer to a mutable char  
- const char * const is a immutable pointer to a immutable char

The basic way to go through strings is
```c
int function(const char * string){
  while (*string != '\0'){
    //do something
    string++; // set pointer forward
  }
}
```  

**Basic string functions**  
These can be found in #include <string.h>

- size_t strlen(const char * s)  
- strncmp(const char * s1, const char * s2, size_t n) and n can be dropped from name and the call. 0 if equal, neg if s1 before s2 in alphabetical ordering, and pos if s2 before s1.    
- strncpy(char * dst, const char * src, size_t n) n can be dropped. Remember to set n one over so that the 0 gets copied as well.  
- char * strncat(char * s1, const char * s2, size_t n) adds s2 behind s1 (max n letters, n can be dropped).  
- char * strchr(const char * s, int c) returns NULL if cannot find character c from char s.  
- char * strstr(const char * s1, const char * s2) returns Null if cannot find string s2 from s1

These can be found in <ctype.h>  

- int isalpha(int character)  
- int toupper(int c)


## Structured datatype  
Structured datatypes are like antecessors of object oriented programming. They allow to create a datatype that can contain variables, lists, and other structures. They should be generally places under a h file so that various c files can access them.  

Basic syntax:  
```c
struct Ship{
  char * name;
  float weight;
  char * cargo[10]; // list of strings
}; // note the semicolon here
```
When structures are given as arguments, they are copied to the stack frame so the original structure cannot be modified. To modify the original structure inside of the function, it is necessary to give the structure as a pointer.  
A the variables of a reference can be accessed with the arrow notation ->.  

```c
// with the previous ship structure
struct Ship my_ship = {"vessel", 1000, {"Iron", "Copper"}}; // probably works
struct Ship *reference = &my_ship;
reference->weight = 2000; // changes weight from 1000 to 2000
(* reference).weight = 3000; // changes weight to 3k, previous is syntactic sugar
```

## Typedef  
The command typedef can be used to alias a type to another name. This is often done when we have a type that is defined by a 'keyword tag name' combination (example is struct my_structure my_structure_name). When it is used in the declaration itself, then calling the type will not allow for 'keyword tag' calls. Examples next:  

```c
enum color {
  RED,
  GREEN,
  BLUE
};

enum color my_color = RED;
// color my_color = RED not allowed
```  

```c
typedef enum {
  RED,
  GREEN,
  BLUE
} color;

color my_color = RED;
// enum color my_color = RED not allowed
```  

```c
enum color {
  RED,
  GREEN,
  BLUE
};
typedef enum color color; // aliases enum color -> color
color my_color = RED;
enum my_second_color = BLUE;
// AND it is compatible with C++ code, since there we can use both
```
