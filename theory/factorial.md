# Experiment 11: To understand recursion in Prolog using factorial example.

## Theory:
In Prolog, following program has two clauses. The first clause has no body, and it is a unit clause. The second clause of Prolog has a body. On the right-hand side of '-', the body of the second clause exists. The symbol '-' will be read as "if". The body consists of literals and that literals can be separated using the commas ','. The symbol '.' will be read as "and". If the clause is a unit clause, then the head of the class will be the whole class. Otherwise, the part of the clause which appears to the left of the colon in ':-' will be the head of the class. The first clause (unit clause) is used to show that "factorial 0 is 1". The second clause is used to show that "factorial of N is F if N>0, N1 is N-1, the factorial of N1 is F1 and F is N*F1".

```text
                  factorial(3,6)
                   /     |     \
                 3>0   2 is 3-1  factorial(2,2)   6 is 3*2
                                  /     |     \
                                2>0   1 is 2-1  factorial(1,1)   2 is 2*1
                                                 /     |     \
                                               1>0   0 is 1-1  factorial(0,1)   1 is 1*1
                                                                  |
                                                                true
```

