# Multi-Function Calculator

```bash
pi
⇒ 3.141592654
sin(pi)
⇒ 1.224646799e-16
alpha = beta1 = 2.3
⇒ 2.3
alpha
⇒ 2.3
ln(alpha)
⇒ 0.8329091229
exp(ln(beta1))
⇒ 2.3
```

> Add memory to the calcuator.

- two new features
- `%define api.value.type union`
    - the symbols are defined with their data types 

```bison
%token <double>  NUM     /* Double precision number. */
%token <symrec*> VAR FUN /* Symbol table pointer: variable/function. */
%nterm <double>  exp
```

- `%nterm` for declaring nonterminal symbols

add the following line to enable debugging

```bison
%define parse.trace
```

you can use `./mfcalc -p` to see the trace

```bash
Starting parse
Entering state 0
Reducing stack by rule 1 (line 24):
-> $$ = nterm input ()
Stack now 0
Entering state 1
Reading a token: pi
Next token is token VAR ()
Shifting token VAR ()
Entering state 5
Reading a token: Next token is token '\n' ()
Reducing stack by rule 7 (line 36):
   $1 = token VAR ()
-> $$ = nterm exp ()
Stack now 0 1
Entering state 10
Next token is token '\n' ()
Shifting token '\n' ()
Entering state 22
Reducing stack by rule 4 (line 30):
   $1 = nterm exp ()
   $2 = token '\n' ()
⇒ 3.141592654
-> $$ = nterm line ()
Stack now 0 1
Entering state 11
Reducing stack by rule 2 (line 25):
   $1 = nterm input ()
   $2 = nterm line ()
-> $$ = nterm input ()
Stack now 0
Entering state 1
Reading a token: ^C
```