# Experiment 2: Write a program to solve 8 queen problem.

## Theory:
This problem is to find an arrangement of N queens on a chess board, such that no queen can attack any other queens on the board. This can be formulated as a problem as follows:
• States: Any arrangement of 0 to 8 queens on the board is a state.
• Initial state: No queens on the board.
• Actions: Add a queen to any empty square.
• Transition model: Returns the board with a queen added to the specified square.
• Goal test: 8 queens are on the board, none attacked.
In this formulation, we have 64 ・ 63 ・ ・ ・ 57 ≈ 1.8×10^14 possible sequences to investigate. A better formulation would prohibit placing a queen in any square that is already attacked:
• States: All possible arrangements of n queens (0 ≤ n ≤ 8), one per column in the leftmost n columns, with no queen attacking another.
• Actions: Add a queen to any square in the leftmost empty column such that it is not attacked by any other queen.
This formulation reduces the 8-queens state space from 1.8×10^14 to just 2,057, and solutions are easy to find.

