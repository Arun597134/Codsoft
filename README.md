# Codsoft

import java.util.Scanner;
import java.util.Random;

public class NumberGuessingGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();

        boolean playAgain = true;
        int totalScore = 0;
        int round = 1;

        System.out.println("Welcome to the Number Guessing Game!");
        System.out.println("You will earn points based on how quickly you guess the number.");

        while (playAgain) {
            System.out.println("\n--- Round " + round + " ---");
            int randomNumber = random.nextInt(100) + 1; // Random number between 1 and 100
            int attempts = 0;
            int maxScore = 100; // Maximum score for the round
            boolean hasWon = false;

            while (!hasWon) {
                System.out.print("Enter your guess: ");
                int guess = scanner.nextInt();
                attempts++;

                if (guess > randomNumber) {
                    System.out.println("Too high! Try again.");
                } else if (guess < randomNumber) {
                    System.out.println("Too low! Try again.");
                } else {
                    hasWon = true;
                    int roundScore = Math.max(maxScore - (attempts - 1) * 10, 0); // Deduct 10 points per extra attempt
                    totalScore += roundScore;

                    System.out.println("Congratulations! You guessed the number in " + attempts + " attempts.");
                    System.out.println("You earned " + roundScore + " points this round.");
                    System.out.println("Your total score is now: " + totalScore);
                }
            }

            // Ask the player if they want to play another round
            System.out.print("Do you want to play another round? (yes/no): ");
            String response = scanner.next();
            playAgain = response.equalsIgnoreCase("yes");
            if (playAgain) round++;
        }

        System.out.println("\nGame over! Your final score is: " + totalScore);
        scanner.close();
    }
}