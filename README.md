# Number-game
import java.util.Scanner;
import java.util.Random;

public class GuessTheNumber {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        
        int minRange = 1;
        int maxRange = 100;
        int attemptsLimit = 5;
        int score = 0;
        
        boolean playAgain = true;
        
        while (playAgain) {
            int randomNumber = random.nextInt(maxRange - minRange + 1) + minRange;
            System.out.println("Welcome to Guess the Number!");
            System.out.println("I've selected a number between " + minRange + " and " + maxRange + ". Guess what it is.");
            
            int attempts = 0;
            boolean guessedCorrectly = false;
            
            while (attempts < attemptsLimit) {
                System.out.print("Enter your guess: ");
                int guess = scanner.nextInt();
                
                attempts++;
                
                if (guess == randomNumber) {
                    System.out.println("Congratulations! You've guessed the number correctly in " + attempts + " attempts.");
                    score++;
                    guessedCorrectly = true;
                    break;
                } else if (guess < randomNumber) {
                    System.out.println("Too low! Try again.");
                } else {
                    System.out.println("Too high! Try again.");
                }
            }
            
            if (!guessedCorrectly) {
                System.out.println("Sorry, you've used all your attempts. The number was: " + randomNumber);
            }
            
            System.out.println("Your current score is: " + score);
            System.out.print("Do you want to play again? (yes/no): ");
            String playAgainResponse = scanner.next();
            playAgain = playAgainResponse.equalsIgnoreCase("yes");
        }
        
        System.out.println("Thank you for playing Guess the Number!");
        scanner.close();
    }
}
