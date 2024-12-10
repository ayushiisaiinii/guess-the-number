# guess-the-number
check your gut feeling and guess a number
#include <math.h>
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

void guess(int N)
{
    int number, user_guess, numberofguess = 0;
    srand(time(NULL));
    number = rand() % N;
    printf("Guess a number between 1 and %d\n", N);
    do {
        if (numberofguess > 9) {
            printf("\nYou Lose!\n");
            break;
        }

        printf("Enter your guess: ");
        scanf("%d", &user_guess);


        if (abs(user_guess - number) <= 5) {
            printf("You're very close!\n");
        } else if (abs(user_guess - number) <= 10) {
            printf("You're close!\n");
        }

    
        if (numberofguess == 0) { 
            if (abs(user_guess - number) <= 5) {
                printf("Your gut feeling is strong! Great start!\n");
            } else if (abs(user_guess - number) <= 10) {
                printf("Not bad! You're getting warm.\n");
            } else {
                printf("Your gut feeling needs some tuning. Keep trying!\n");
            }
        }
        if (user_guess > number) {
            printf("Lower number please!\n");
            numberofguess++;
        }
        else if (user_guess < number) {
            printf("Higher number please!\n");
            numberofguess++;
        }
        else {
            printf("You guessed the number in %d attempts!\n", numberofguess);
        }

    } while (user_guess != number);
}

int main()
{
    int N = 100;
    guess(N); // Call the guess function
    return 0;
}
