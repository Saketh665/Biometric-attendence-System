# Biometric-attendence-System
#include <stdio.h>
#include <string.h>

// Maximum number of users
#define MAX_USERS 10

// Structure to store user information
typedef struct {
    int id;
    char name[50];
    char fingerprint[20];  // Simplified fingerprint representation
} User;

// Sample database of users
User users[MAX_USERS] = {
    {1, "Saketh", "fp_Saketh"},
    {2, "Nani", "fp_Nani"},
    {3, "Geethi", "fp_Geethi"}
};

// Function to simulate fingerprint matching
int matchFingerprint(char fingerprint[]) {
    for (int i = 0; i < MAX_USERS; i++) {
        if (strcmp(users[i].fingerprint, fingerprint) == 0) {
            return users[i].id;
        }
    }
    return -1;  // Return -1 if no match found
}

// Function to mark attendance
void markAttendance(int userId) {
    printf("Attendance marked for User ID: %d\n", userId);
}

// Main function
int main() {
    char inputFingerprint[20];
    
    printf("Enter fingerprint: ");
    scanf("%s", inputFingerprint);
    
    int userId = matchFingerprint(inputFingerprint);
    
    if (userId != -1) {
        markAttendance(userId);
    } else {
        printf("Fingerprint not recognized.\n");
    }
    
    return 0;
}
