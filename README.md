# Sudoku-Solver-CSP-modelling-in-Z3
Constraint satisfaction Problem (CSP)

By implementing following constraints, sudoku problem can be solved.

1. Typical Sudoku constraints:
   - (a) Numbers cannot be repeated in any row, column, or 3x3 square.
   - (b) Cells, whose values are already specified, must be assigned to the respective values.
 
2. Top middle 3x3 square: For every corner cell of this square, one of the horizontally or
   vertically adjacent cells must equal the value plus 1. 
   - For example, for the cell [3, 0],
   if [3, 0] = 4, then either [3, 1] = 5 or [4, 0] = 5.
  
3. Top right 3x3 square: The sum of the indicated cells must be equal to twice the value
   of the center cell. 
   - In other words: [7, 0] + [6, 1] + [7, 2] + [8, 1] = 2 × [7, 1]
  
4. Middle left square: The numbers must comply with the arithmetic expressions drawn
   in the figure:
   - (a) [1, 3] + [2, 3] = 13
   - (b) [0, 5] / [0, 4] = 2
   - (c) [2, 5] − [2, 4] = 4
  
5. Center square: Numbers must comply with the inequalities. More specifically:
   - (a) [3, 3] > [3, 4] > [3, 5]
   - (b) [4, 3] > [4, 4] > [4, 5]
   - (c) [5, 3] > [5, 4] > [5, 5]
  
6. Middle right square: Exactly one of the yellow cells must contain a value smaller
  than 5, the other yellow cells must contain a value greater or equal to 5.

7. Bottom left square: The sum of all rows in this square must be equal
   - [0, 6] + [1, 6] + [2, 6] = [0, 7] + [1, 7] + [2, 7] = [0, 8] + [1, 8] + [2, 8].

8. Bottom middle square:
   - (a) Multiplying the sums of the two indicated columns gives an odd number:
     - ([3, 6] + [3, 7] + [3, 8]) × ([5, 6] + [5, 7] + [5, 8]) must be odd.
   - (b) The numbers must comply with the arithmetic expressions drawn in the figure:
     - [4, 7] + [4, 8] = 3.

9. Bottom right square: The values of the green cells must be either all odd or all even.
  Moreover, if the green cells contain odd numbers, then the orange cell must contain
  an even number. If the green cells contain even numbers, then the orange cell must
  contain an odd number.
