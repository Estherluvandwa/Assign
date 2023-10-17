# Assign
#include <stdio.h>

// Define a structure to store student information
struct Student {
    char name[50];
    int registration;
    int grades[5]; // Assuming 5 units
};

int main() {
    // Create an array to store student data for 5 students
    struct Student students[5];

    // Input data for each student
    for (int i = 0; i < 5; i++) {
        printf("Enter student name: ");
        scanf("%s", students[i].name);
        printf("Enter registration number: ");
        scanf("%d", &students[i].registration);
        
        // Input grades for 5 units
        for (int j = 0; j < 5; j++) {
            printf("Enter grade for Unit %d: ", j + 1);
            scanf("%d", &students[i].grades[j]);
        }
    }

    // Calculate average, highest, and lowest grades
    for (int i = 0; i < 5; i++) {
        int sum = 0;
        int highest = students[i].grades[0];
        int lowest = students[i].grades[0];
        
        for (int j = 0; j < 5; j++) {
            sum += students[i].grades[j];
            
            if (students[i].grades[j] > highest) {
                highest = students[i].grades[j];
            }
            
            if (students[i].grades[j] < lowest) {
                lowest = students[i].grades[j];
            }
        }
        
        float average = (float)sum / 5;

        // Display results for each student
        printf("Name: %s\n", students[i].name);
        printf("Registration Number: %d\n", students[i].registration);
        printf("Average Grade: %.2f\n", average);
        printf("Highest Grade: %d\n", highest);
        printf("Lowest Grade: %d\n", lowest);
        printf("\n");
    }

    // Search for a student by registration number
    int search_reg_no;
    printf("Enter registration number to search for a student: ");
    scanf("%d", &search_reg_no);

    int found = 0;
    for (int i = 0; i < 5; i++) {
        if (students[i].registration == search_reg_no) {
            found = 1;
            printf("Name: %s\n", students[i].name);
            printf("Average Grade: %.2f\n", (float)(students[i].grades[0] + students[i].grades[1] + students[i].grades[2] + students[i].grades[3] + students[i].grades[4]) / 5);
            break;
        }
    }

    if (!found) {
        printf("Student not found.\n");
    }

    return 0;
}
