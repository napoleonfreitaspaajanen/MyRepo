---
title: C programming essentials
---
# Basics  
reference page: [Creference](https://en.cppreference.com/w/c)  

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
} while (a < 10)
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
The difference between the tru is that aPtr is a variable, so aPtr = a and aPtr++ are legal, whereas a = aPtr and a++ are not.  

A table can also be initialized as follows:
```c
short slots[5] = {1 ,5, 3, 5, 6};
int numbers[] = {2232, 434, 232}; // Number of elements is interpreted  
int numbers2[10] = {0}; // array of zeros: if less numbers given in curly, rest will be set to zero
int number3[5]; // This will not contain zeros, it will contain random numbers
```  
# Types  
## Strings  
Strings are character arrays that end with the character `\0`. Thus we have the following:  
```c
char string[] = {'h', 'e', 'l', 'l', 'o'};
// Is the same than
char string[] = "hello"
// Is the same than
const char *string = "hello" // Note that  const is disnescessary but it will be immutable even without it.
```

The basic way to go through strings is
```c
int function(const char * string){
  while (*string != '\0'){
    //do something
    string++; // set pointer forward
  }
}
```
