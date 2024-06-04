# Simple Error Recovery

```bison
line:
  '\n'
| exp '\n'   { printf ("\t%.10g\n", $1); }
| error '\n' { yyerrok;                  }
;
```

The program can still run after an error, but the error message is not very helpful.

```bash
linkdom@ubuntu:~/Desktop/BisonTuto/examples/03$ ./run.sh 
1+@
syntax error
1+2
3
3
3
2^5
32
exit
syntax error
```