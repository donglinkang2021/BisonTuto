| code | description |
| ---- | ----------- |
| `/* Reverse Polish Notation calculator. */` | Comment |
| `%{` | Prologue start |
| `#include <stdio.h>` | Include standard I/O library |
| `#include <math.h>` | Include math library, used to include the `pow` function |
| `int yylex (void);` | Declare the lexer function |
| `void yyerror (char const *);` | Declare the error function |
| `%}` | Prologue end |
| `%define api.value.type {double}` | thus specifying the C data type for semantic values, {int} is default, each token and each expression has an associated value, which is a floating point number. C code can use `YYSTYPE` to refer to the value `api.value.type`|
| `%token NUM` | Define the token `NUM` |
