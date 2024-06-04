# Reverse Polish Notation Calculator

## Declarations for `rpcalc.y`

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

## Grammar Rules for `rpcalc`

- groupings
    - `input`
    - `line`
    - `exp`
- Each of these nonterminal symbols 
    - has several alternate rules, 
    - joined by the vertical bar ‘|’ (or)
- semantic values
    - pseudo-variable `$$` stands for semantic value for the grouping
    - semantic values of the components of the rule are referred to as $1, $2 ...

```bison
input:
  %empty
| input line
;
```

> A complete input is either an empty string, or a complete input followed by an input line

- left recursive
    - makes this rule into a loop


```bison
line:
  '\n'
| exp '\n'      { printf ("%.10g\n", $1); }
;
```

- `\n` means that rpcalc accepts a blank line
- `exp '\n'` means that rpcalc accepts an expression followed by a newline

```bison
exp:
  NUM
| exp exp '+'   { $$ = $1 + $2;      }
| exp exp '-'   { $$ = $1 - $2;      }
| exp exp '*'   { $$ = $1 * $2;      }
| exp exp '/'   { $$ = $1 / $2;      }
| exp exp '^'   { $$ = pow ($1, $2); }  /* Exponentiation */
| exp 'n'       { $$ = -$1;          }  /* Unary minus   */
;
```

more readable
