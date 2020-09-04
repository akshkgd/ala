# Ala-Programming-Language

A small programming language created by Ashish Kumar Shukla.
## Overview

It supports various fundamental programming concepts such as variable-declaration, 
function calling, conditional statements, loops, proper order of operations, and recursion. 
The language syntax is meant to be very readable and intuitive: for instance, every 
function body, conditional statement body, and loop body is wrapped in colons; loops 
follow a "from [startingNumber] to [endingNumber] with [variable]" syntax; and variable types are
specified upon declaration. Below is the language's EBNF-based grammar, and following that are some examples of programs that the language can run. Even further down is a link to a repl.it where the programs can be run.

## Grammar

**program::=** variable-declaration | conditional | loop | expression [ program ]

**variable-declaration::=** variable-keyword variable-name assignment-operator variable-body  
**variable-keyword::=** "fn" | "num" | "str" | "arr" | "bool"  
**variable-name::=** identifier  
**assignment-operator::=** "="  
**variable-body::=** function-declaration | expression | comparison

**function-declaration::=** function-arguments wrapper function-body wrapper  
**function-arguments::=** "(" [ { expression "," } ] ")"  
**function-body::=** program

**conditional::=** "if" comparison wrapper program wrapper [ { "else if" ... } | "else" wrapper program wrapper ]

**comparison::=** expression [ comparison-operator expression ]  
**comparison-operator::=** "=="

**loop::=** "from" expression "to" expression "with" identifier wrapper program wrapper

**expression::=** term { "+" | "-" term }  
**term::=** factor { "\*" | "/" | "%" factor }  
**factor::=** number | string | boolean | array | identifier | "-" factor | "(" expression ")" | function-call  
**function-call::=** identifier "(" [ { expression "," } ] ")"  
**identifier::=** { letter }  
**number::=** { digit } [ "." { digit } ]  
**string::=** """ [ { * } ] """  
**array::=** "[" [ { expression "," } ] "]"  
**boolean::=** "true" | "false"

**letter::=** "a" | "b" | ... | "y" | "z" | "A" | "B" | ... | "Y" | "Z"  
**digit::=** "0" | "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9"

**wrapper::=** ":"

## Examples of Working Programs

### Interpreter Instantiation

```javascript
let Ala = new Interpreter(memory)
```

### Basic Variable Declaration

```javascript
Ala.input(`

	num one = 1
	num three = 3
	str hello = "hello"
	arr array = [1, 2, 3, 4, 5, 6, 7]
	fn add = (num a, num b) :
		=> a + b
	:
	fn echo = (num a) :
		=> a
	:
	
`)

Ala.memory
```

### Basic Function Calling

```javascript
Ala.input(`

	add(one, three) + add(echo(one), three)

`)
```

### Basic Conditional Statements

```javascript
Ala.input(`

	if 3 == 3 :
		print("First!")
	: elsif echo(one) == 1 :
		print("Second!")
	: else :
		print("Third!")
	:

`)
```

### Basic Loops

```javascript
Ala.input(`

	from 0 to 6 with i :
		num currentIndexValue = index(array, i)
		print(currentIndexValue)
	:

`)
```

### Nested Loops

```javascript
Ala.input(`

	from 1 to 3 with i :
		from 1 to 3 with j :
			from 1 to 3 with k :
				print(i, j, k)
			:
		:
	:

`)
```

### FizzBuzz

```javascript
Ala.input(`

	fn fizzBuzz = (num n) :
		from 1 to n with i :
			if i % 15 == 0 :
				print("FizzBuzz")
			: elsif i % 5 == 0 :
				print("Buzz")
			: elsif i % 3 == 0 :
				print("Fizz")
			: else :
				print(i)
			:
		:
	:

`)

Ala.input(`

	fizzBuzz(35)

`)
```

### Recursion and Fibonacci

```javascript
Ala.input(`

	fn fib = (num n) :
		if n == 1 :
			=> 0
		: elsif n == 2 :
			=> 1
		: else :
			=> fib(n - 1) + fib(n - 2)
		:
	:

`)

Ala.input(`

	from 1 to 15 with i :
		print(i, fib(i))
	:

`)
```

### Order of Operations

```javascript
Ala.input(`

	fn alwaysTwo = (num n) :
		=> ((((n + 47 % (19 * add(-3, 5))) * echo(three - one) - 4) / fib(4) - n + fib(echo(10)) - 29) * 3 - 9) / 3 - (((n + 109 % 10) * 2 - 4) / 2 - n)
	:

`)

Ala.input(`

	alwaysTwo(4751)

`)
```


