import java.util.*;

class RockPaperScissors {
    static int user = 0;
    static int computer = 0;

    public static void main(String args[]) {
        Scanner sc = new Scanner(System.in);
        String choice[] = {"Rock", "Paper", "Scissors"};

        boolean playAgain;
        do {
            user = 0;
            computer = 0;
            int rounds = 3;

            for (int i = 0; i < rounds; i++) {
                int compChoice = getComp();
                int userChoice = getUserChoice(sc);
                
                System.out.println("Computer chose: " + choice[compChoice]);
                getDecision(compChoice, userChoice);
                System.out.println("Score -> User: " + user + " | Computer: " + computer);
                System.out.println("----------------------");
            }
            getResult();

            
            System.out.print("Do you want to play again? (yes/no): ");
            playAgain = sc.nextLine().equalsIgnoreCase("yes");

        } while (playAgain);

        System.out.println("Thanks for playing!");
        sc.close();
    }

    public static int getComp() {
        return new Random().nextInt(3);
    }

    public static int getUserChoice(Scanner sc) {
        while (true) {
            System.out.print("Enter Rock, Paper, or Scissors: ");
            String userString = sc.nextLine().toLowerCase();
            switch (userString) {
                case "rock": return 0;
                case "paper": return 1;
                case "scissors": return 2;
                default:
                    System.out.println("Invalid choice. Try again.");
            }
        }
    }

    public static void getDecision(int choice1, int choice2) {
        if (choice1 == choice2) {
            System.out.println("It's a tie!");
        } else if ((choice1 == 0 && choice2 == 2) || 
                   (choice1 == 1 && choice2 == 0) || 
                   (choice1 == 2 && choice2 == 1)) {
            System.out.println("Computer Wins this round!");
            computer++;
        } else {
            System.out.println("User Wins this round!");
            user++;
        }
    }

    public static void getResult() {
        System.out.println("\nFinal Score:");
        System.out.println("User: " + user + " | Computer: " + computer);
        if (user > computer)
            System.out.println("User Wins the Game!");
        else if (computer > user)
            System.out.println("Computer Wins the Game!");
        else
            System.out.println("It's a Tie!");
    }
}
