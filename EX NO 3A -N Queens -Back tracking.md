
# EX 3A N Queens Problem - Backtracking Approach.

## AIM:
To Write a Java program for N queens using backtracking approach.
You are given an integer N. For a given N x N chessboard, find a way to place 'N' queens such that no queen can attack any other queen on the chessboard.
A queen can be attacked when it lies in the same row, column, or the same diagonal as any of the other queens. You have to print one such configuration.
Chess Board
<img width="241" height="209" alt="image" src="https://github.com/user-attachments/assets/96aacb61-4f34-423f-b324-5e34454e42b8" />


Note :

Get the input from the user for N . The value of N must be from 1 to 4

If solution exists Print a binary matrix as output that has 1s for the cells where queens are placed

If there is no solution to the problem  print  "Solution does not exist"

## Algorithm

1. Read the value of N and initialize an N × N chessboard with all elements set to 0.

2. Start placing queens column by column, beginning from the first column (col = 0).

3. For each column, check every row:
   - Place a queen if the position is safe (no other queen in the same row, upper-left diagonal, or lower-left diagonal).

4. If placing a queen is safe:
   - Mark the position as 1 (queen placed).
   - Recursively attempt to place the next queen in the next column.
   - If it fails, backtrack by removing the queen (set position back to 0).

5. If all queens are successfully placed (col ≥ N), print the board as the solution; otherwise, report that no solution exists.

## Program:
```java
/*
Program to solve the N-Queens problem using backtracking
Developed by: JAYASREE R
Register Number: 212223040074
*/

import java.util.Scanner;

public class NQueensInput {

    static int N;

    static void printSolution(int[][] board) {
        for (int i = 0; i < N; i++) {
            for (int j = 0; j < N; j++) {
                System.out.print(board[i][j] + " ");
            }
            System.out.println();
        }
    }

    static boolean isSafe(int[][] board, int row, int col) {
        for (int i = 0; i < col; i++)
            if (board[row][i] == 1)
                return false;
        for (int i = row, j = col; i >= 0 && j >= 0; i--, j--)
            if (board[i][j] == 1)
                return false;
        for (int i = row, j = col; i < N && j >= 0; i++, j--)
            if (board[i][j] == 1)
                return false;
        return true;
    }

    static boolean solveNQUtil(int[][] board, int col) {
        if (col >= N)
            return true;

        for (int i = 0; i < N; i++) {
            if (isSafe(board, i, col)) {

                board[i][col] = 1;

                if (solveNQUtil(board, col + 1))
                    return true;

                board[i][col] = 0; 
            }
        }
        return false;
    }

    static boolean solveNQ() {
        if (N < 1 || N > 8) {
            System.out.println("Solution does not exist");
            return false;
        }
        int[][] board = new int[N][N];
        if (!solveNQUtil(board, 0)) {
            System.out.println("Solution does not exist");
            return false;
        }
        printSolution(board);
        return true;
    }
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        N = scanner.nextInt();
        solveNQ();
        scanner.close();
    }
}
```

## Output:
<img width="498" height="364" alt="image" src="https://github.com/user-attachments/assets/afc38bbf-cf72-4715-b67d-e3c7c373e9bf" />


## Result:
The program successfully implemented and the ouput is verified. 
