```prolog
% Sudoku Solver using CLPFD
% Run:
% ?- problem(1, Rows), sudoku(Rows), maplist(portray_clause, Rows).

:- use_module(library(clpfd)).

% Main Sudoku Solver
sudoku(Rows) :-
    length(Rows, 9),
    maplist(same_length(Rows), Rows),

    append(Rows, Vs),
    Vs ins 1..9,

    % Each row contains different values
    maplist(all_distinct, Rows),

    % Each column contains different values
    transpose(Rows, Columns),
    maplist(all_distinct, Columns),

    % Divide rows for 3x3 blocks
    Rows = [As,Bs,Cs,Ds,Es,Fs,Gs,Hs,Is],

    blocks(As, Bs, Cs),
    blocks(Ds, Es, Fs),
    blocks(Gs, Hs, Is),

    % Assign values to variables
    labeling([ffc], Vs).


% Check 3x3 blocks
blocks([], [], []).

blocks([N1,N2,N3|Ns1],
       [N4,N5,N6|Ns2],
       [N7,N8,N9|Ns3]) :-

    all_distinct([
        N1,N2,N3,
        N4,N5,N6,
        N7,N8,N9
    ]),

    blocks(Ns1, Ns2, Ns3).


% Problem 0
problem(0, [
    [_,_,_,_,_,_,_,_,_],
    [_,_,_,_,_,3,_,8,5],
    [_,_,1,_,2,_,_,_,_],
    [_,_,_,5,_,7,_,_,_],
    [_,_,4,_,_,_,1,_,_],
    [_,9,_,_,_,_,_,_,_],
    [5,_,_,_,_,_,_,7,3],
    [_,_,2,_,1,_,_,_,_],
    [_,_,_,_,4,_,_,_,9]
]).


% Problem 1
problem(1, [
    [1,_,_,8,_,4,_,_,_],
    [_,2,_,_,_,_,4,5,6],
    [_,_,3,2,_,5,_,_,_],
    [_,_,_,4,_,_,8,_,5],
    [7,8,9,_,5,_,_,_,_],
    [_,_,_,_,_,6,2,_,3],
    [8,_,1,_,_,_,7,_,_],
    [_,_,_,1,2,3,_,8,_],
    [2,_,5,_,_,_,_,_,9]
]).


% Problem 2
problem(2, [
    [_,_,2,_,3,_,1,_,_],
    [_,4,_,_,_,_,_,3,_],
    [1,_,5,_,_,_,_,8,2],
    [_,_,_,2,_,_,6,5,_],
    [9,_,_,_,8,7,_,_,3],
    [_,_,_,_,4,_,_,_,_],
    [8,_,_,_,7,_,_,_,4],
    [_,9,3,1,_,_,_,6,_],
    [_,_,7,_,6,_,5,_,_]
]).


% Problem 3
problem(3, [
    [1,_,_,_,_,_,_,_,_],
    [_,_,2,7,4,_,_,_,_],
    [_,_,_,5,_,_,_,_,4],
    [_,3,_,_,_,_,_,_,_],
    [7,5,_,_,_,_,_,_,_],
    [_,_,_,_,_,9,6,_,_],
    [_,4,_,_,_,6,_,_,_],
    [_,_,_,_,_,_,_,7,1],
    [_,_,_,_,_,1,_,3,_]
]).
```
