# Quiz-Game-and-score-analyzer
this project is Quiz game and game score analyzer

#include <stdio.h>

#define MAX 100

// Display scores
void display(int arr[], int n) {
    printf("\nScores:\n");
    for(int i = 0; i < n; i++)
        printf("%d ", arr[i]);
    printf("\n");
}

// Max score
int findMax(int arr[], int n) {
    int max = arr[0];
    for(int i = 1; i < n; i++)
        if(arr[i] > max)
            max = arr[i];
    return max;
}

// Min score
int findMin(int arr[], int n) {
    int min = arr[0];
    for(int i = 1; i < n; i++)
        if(arr[i] < min)
            min = arr[i];
    return min;
}

// Average
float findAvg(int arr[], int n) {
    int sum = 0;
    for(int i = 0; i < n; i++)
        sum += arr[i];
    return (float)sum / n;
}

// Sort (Bubble Sort)
void sort(int arr[], int n) {
    for(int i = 0; i < n - 1; i++) {
        for(int j = 0; j < n - i - 1; j++) {
            if(arr[j] > arr[j + 1]) {
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}

// Search
int search(int arr[], int n, int key) {
    for(int i = 0; i < n; i++)
        if(arr[i] == key)
            return i;
    return -1;
}

// Pass/Fail
void passFail(int arr[], int n) {
    int pass = 0, fail = 0;
    for(int i = 0; i < n; i++) {
        if(arr[i] >= 4)  // out of 10 quiz
            pass++;
        else
            fail++;
    }
    printf("\nPass: %d\nFail: %d\n", pass, fail);
}

// Quiz Function
int conductQuiz() {
    int score = 0, ans;

    printf("\n--- Quiz Started ---\n");

    printf("\n1. Largest planet?\n1) Earth\n2) Jupiter\n3) Mars\n4) Venus\n");
    scanf("%d", &ans);
    if(ans == 2) score++;

    printf("\n2. Capital of India?\n1) Mumbai\n2) Kolkata\n3) New Delhi\n4) Chennai\n");
    scanf("%d", &ans);
    if(ans == 3) score++;

    printf("\n3. Who wrote Macbeth?\n1) Dickens\n2) Shakespeare\n3) Twain\n4) Austen\n");
    scanf("%d", &ans);
    if(ans == 2) score++;

    printf("\n4. Symbol O?\n1) Gold\n2) Oxygen\n3) Ozone\n4) Osmium\n");
    scanf("%d", &ans);
    if(ans == 2) score++;

    printf("\n5. Smallest prime?\n1) 0\n2) 1\n3) 2\n4) 3\n");
    scanf("%d", &ans);
    if(ans == 3) score++;

    printf("\nQuiz Score: %d/5\n", score);

    return score;
}

int main() {
    int scores[MAX];
    int n = 0, choice, key;

    do {
        printf("\n--- Quiz Analyzer Menu ---\n");
        printf("1. Take Quiz\n");
        printf("2. Display Scores\n");
        printf("3. Highest Score\n");
        printf("4. Lowest Score\n");
        printf("5. Average Score\n");
        printf("6. Sort Scores\n");
        printf("7. Search Score\n");
        printf("8. Pass/Fail Count\n");
        printf("9. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);

        switch(choice) {
            case 1:
                scores[n] = conductQuiz();
                n++;
                break;

            case 2:
                display(scores, n);
                break;

            case 3:
                printf("Highest Score: %d\n", findMax(scores, n));
                break;

            case 4:
                printf("Lowest Score: %d\n", findMin(scores, n));
                break;

            case 5:
                printf("Average Score: %.2f\n", findAvg(scores, n));
                break;

            case 6:
                sort(scores, n);
                printf("Scores sorted.\n");
                break;

            case 7:
                printf("Enter score to search: ");
                scanf("%d", &key);
                int pos = search(scores, n, key);
                if(pos != -1)
                    printf("Found at position %d\n", pos + 1);
                else
                    printf("Not found\n");
                break;

            case 8:
                passFail(scores, n);
                break;

            case 9:
                printf("Exiting...\n");
                break;

            default:
                printf("Invalid choice!\n");
        }

    } while(choice != 9);

    return 0;
}
