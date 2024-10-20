#include <stdio.h>

// Define a structure named Time
struct Time {
    int hours;
    int minutes;
    int seconds;
};

// Function to add two time values
struct Time addTime(struct Time t1, struct Time t2) {
    struct Time result;
    
    // Add seconds
    result.seconds = t1.seconds + t2.seconds;
    if (result.seconds >= 60) {
        result.seconds -= 60;
        result.minutes = 1;  // Carry over to minutes
    } else {
        result.minutes = 0;
    }

    // Add minutes
    result.minutes += t1.minutes + t2.minutes;
    if (result.minutes >= 60) {
        result.minutes -= 60;
        result.hours = 1;  // Carry over to hours
    } else {
        result.hours = 0;
    }

    // Add hours
    result.hours += t1.hours + t2.hours;
    
    return result;
}

// Function to display time in proper format
void displayTime(struct Time t) {
    printf("Time: %02d:%02d:%02d\n", t.hours, t.minutes, t.seconds);
}

int main() {
    struct Time t1, t2, result;

    // Input first time
    printf("Enter first time (hours minutes seconds): ");
    scanf("%d %d %d", &t1.hours, &t1.minutes, &t1.seconds);

    // Input second time
    printf("Enter second time (hours minutes seconds): ");
    scanf("%d %d %d", &t2.hours, &t2.minutes, &t2.seconds);

    // Add the two times
    result = addTime(t1, t2);

    // Display the result
    printf("The sum of the two times is: ");
    displayTime(result);

    return 0;
}

