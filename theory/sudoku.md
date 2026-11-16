# Experiment 4: To understand the concept of constraint propagation and finite domain using the sudoku problem.

## Theory:
A Sudoku puzzle can be considered a CSP with 81 variables, one for each square. We use the variable names A1 through A9 for the top row (left to right), down to I1 through I9 for the bottom row. The empty squares have the domain {1, 2, 3, 4, 5, 6, 7, 8, 9} and the prefilled squares have a domain consisting of a single value. In addition, there are 27 different Alldiff constraints: one for each row, column, and box of 9 squares.

Alldiff (A1,A2,A3,A4,A5,A6, A7, A8, A9)
Alldiff (B1,B2,B3,B4,B5,B6,B7,B8,B9)
・ ・ ・
Alldiff (A1,B1,C1,D1,E1, F1,G1,H1, I1)
Alldiff (A2,B2,C2,D2,E2, F2,G2,H2, I2)
・ ・ ・
Alldiff (A1,A2,A3,B1,B2,B3,C1,C2,C3)
Alldiff (A4,A5,A6,B4,B5,B6,C4,C5,C6)

