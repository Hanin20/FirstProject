/**
 * Tic Tac Toe Game
 * @author Hanin Aljalab: 3009857
 */

import java.util.*;
public class Main {
    public static void main(String[] args) {

        //Decleration of the variables
        char f1, f2, f3, f4, f5, f6, f7, f8, f9;
        int player;
        boolean win;

        //Initialize the variables
        f1 = f2 = f3 = f4 = f5 = f6 = f7 = f8 = f9 = '#';
        player = 1;
        win = false;

        //creating the "Scanner"
        Scanner sc = new Scanner(System.in);

        //start the game
        while (win == false) {
            //Output the playing field
            spielfeldAusgeben(f1,f2,f3,f4,f5,f6,f7,f8,f9);

            //When it's player 1's turn
            if (player == 1){
                System.out.println("Spieler 1 ist an der Reihe.");
                System.out.println("Wo möchten Sie setzen?");
                int input = sc.nextInt();
                System.out.println("Sie haben die Position "+input+ " gewählt.");

                //Check with field has been selected
                //change the selected field
                switch (input){
                    case 1:
                        f1 = 'X';
                        break;

                    case 2:
                        f2 = 'X';
                        break;

                    case 3:
                        f3 = 'X';
                        break;

                    case 4:
                        f4 = 'X';
                        break;

                    case 5:
                        f5 = 'X';
                        break;

                    case 6:
                        f6 = 'X';
                        break;

                    case 7:
                        f7 = 'X';
                        break;

                    case 8:
                        f8 = 'X';
                        break;

                    case 9:
                        f9 = 'X';
                        break;
                }
            } else if (player == 2) {       //When it's player 2's turn
                System.out.println("Spieler 2 ist an der Reihe.");
                System.out.println("Wo möchten Sie setzen?");
                int input = sc.nextInt();
                System.out.println("Sie haben die Position "+input+ " gewählt.");

                //Check with field has been selected
                //change the selected field
                switch (input){
                    case 1:
                        f1 = 'O';
                        break;

                    case 2:
                        f2 = 'O';
                        break;

                    case 3:
                        f3 = 'O';
                        break;

                    case 4:
                        f4 = 'O';
                        break;

                    case 5:
                        f5 = 'O';
                        break;

                    case 6:
                        f6 = 'O';
                        break;

                    case 7:
                        f7 = 'O';
                        break;

                    case 8:
                        f8 = 'O';
                        break;

                    case 9:
                        f9 = 'O';
                        break;
                }
            }else {
                System.out.println("Spielerzählung hat nicht funktioniert");
                win = true;
            }

            //the review was won
            if (f1 == f2 && f1 == f3 && f1 != '#'){
                win = true;
            } else if (f4 == f5 && f4 == f6 && f4 != '#') {
                win = true;
            } else if (f7 == f8 && f7 == f9 && f7 != '#') {
                win = true;
            } else if (f1 == f4 && f1 == f7 && f1 != '#') {
                win = true;
            } else if (f2 == f5 && f2 == f8 && f2 != '#') {
                win = true;
            } else if (f3 == f6 && f3 == f9 && f3 != '#') {
                win = true;
            } else if (f1 == f5 && f1 == f9 && f1 != '#') {
                win = true;
            } else if (f3 == f5 && f3 == f7 && f3 != '#') {
                win = true;
            }else {
            }

            //Who wins?
            if (win == true){
                spielfeldAusgeben(f1,f2,f3,f4,f5,f6,f7,f8,f9);
                System.out.println("Spieler "+player+" hat gewonnen");
            }

            //change the player
            if (player == 1){
                player++;
            }else {
                player--;
            }
        }

    }

   //Implementation of the method
    public static void spielfeldAusgeben(char f1, char f2, char f3, char f4, char f5, char f6, char f7, char f8, char f9) {

        System.out.println(f7 + " | " + f8 + " | " + f9);
        System.out.println("---------");
        System.out.println(f4 + " | " + f5 + " | " + f6);
        System.out.println("---------");
        System.out.println(f1 + " | " + f2 + " | " + f3);
    }
}
