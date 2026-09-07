# BanglaBhasha Compiler

A Bengali programming language compiler developed in Python as an academic project for the **Compiler Design and Construction Sessional** course.

BanglaBhasha allows programmers to write source code using Bengali syntax and keywords. The compiler processes the source through standard compiler phases including lexical analysis, syntax analysis, semantic analysis, intermediate code generation, and target code generation.

The current implementation generates executable **Python code** as its target output.

## Compiler Pipeline

```text
BanglaBhasha Source Code
          |
          v
        Lexer
          |
        Tokens
          |
          v
        Parser
          |
         AST
          |
          v
  Semantic Analyzer
    + Symbol Table
          |
          v
         TAC
  (Three-Address Code)
          |
          v
    Python Backend
          |
          v
   Generated Python
          |
          v
      Execution

The implementation is organized into actual compiler phases rather than performing simple Bengali-to-Python keyword replacement.

Project Structure
BanglaBhasha_Compiler/
│
├── bangla_compiler.py
├── BanglaBhasha_Compiler.ipynb
└── README.md
bangla_compiler.py

Contains the complete compiler implementation.

BanglaBhasha_Compiler.ipynb

Jupyter/Google Colab version of the compiler, organized so that different compiler phases can be demonstrated separately.

README.md

Project documentation and usage guide.

Implemented Features
Lexical Analysis

The lexer recognizes:

Bengali/Unicode identifiers
Integer literals
Floating-point literals
String literals
Boolean literals
Arithmetic operators
Comparison operators
Logical operators
Assignment operator
Parentheses
Braces
Commas
Semicolons
Bengali keywords
Comments
End-of-file token
Data Types

BanglaBhasha supports:

Integer
Float
Boolean
String

The compiler also uses internal semantic categories such as:

list
stack
queue
void
error
Variable Declaration

The compiler supports:

Explicit declaration
Declaration without initializer
Type-inferred declaration
Assignment

Assignment statements are supported with semantic type checking.

Compatible numeric widening is supported where applicable, while incompatible assignments generate semantic errors.

Output

BanglaBhasha provides an output statement that is translated into Python's:

print(...)
Arithmetic Operators

Supported arithmetic operators include:

+
-
*
/
%

The parser implements operator precedence.

Comparison Operators

The compiler supports comparison expressions that produce Boolean results.

Boolean Values and Logical Operators

Boolean values and logical operators are supported:

AND
OR
NOT
IF-ELSE

Conditional statements are supported using IF-ELSE structures.

WHILE Loop

The compiler supports WHILE loops for repeated execution based on a Boolean condition.

Break

A break statement is supported for terminating loops.

The semantic analyzer checks whether break is used inside a valid loop context.

Functions

BanglaBhasha supports user-defined functions.

Implemented capabilities include:

Function declaration
Parameters
Function calls
Return statements
Return types

Functions are translated into equivalent Python functions.

Classes and Objects

The compiler includes a basic class and object system.

Supported concepts include:

Class declaration
Class fields
Methods
Object creation
Member access
Method calls
Member assignment
Object reference

The current implementation focuses on a simple educational OOP model.

Stack

A built-in stack abstraction is included in the generated Python runtime.

Supported operations include:

Push
Pop
Top/Peek
Empty checking

The stack follows:

LIFO — Last In, First Out
Queue

A built-in queue abstraction is also included.

Supported operations include:

Enqueue
Dequeue
Front
Empty checking

The queue follows:

FIFO — First In, First Out
Lists

List literals are supported by the compiler.

Bengali Unicode Identifiers

BanglaBhasha supports Bengali/Unicode identifiers, allowing programmers to use Bengali names for variables and supported identifiers.

Comments

The lexer recognizes supported comment syntax and prevents comments from being treated as executable statements.

Error Handling

The compiler handles errors across multiple compiler phases.

Lexical Errors

Detects invalid or unknown characters.

Syntax Errors

Detects invalid token sequences and malformed language structures.

The parser provides syntax recovery for supported syntax errors.

Semantic Errors

The semantic analyzer detects problems such as:

Type mismatches
Invalid assignments
Invalid use of language constructs

Target Python code is not generated when unresolved compiler errors remain.

Three-Address Code (TAC)

BanglaBhasha generates an intermediate representation based on Three-Address Code (TAC).

For example:

t1 = b * 4
t2 = a + t1

The TAC representation demonstrates the intermediate-code-generation phase of compiler construction.

The TAC generator supports representations for:

Assignments
Arithmetic operations
Unary operations
Conditional jumps
Labels
Function calls
Returns
Functions
Classes
Object creation
Stack/queue operations
Method calls
Break operations
Python Target Code Generation

After successful analysis, the compiler backend converts the validated AST into Python source code.

The generated Python source also includes runtime definitions required by built-in BanglaBhasha features such as stack and queue.

Python is currently the target language of the compiler.

Compiler API

The main compiler function is:

compile_source(source)

A convenience function is also provided for compiling and executing source code:

run_source(source)

The compiler can expose information such as:

Tokens
AST
Semantic Analysis
TAC
Generated Python

This makes the individual compiler phases easier to inspect during academic demonstrations.

How to Run
Google Colab / Jupyter Notebook

Open:

BanglaBhasha_Compiler.ipynb

Run the notebook cells and provide or modify the BanglaBhasha source program.

Python File

Python 3 is required.

Example:

from bangla_compiler import compile_source, run_source

source = """
# BanglaBhasha source code
"""

result, output = run_source(source)

if result.success:
    print(output)
else:
    print(result.errors)
Compilation Result

The compilation result stores information generated during the compilation process, including compiler output and diagnostic information.

Compilation succeeds when no unresolved compiler errors remain.

Otherwise, the compiler reports the detected errors.

Current Scope and Limitations

BanglaBhasha is an educational compiler developed for a Compiler Design course rather than a production programming language.

The current implementation does not provide several production-language features, including:

Inheritance
Constructors with arguments
Access modifiers
Exception handling in the Bangla language
Advanced for loops
Switch/case
General file indexing
Full multidimensional structures
A full standard library
Static method support
Method overloading
Full function argument type checking
Separate machine-code/runtime implementation

These limitations keep the project focused on demonstrating core compiler construction concepts.

Design Rationale

The project follows classical compiler concepts:

Lexical Analysis
        ↓
Syntax Analysis
        ↓
Abstract Syntax Tree
        ↓
Semantic Analysis
        ↓
Intermediate Representation
        ↓
Target Code Generation
        ↓
Execution

BanglaBhasha syntax serves as the user-facing language while Python serves as the target language.

Project Status
Core Compiler Requirements
 Multiple data types
 Type checking
 Arithmetic operations
 Operator precedence
 Assignment
 IF-ELSE
 WHILE
 Syntax error recovery
 Graceful compiler errors
 Executable Python target generation
Advanced Features
 Functions
 Return statements
 Classes
 Objects
 Stack
 Queue
 Boolean operators
 Lists
 Break
 Bengali Unicode identifiers
 Comments
Academic Context

Course: Compiler Design and Construction Sessional

Project: BanglaBhasha Compiler

Implementation Language: Python

Target Language: Python

Project Type: Academic Compiler Construction Project

The project demonstrates the practical implementation of major compiler-design concepts through a Bengali-oriented programming language.

Author

Md. Emad Uddin Khan Sahabi

B.Sc. in Computer Science & Engineering
Leading University

Portfolio: https://sahabi.ami.bd
GitHub: https://github.com/Sahabi80
License / Academic Use

This project was developed for academic and educational purposes as part of a Compiler Design and Construction Sessional course.
