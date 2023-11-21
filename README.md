/**
 * Tic Tac Toe Game
 * @author: Hanin Aljalab: 3009857, Tasnem Alkhateeb: 3009708, Niloufar Moghaddas: 3011331
 */


import java.util.*;

public class Main {
    public static void main(String[] args) {

        // Decleration of the variables
        char[][] board = { { ' ', ' ', ' ' },
                           { ' ', ' ', ' ' },
                           { ' ', ' ', ' ' }
        };
        int player;
        boolean win;

        // Initialize the variables
        player = 1;
        win = false;

        // creating the "Scanner"
        Scanner sc = new Scanner(System.in);

        // Start the game
        while (!win && !isBoardFull(board)) {
            spielfeldAusgeben(board);

            if (player == 1) {
                // Player's turn
                spielerZug(board, sc);
            } else {
                // Computer's turn
                computerZug(board);
            }

            // Check for a win or draw
            win = isWin(board);
            if (!win) {
                player = (player == 1) ? 2 : 1; // change the player
            }
        }

        spielfeldAusgeben(board);

        if (win) {
            System.out.println("Spieler " + player + " gewinnt!");
        } else {
            System.out.println("Unentschieden!");
        }
    }

    // print the game board
    public static void spielfeldAusgeben(char[][] board) {
        for (int i = 0; i < board.length; i++) {
            for (int j = 0; j < board[i].length; j++) {
                System.out.print(" [" + board[i][j] + "] ");
            }
            System.out.println();
        }
    }

    //
    public static void spielerZug(char[][] board, Scanner sc) {
        System.out.println("Spieler, geben Sie Ihre Position ein (1-9): ");
        int input = sc.nextInt();

        // Convert input in row and column
        int row = (input - 1) / 3;
        int col = (input - 1) % 3;

        // Check whether the position is valid and the field is not occupied
        if (input >= 1 && input <= 9 && board[row][col] == ' ') {
            board[row][col] = 'O';
        } else {
            System.out.println("Ungültige Position. Bitte erneut versuchen.");
            spielerZug(board, sc); // Recursive call for new input
        }
    }

    public static void computerZug(char[][] board) {
        Random ra = new Random();
        int row, col;

        do {
            row = ra.nextInt(board.length);
            col = ra.nextInt(board.length);
        } while (board[row][col] != ' ');

        board[row][col] = 'X';
    }

    public static boolean isWin(char[][] board) {
        // Check for profit in rows, columns and diagonals
        for (int i = 0; i < 3; i++) {
            // Profit in rows
            if (board[i][0] == board[i][1] && board[i][1] == board[i][2] && board[i][0] != ' ') {
                return true;
            }
            // Profit in columns
            if (board[0][i] == board[1][i] && board[1][i] == board[2][i] && board[0][i] != ' ') {
                return true;
            }
        }
        // Profit in diagonals
        if ((board[0][0] == board[1][1] && board[1][1] == board[2][2] && board[0][0] != ' ') || (board[0][2] == board[1][1] && board[1][1] == board[2][0] && board[0][2] != ' ')) {
            return true;
        }
        return false;
    }

    public static boolean isBoardFull(char[][] board) {
        // Check whether the pitch is full (draw)
        for (int i = 0; i < board.length; i++) {
            for (int j = 0; j < board[i].length; j++) {
                if (board[i][j] == ' ') {
                    return false; // There are still empty positions
                }
            }
        }
        return true; // All positions have been filled
    }
}
