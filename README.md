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


Test it live here: https://repl.it/@AshishKumar53/Ala#index.js
