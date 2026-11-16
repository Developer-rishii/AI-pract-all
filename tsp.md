```prolog
/*
  Traveling Salesman Problem in Prolog (SWI-Prolog).
  Usage:
  ?- shortest_path(Path).
  ?- best_path(Path, Cost).
*/


/* This is the data set. */

edge(a, b, 3).
edge(a, c, 4).
edge(a, d, 2).
edge(a, e, 7).

edge(b, c, 4).
edge(b, d, 6).
edge(b, e, 3).

edge(c, d, 5).
edge(c, e, 8).

edge(d, e, 6).

edge(b, a, 3).
edge(c, a, 4).
edge(d, a, 2).
edge(e, a, 7).

edge(c, b, 4).
edge(d, b, 6).
edge(e, b, 3).

edge(d, c, 5).
edge(e, c, 8).
edge(e, d, 6).

edge(a, h, 2).
edge(h, d, 1).


/* Calculate the length of a list. */

len([], 0).

len([H|T], N) :-
    len(T, X),
    N is X + 1.


/* Find the best path. */

best_path(Visited, Total) :-
    path(a, a, Visited, Total).


/* Initialize the path. */

path(Start, Fin, Visited, Total) :-
    path(Start, Fin, [Start], Visited, 0, Total).


/* Recursive path calculation. */

path(Start, Fin, CurrentLoc, Visited, Costn, Total) :-
    edge(Start, StopLoc, Distance),
    NewCostn is Costn + Distance,
    \+ member(StopLoc, CurrentLoc),
    path(StopLoc, Fin, [StopLoc|CurrentLoc],
         Visited, NewCostn, Total).


/* Calculate the final path and total cost. */

path(Start, Fin, CurrentLoc, Visited, Costn, Total) :-
    edge(Start, Fin, Distance),
    reverse([Fin|CurrentLoc], Visited),
    len(Visited, Q),
    (Q \= 7 -> Total is 100000;
               Total is Costn + Distance).


/* Find the shortest path. */

shortest_path(Path) :-
    setof(Cost-Path, best_path(Path, Cost), Holder),
    pick(Holder, Path).


/* Compare two paths. */

best(Cost-Holder, Bcost-_, Cost-Holder) :-
    Cost < Bcost, !.

best(_, X, X).


/* Pick the minimum-cost path. */

pick([Cost-Holder|R], X) :-
    pick(R, Bcost-Bholder),
    best(Cost-Holder, Bcost-Bholder, X), !.

pick([X], X).
```
