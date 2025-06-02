---
{"dg-publish":true,"permalink":"/content-folders/javascript/java-script-from-zero/","dgShowToc":true}
---

# Index

```table-of-contents
title: 
style: nestedList # TOC style (nestedList|nestedOrderedList|inlineFirstLevel)
minLevel: 0 # Include headings from the specified level
maxLevel: 0 # Include headings up to the specified level
includeLinks: true # Make headings clickable
debugInConsole: false # Print debug info in Obsidian console
```

1. Use console.log() to print something on to the console

# Introduction to variables

- Variables are used to store values that may vary and are case sensitive.
- var_name = value; is the general format used to create a variable.
- Using 'var' keyword is not mandatory unless the programmer uses "use strict" option in the first line of the file which enables strict validation.
- var keyword can be skipped when overwriting the value of a variable.
- With "use strict" : var var_name = value;

## Rules for naming variables

1. Variable names cannot start with numbers.
2. Only underscore and dollar symbols are allowed.
3. Spaces are not allowed.
4. Must not be a keyword.

> Convention : Use camelCase for naming variables.

## Using 'let' keyword

- 'let' keyword is used to create a variable.
- Using 'let' instead of 'var' has it's own advantages which will be discussed in later parts of the notes.
- 'let' can be used only when creating and assigning value to the variable but not when editing or overwriting the value of the variable.
- Mostly, programmers use 'let' over 'var' due to it's advantage in scope which is discussed in the [[#Block scope v/s function scope]] part of the notes.

# Introduction to constants

- Constants are those values that do not change.
- 'const' keyword is used to create a constant.
- Unlike variables, a constant cannot be overwritten or edited.

# Introduction to strings

```js
let name = "Archith";
```

| A   | r   | c   | h   | i   | t   | h   |
| --- | --- | --- | --- | --- | --- | --- |
| 0   | 1   | 2   | 3   | 4   | 5   | 6   |

- Strings are indexed from 0. 
- console.log(name[0]) prints the character at index 0 of the string.
- console.log(name.length) prints the length of the string stored in the variable 'name'.
- Last index of the string can be accessed using 'length-1'
- Length counts spaces too.

## trim() method

- trim() method is used to remove unnecessary spaces at the beginning and end of the string.
- Since strings are immutable, the result of the trim() method is a new string and must be stored to a variable. (Either the same variable as the existing string or a new one).

```js
let name = "    Archith     ";
name = name.trim() //assigning to the same variable
let name2 = name.trim() //assigning to a new variable
```

## toLowerCase() & toUpperCase() methods

- Similar to [[#trim() method]] discussed above, these methods create a new string and will need to be stored to a variable.
- Yet, storing or assigning the output of these methods is not mandatory. The output can be directly used in other functions or operations3.

## slice() method

- slice() method is used to access a part of the given string.
- slice() method takes two arguments, namely the start index and the end index : slice(start_index, end_index);
- The method always considers characters up to end_index - 1th index.
- slice(start_index) considers all the characters from the start_index through the last index of the string
- The output of this method must be stored to a variable or can be directly used for further processing by nesting.

# Introduction to datatypes

Some of the primitive datatypes in JS include:

- String
- Number
- Boolean
- Undefined
- Null
- BigInt
- Symbols

JS resolves the datatypes of variables and constants automatically and hence does not require explicit declaration unlike C/C++ or Java.

## typeof operator

- The 'typeof' operator is used to find the datatype of a variable declared in the program.

```js
let age = 19;
let name = "Archith";
console.log(typeof age) //logs 'number'
console.log(typeof name) //logs 'string'
console.log(typeof 19) //logs 'number'
console.log(typeof "Archith") //logs 'string'
```

## Converting a number to string

let age = 19;

Here, variable 'age' is a number. To convert it to a string, append an empty string to the variable. 

```js
let age = 19;
let age1 = 19 + "";
```

> The length of the new variable does not change unless a space is added between the double quotes.

## Converting a string to number

let num = "19";

Here, num, with it's value enclosed in double quotes, is a string. To convert it into a string, just prefix a '+' symbol. 

```js
let num = "19";
let num1 = +"19";
```

The variable 'num1' is now a number.

### Alternative methods

- To convert a number into string, one can use String() method. 

```js
let age = 19;
let age1 = String(age);
```

- To convert a string into number, one can make use of Number() method.

```js
let num = "19";
let num1 = Number(num);
```

## String concatenation

```js
let firstname = "Archith";
let lastname = "Chinnadamane";
console.log(firstname + " " + lastname); //logs 'Archith Chinnadamane'
```

> When operating on numbers stored as strings, it is crucial to convert them to numbers.

```js
let string1 = "17";
let string2 = "10";
console.log(string1 + string2); //logs 1710
console.log(+string1 + +string2); //logs 27
```

The extra '+' symbols prefixed to the names of both variables convert them to numbers.

## Template string

- Concatenation of strings takes too much efforts and makes the code too lengthy and messy.
- Programmers can use template strings to avoid this.
- Backticks and dollar symbols are used in template string definitions

```js
let aboutMe = `My name is $name and my age is $age`;
console.log(aboutMe);
```

> Backticks can be found just below the 'escape' button on a keyboard, alongside the tilde (~) symbol.

- The dollar ($) symbol is used to access the value of the variables. Not using a dollar symbol will just log the variable name as if it were a part of the string.

## The 'undefined' datatype

- Any variable that is created or declared but not initialized or not assigned with a value becomes undefined.

```js
let name;
console.log(typeof name) //logs 'undefined'
```

> A constant cannot be undefined (throws error is left undefined).

## The 'null' datatype

- 'null' means nothing.

```js
let name = null;
console.log(typeof name); //logs 'null'
```

>console.log(typeof null) logs 'object' which is a glitch in javascript. The datatype of 'null' is 'null'.


# Comparison operators

These operators return Boolean true or false.

- Greater than - >
- Lesser than - <
- Greater than or equal to - >=
- Lesser than or equal to - <=

Usage of these operators in JavaScript is similar to that in other programming languages.

> == versus ===
> 
> The == operator compares only the value and not the datatype. i.e 10, which is an integer is similar to "10" which is a string.
> Whereas === operator checks for both value and datatype.

> != versus !==
> 
> The != operator compares only the value and not datatype while !== checks for both.

> truthy and falsy values
> 
> *Truthy values :* Any value that has a meaning
> *Falsy values :* Null, Undefined, " ", false, 0

# if and else statements

```js
if (condition){
	statements for true part;
}
else {
	statements for false part;
}
```

# Ternary operator (Conditional operator)

Ternary operators are advanced if-else statements with both if and else parts defined in a single statement. 

A conventional if-else block :

```js
if (age >= 5){
	drink = "Coffee";
}
else{
	drink = "Milk";
}
```

The same example can be written using ternary operator as follows :

```js
let drink = age >= 5 ? "Coffee" : "Milk";
```

> General format or a ternary or conditional operator can be written as :
> 
> condition ? "True part" : "False part";


# && and || operators

Boolean AND and OR are represented using && and || respectively.

The usage of these operators are similar to that in other languages.


# Nested if-else statements

Also called if-else ladder, includes multiple if-else statements nested inside each other and are implemented just as in other programming languages.


# Switch statement

An alternative to if-else statements, mostly used when there are many possibilities, is a switch statement.

```js
switch (variable){
case ' ' :
	statement;
case ' ' : 
	statement;
case ' ' : 
	statement;
default :
	statement;
}
```


# while loops

A while loop is used to repeatedly execute a task as long as a condition is true.

```js
while (condition){
	statements to be executed;
	increment loop variable;
}
```


# for loops

For loops are used when the terminating condition is known.

```js
for (let i=0; i<=10; i++){
	statements to be executed;
}
```


# break and continue statements





---
*Created : .*
*Last Modified : .*