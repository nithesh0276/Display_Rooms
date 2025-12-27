MINI PROJECT HANDBOOK ASSIGNMENT
Course Code & Title: 25ITT11 - C Programming
Module: Display Rooms Module


void displayRooms() {
    struct Room r;
    FILE *fp = fopen("rooms.txt", "r");

    if (fp == NULL) {
        printf("\nNo rooms found! Please add a room first.\n");
        return;
    }

    printf("\n-------------------------------------------------------\n");
    printf(" Room No  |  Type        |  Price (Rs)  |  Status      \n");
    printf("-------------------------------------------------------\n");

    while (fscanf(fp, "%d %s %f %d", &r.roomNo, r.type, &r.price, &r.isBooked) != EOF) {

        char status[15];
        if (r.isBooked == 0) {
            sprintf(status, "Available");
        } else {
            sprintf(status, "Booked");
        }

        printf(" %-8d | %-12s | %-12.2f | %s\n",
               r.roomNo, r.type, r.price, status);
    }

    printf("-------------------------------------------------------\n");

    fclose(fp);
}

