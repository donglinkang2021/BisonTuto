# Infix Notation Calculator

Modify rpcalc to handle infix operators instead of postfix.

- in `Bison declarations`
    - `%left` declares token kinds and says they are left-associative operators

- `Operator precedence` is determined by the line ordering of the declarations;
    - the higher the line number of the declaration
    - the higher the precedence

- in `grammar section`
    - `%prec`
        - specifies the precedence of a rule
        - `| - exp` has the same precedence as `NEG`