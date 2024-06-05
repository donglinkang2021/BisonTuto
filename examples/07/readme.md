# Minimal CPP Flex Bison Project

- Write scanner `src/parse/scan.ll`, you can declare:
  - Named regex (follow the example of `blank` and `eol`)
  - Flex options
  - Stacks to simulate contexts (useful for comments for example)
  - Tokens and associated code, one by line `{blank}  { /* C++ code goes here */ return TOKEN; }` (TOKEN will be caught by Bison that will try to match it with the grammar)
- Write parser `src/parse/parse.yy`, you can declare:
  - Tokens (names and types, they will be used both in `scan.ll` and `parse.yy`)
  - Bison options
  - Precedance rules
  - Grammar
  - Customize error reporting using the `error()` function
- Interact with parser through the driver, as is shown in `main.cc`
  - Include `driver.hh`
  - Create a `Driver` object
  - Use one of `parse()` or `parse_file()` functions (read from stdin and a file respectively)